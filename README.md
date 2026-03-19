# Active Directory Attack Lab

## 🖥️ Lab Overview
This lab demonstrates network reconnaissance, firewall evasion, and service enumeration against a Windows Server in a controlled environment.

---

## 🔍 1. Network Discovery
[Network Discovery](images/01-network-discovery.png)

- Used `nmap -sn` to identify live hosts
- Discovered multiple active systems on the subnet

---

## 🚫 2. Initial Scan (All Ports Filtered)
[Initial Scan](images/02-initial-scan-filtered.png)

- Conducted a fast scan using:
nmap -Pn -n -F <target>

- All ports appeared filtered due to firewall restrictions

## 🔥 3. Firewall Disabled
[Firewall Disabled](images/03-firewall-disabled.png)

- Disabled Windows Firewall using:
netsh advfirewall set allprofiles state off

## 🖥️ 4. RDP Enabled
[RDP Enabled](images/04-rdp-enabled.png)

- Enabled Remote Desktop:
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Terminal Server" /v fDenyTSConnections /t REG_DWORD /d 0 /f
netsh advfirewall firewall set rule group="remote desktop" new enable=Yes

## ✅ 5. Final Scan (Successful Enumeration)
[Final Scan](images/05-final-scan.png)

- Open ports identified:
- 135 (MSRPC)
- 139 (NetBIOS)
- 445 (SMB)
- 3389 (RDP)

## 🧠 Key Takeaways
- Firewalls can completely obscure attack surface visibility
- Service exposure drastically changes after misconfiguration
- Enumeration is critical before exploitation
