import os
from datetime import datetime

group_name = input("Enter address group name (default: gpblock-1): ").strip()
if not group_name:
    group_name = "gpblock-1"

print("\nPaste IP addresses (can be multiple lines or space-separated).")
print("Press ENTER twice to finish:\n")

# Read pasted input
lines = []
while True:
    line = input()
    if line.strip() == "":
        break
    lines.append(line)

# Split by space and newline
raw_text = " ".join(lines)
ips = [ip.strip() for ip in raw_text.replace(",", " ").split() if ip.strip()]

if not ips:
    print("No valid IPs entered. Exiting.")
    exit()

downloads = os.path.expanduser("~/Downloads")
timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
output_file = os.path.join(downloads, f"fortigate_block_{timestamp}.txt")

with open(output_file, "w") as f:
    f.write("config firewall address\n")
    for ip in ips:
        f.write(f"    edit {ip}\n")
        f.write(f"        set subnet {ip}/32\n")
        f.write("    next\n")
    f.write("end\n\n")

    f.write("config firewall addrgrp\n")
    f.write(f"    edit {group_name}\n")
    f.write("        set member " + " ".join(ips) + "\n")
    f.write("    next\n")
    f.write("end\n")

print("\n✅ FortiGate CLI saved successfully:")
print(output_file)
