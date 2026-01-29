# FortiGate Bulk IP Block Script Creator Tool

This Python script helps you quickly generate FortiGate CLI commands to:

- Create multiple **firewall address objects** from IP addresses  
- Add all those objects into a **single address group**  
- Save the output as a `.txt` file locally, ready to paste into FortiGate CLI  

It is useful for **SOC operations, incident response, and bulk IP blocking**.

---

## 🧰 Requirements

- Python **3.8+** (tested on Python 3.13)  
- Windows / Linux / macOS  

---

## ⚡ Instructions to Use the Tool

1. **Open Command Prompt (Windows) or Terminal (Linux/macOS)**

2. **Run Python**  
   - Type `python` and press Enter  
   - Or open the saved `.py` script and run it

3. **Enter the address group name** when prompted  
   - You can use an existing group or create a new one

   <img width="416" height="182" alt="image" src="https://github.com/user-attachments/assets/9466b88b-ebd7-4aa6-9264-e723b6fdf130" />


4. **Prepare the IP list for input** in Python CLI:  

“Since we can’t paste the IPs as a list in the CLI, we are converting them into a single line separated by spaces

   - Open **Microsoft Word**  
   - Paste your IP addresses (one per line)  
   <img width="415" height="217" alt="image" src="https://github.com/user-attachments/assets/443fb6c8-83fa-4ae2-b098-c1b9c416d23c" />

   - Press **Ctrl + F** (Find and Replace)  
     - **Find : ^p  
     - **Replace with: (one space) 
     - Click **Replace All**  

     <img width="415" height="215" alt="image" src="https://github.com/user-attachments/assets/0a738c82-49d5-4948-ae6a-44b29143d8c1" />

   - Now all IPs are in **one line separated by spaces**
   <img width="415" height="157" alt="image" src="https://github.com/user-attachments/assets/c36c72f7-48e5-4536-b1a7-57dd96cde95a" />


5. **Copy the space-separated IP list**  
   - Paste it into the Python CLI when prompted  
   - Press **Enter** **twice**

6. **Check the output file**  
   - The script saves the FortiGate CLI commands in your **Downloads folder**:  
     ```
     C:\Users\<username>\Downloads\fortigate_block_YYYYMMDD_HHMMSS.txt
     ```

7. **Apply the commands in FortiGate CLI**  
   - Open the generated file, copy the content  
   - Paste it into the **FortiGate CLI**  
   - All IP objects will be created and added to the specified address group
