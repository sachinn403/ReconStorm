# ReconStorm
ReconStorm is an advanced reconnaissance tool for penetration testers and bug hunters, automating subdomain enumeration, port scanning, and web enumeration.
# ReconStorm Development Roadmap

## 🚀 Overview
ReconStorm is a CLI-based reconnaissance tool for gathering domain information. It automates tasks such as subdomain enumeration, port scanning, web technology detection, directory enumeration, and more.

---

## 🔹 Step 1: Setting Up the Project Structure
### **Logic:**
1. Accept a **domain name** from the user via command-line arguments (`-d example.com`).
2. Create a **main directory** named after the target domain to store results.
3. Inside the main directory, create **subdirectories** for each scan type:
   - `subdomains/` → Stores subdomain enumeration results
   - `ports/` → Stores port scanning results
   - `web_tech/` → Stores detected web technologies
   - `screenshots/` → Stores website screenshots
   - `directories/` → Stores directory enumeration results
   - `dns_info/` → Stores DNS and WHOIS lookup results
   - `http_probing/` → Stores HTTP probing results
4. Display a success message once the folder structure is created.

### **Expected Output:**
```bash
[+] Folder structure created for: example.com
```

---

## 🔹 Step 2: Subdomain Enumeration
### **Logic:**
1. Use **Subfinder** (`subfinder -d example.com`) to find subdomains.
2. Store the found subdomains in `subdomains/subdomains.txt`.
3. Display the discovered subdomains on the terminal.

### **Enhancements:**
✅ Optionally, integrate **Amass** (`amass enum -d example.com`) for deeper enumeration.

### **Expected Output:**
```bash
[+] Running subfinder for example.com...
[+] Found subdomains saved in subdomains/subdomains.txt
```

---

## 🔹 Step 3: Port Scanning
### **Logic:**
1. Use **Nmap** (`nmap -p- example.com`) to scan for open ports.
2. Store the scan results inside `ports/nmap_scan.txt`.
3. Display the detected open ports in the terminal.

### **Enhancements:**
✅ Use **Masscan** (`masscan -p1-65535 example.com`) for faster scanning.

### **Expected Output:**
```bash
[+] Running Nmap for example.com...
[+] Open ports saved in ports/nmap_scan.txt
```

---

## 🔹 Step 4: Web Technology Detection
### **Logic:**
1. Use **WhatWeb** (`whatweb example.com`) or **Wappalyzer** to detect web technologies.
2. Store detected technologies in `web_tech/tech_stack.json`.
3. Display the results in JSON format on the terminal.

### **Expected Output:**
```bash
[+] Running WhatWeb for example.com...
[+] Technologies detected: Apache, PHP, WordPress
[+] Results saved in web_tech/tech_stack.json
```

---

## 🔹 Step 5: Screenshot Capture
### **Logic:**
1. Use **GoWitness** (`gowitness scan --target example.com`) to capture website screenshots.
2. Save the screenshots inside `screenshots/`.
3. Display a confirmation message on completion.

### **Expected Output:**
```bash
[+] Capturing screenshot for example.com...
[+] Screenshot saved in screenshots/
```

---

## 🔹 Step 6: Directory Enumeration
### **Logic:**
1. Use **ffuf** (`ffuf -u https://example.com/FUZZ -w wordlist.txt`) to find hidden directories.
2. Store the results in `directories/dirs.txt`.
3. Display discovered directories on the terminal.

### **Expected Output:**
```bash
[+] Running directory enumeration for example.com...
[+] Found directories:
    - /admin
    - /uploads
    - /login
[+] Results saved in directories/dirs.txt
```

---

## 🔹 Step 7: DNS & WHOIS Lookup
### **Logic:**
1. Use **WHOIS** (`whois example.com`) to get domain ownership information.
2. Store the WHOIS results in `dns_info/whois.txt`.
3. Use **DNSRecon** (`dnsrecon -d example.com`) to fetch DNS records.
4. Store DNS records in `dns_info/dns_records.txt`.

### **Expected Output:**
```bash
[+] Running WHOIS lookup for example.com...
[+] WHOIS data saved in dns_info/whois.txt
[+] Running DNS Recon for example.com...
[+] DNS records saved in dns_info/dns_records.txt
```

---

## 🔹 Step 8: HTTP Probing
### **Logic:**
1. Use **httpx** (`httpx -list subdomains.txt -o live_subdomains.txt`) to check for live subdomains.
2. Store live subdomains inside `http_probing/live_subdomains.txt`.
3. Display live subdomains on the terminal.

### **Expected Output:**
```bash
[+] Running HTTP probing for example.com...
[+] Live subdomains:
    - https://blog.example.com
    - https://shop.example.com
[+] Results saved in http_probing/live_subdomains.txt
```

---

## 🔹 Step 9: Adding Multithreading for Faster Execution
### **Logic:**
1. Use **multithreading** (`threading` or `asyncio`) to run multiple tasks in parallel.
2. Assign each scan its own thread for **faster execution**.
3. Display a progress bar (`tqdm`) to indicate progress.

### **Expected Benefit:**
✅ **10x Faster Execution** 🚀

---

## 🔹 Step 10: Adding JSON/CSV Output Support
### **Logic:**
1. Convert scan results into a structured JSON file (`report.json`).
2. Allow users to **export results as CSV** (`report.csv`).
3. Save reports inside the main domain directory.

### **Expected Output:**
```bash
[+] Generating structured report...
[+] Report saved as example.com/report.json
```

---

## 🔹 Step 11: Enhancing User Experience
### **Optional Enhancements:**
✅ **Support multiple domains** (`-d domain1.com domain2.com`).
✅ **Add a configuration file (`config.yaml`)** to customize scan options.
✅ **Implement error handling** for missing tools or incorrect inputs.

---

## 🎯 Final ReconStorm Execution Flow
1️⃣ User runs the script:  
   ```bash
   python3 reconstorm.py -d example.com
   ```  
2️⃣ Script creates the **project directory structure**.  
3️⃣ Runs **all reconnaissance modules** in parallel:
   - Subdomain Enumeration
   - Port Scanning
   - Web Tech Detection
   - Screenshot Capture
   - Directory Enumeration
   - DNS & WHOIS Lookup
   - HTTP Probing
4️⃣ Saves **structured output** inside the domain folder.
5️⃣ Displays a **summary report** in the terminal.

---



