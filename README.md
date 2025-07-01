# 🔐 Windows Firewall Configuration Task

## 🎯 Objective

To configure, test, and verify inbound firewall rules on a Windows system using GUI (Windows Defender Firewall) and PowerShell. This task demonstrates understanding of network traffic filtering, basic firewall operations, and system hardening techniques.

---

## 🛠️ Tools & Technologies Used

- ✅ Windows Defender Firewall (Advanced Security)
- ✅ Windows PowerShell
- ✅ Command Prompt (CMD)
- ✅ Localhost Testing
- ✅ Screenshots for Documentation

---

## 📁 Task Description

This project involved performing a practical firewall configuration task on a Windows system, including:

- Blocking **Telnet traffic** on **port 23**
- Verifying the firewall rule via **PowerShell**
- Allowing **SSH traffic** on **port 22** (optional)
- Cleaning up by removing the test rule
- Documenting the entire process with screenshots and commands

---

## 🧭 Step-by-Step Process

### 🔹 1. Opened Windows Defender Firewall

Accessed via:

```
Win + R → control firewall.cpl → Advanced Settings
```

Navigated to:

```
Inbound Rules → New Rule
```

---

### 🔹 2. Blocked Inbound Traffic on Port 23 (Telnet)

Created a new **Inbound Rule**:
- Rule Type: **Port**
- Protocol: **TCP**
- Port: **23**
- Action: **Block the connection**
- Applied to: **All profiles**
- Rule Name: **Block Telnet**

---

### 🔹 3. Tested the Rule using PowerShell

Ran this command in **Windows PowerShell**:
```powershell
Test-NetConnection -ComputerName localhost -Port 23
```

**Expected Result**:
```
TcpTestSucceeded : False
```

This confirmed that the firewall successfully blocked Telnet traffic on port 23.


---

### 🔹 4. (Optional) Allowed Inbound Traffic on Port 22 (SSH)

Added an **allow rule** via PowerShell:
```powershell
New-NetFirewallRule -DisplayName "Allow SSH" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow
```

This showed the ability to manage firewall rules programmatically.

---

### 🔹 5. Removed the Telnet Block Rule to Restore System

Navigated to:

```
Windows Defender Firewall → Inbound Rules
```

Located the **Block Telnet** rule → Right-click → **Delete**


---

### 🔹 6. Verified the System is Back to Normal

Re-ran the test command:
```powershell
Test-NetConnection -ComputerName localhost -Port 23
```

This verified there were no longer active block rules on port 23 (though no service is expected to be running on port 23, so failure is okay).

---

## 🧪 Commands Used (also available in `firewall-commands.txt`)

```powershell
# Test blocked port (Telnet)
Test-NetConnection -ComputerName localhost -Port 23

# Allow SSH traffic
New-NetFirewallRule -DisplayName "Allow SSH" -Direction Inbound -LocalPort 22 -Protocol TCP -Action Allow

# Reset firewall to default (optional)
netsh advfirewall reset
```

---

## ✅ Outcome

- Successfully applied and verified a firewall rule to block Telnet (port 23).
- Used PowerShell to test network connectivity.
- Demonstrated rule creation and deletion both via GUI and command line.
- Learned to filter and manage inbound traffic effectively on a Windows system.
- All steps are documented with screenshots.

---

## 👩‍💻 Author

**Latha Kola**  
Cybersecurity Enthusiast | Windows Security Explorer | Network Defender



