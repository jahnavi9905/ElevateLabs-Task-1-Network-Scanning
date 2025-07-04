Practical Report: Scan Your Local Network for Open Ports

Objectives: To identify open ports on devices within your local network, understand the services running on those ports, and assess potential security risks.

Tools Used:
Nmap – Network scanning tool.
Wireshark (optional) – For packet capture and traffic analysis.
Operating System – Windows 10 (can vary).
Command Line / Terminal – For executing scan commands.

Step-by-Step Process:
Step 1: Install Nmap
Downloaded and installed Nmap from https://nmap.org/download.html

Step 2: Identify Local IP Range
Ran the following command to find local IP: ipconfig 

Step 3: Perform TCP SYN Scan (Stealth Scan)
Command Used: nmap -sS 192.168.1.4
The -sS flag runs a SYN scan which is faster and stealthier than a full TCP connect scan.

Step 4: Review Results
Starting Nmap 7.97 ( https://nmap.org ) at 2025-06-23 21:14 +0530
Nmap scan report for 192.168.1.4
Host is up (0.000010s latency).
Not shown: 997 closed tcp ports (reset)
PORT    STATE SERVICE
135/tcp open  msrpc
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds

Nmap done: 1 IP address (1 host up) scanned in 0.94 seconds

Step 5: Optional – Analyze with Wireshark

Step 6: Identify Potential Security Risks
Open Ports Identified on 192.168.1.4:
Port	State	Service	Description
135	open	msrpc	        Microsoft RPC service used for DCOM communication
139	open	netbios-ssn  	NetBIOS Session Service, used for Windows file/printer sharing
445	open	microsoft-ds	SMB over TCP (common in Windows networking)
Security Risks Identified:
Open SMB Port (445) poses the highest risk — vulnerable to known exploits if not properly secured.
NetBIOS and RPC services may leak system info, allow network enumeration, or be leveraged in lateral movement attacks.
On a corporate or university network, these ports should be restricted by firewall policies and monitored regularly.

Step 7: Save Scan Results for Documentation
nmap -sS 192.168.1.4 -oN host_192.168.1.4_scan.txt

