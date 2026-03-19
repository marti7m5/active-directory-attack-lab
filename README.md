# Active Directory Attack Lab

## 🖥️ Lab Overview
This lab demonstrates network reconnaissance, firewall evasion, and service enumeration against a Windows Server in a controlled environment.

---

## 🔍 1. Network Discovery
<p align="center">
  <img src="images/01-network-discovery.png" width="700">
</p>

- Used `nmap -sn` to identify live hosts
- Discovered multiple active systems on the subnet

---

## 🚫 2. Initial Scan (All Ports Filtered)
<p align="center">
  <img src="images/02-initial-scan-filtered.png" width="700">
</p>

- Conducted a fast scan using:
nmap -Pn -n -F <target>

- All ports appeared filtered due to firewall restrictions

## 🔥 3. Firewall Disabled
<p align="center">
  <img src="images/03-firewall-disabled.png" width="700">
</p>

- Disabled Windows Firewall using:
netsh advfirewall set allprofiles state off

## 🖥️ 4. RDP Enabled
<p align="center">
  <img src="images/04-rdp-enabled.png" width="700">
</p>

- Enabled Remote Desktop:
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f
netsh advfirewall firewall set rule group="remote desktop" new enable=Yes

## ✅ 5. Final Scan (Successful Enumeration)
<p align="center">
  <img src="images/05-final-scan.png" width="700">
</p>

- Open ports identified:
- 135 (MSRPC)
- 139 (NetBIOS)
- 445 (SMB)
- 3389 (RDP)

## 🧠 Key Takeaways
- Firewalls can completely obscure attack surface visibility
- Service exposure drastically changes after misconfiguration
- Enumeration is critical before exploitation
