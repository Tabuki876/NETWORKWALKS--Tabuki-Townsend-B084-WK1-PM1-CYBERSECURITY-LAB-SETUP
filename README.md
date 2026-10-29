NETWORKWALKS — Tabuki-Townsend-B084-WK1-PM1-CYBERSECURITY-LAB-SETUP

** Cybersecurity Lab Environment Setup
Building an isolated virtual lab for penetration testing and ethical hacking practice

**Project Overview
This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.
The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly. The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

**Objectives
The main objectives of this project are to:
•	Install and configure VirtualBox.
•	Install/import Kali Linux as a virtual machine.
•	Create a private NAT Network for the cybersecurity lab.
•	Configure network connectivity for Kali Linux.
•	Assign a consistent IP address to the Kali VM.
•	Verify network connectivity and DNS resolution.
•	Take a clean VM snapshot for recovery.
•	Document the complete setup process.
•	Prepare the environment for future cybersecurity projects.





🛡️ Purpose of the Lab
The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing. It can be used for activities such as:
•	Network reconnaissance
•	Port scanning
•	Vulnerability assessment
•	Packet analysis
•	Web security testing
•	Exploitation practice
•	Security-tool experimentation


🏗️ Lab Architecture

Additional target machines can be added to the same virtual network in future projects.
⚙️ Lab Configuration
🧩 Component	⚙️ Configuration
🖥️ Host OS	Windows 11
🧠 Host RAM	10 GB
⚡ Processor	Intel Core i7
🧰 Hypervisor	VirtualBox 7.2
🐉 Security OS	Kali Linux 2026.2 (Batch 84 Update)
🧠 Kali RAM	2048 MB
🌐 Virtual Network	NAT Network
📡 Network Address	10.0.0.0/24
🐧 Kali IP Address	10.0.0.2/24
🚪 Default Gateway	10.0.0.1
🌍 DNS Server	8.8.8.8
🔮 Future VM Range	10.0.0.3–10.0.0.99


🪜 Lab Setup Procedure
•	Step 1. Install 7-Zip: 7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive. (Tool: 7-Zip)
•	Step 2. Install VirtualBox: VirtualBox was installed as the hypervisor.
•	Step 3. Create the NAT Network: A dedicated NAT Network was created in VirtualBox.
o	Configuration: Network Name: NatNetwork | IPv4 Prefix: 10.0.0.0/24 | DHCP: Enabled | IPv6: Disabled
o	Why: A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity, allowing future attacker and target VMs to communicate within the lab.
•	Step 4. Import Kali Linux: The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.
o	Adapter 1 Settings: Attached to: NAT Network | Network: NatNetwork | Adapter Type: Intel PRO/1000 MT Desktop
o	Resources: RAM: 2048 MB. A shared folder was also configured for transferring required files between the host operating system and the Kali VM.
•	Step 5. Configure the Kali Linux Network: The Kali Linux network configuration was checked and configured with a consistent IPv4 address:
o	IP Address: 10.0.0.2
o	Subnet Mask: 255.255.255.0
o	Gateway: 10.0.0.1
o	DNS: 8.8.8.8
o	Note: A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.
•	Step 6. Create a Clean VM Snapshot: After completing the initial configuration, a VirtualBox snapshot was created (Clean Kali - Network Setup). This represents the clean baseline of the laboratory so the machine can be restored if a future exercise damages the configuration.
🔎 Lab Verification
✅ Test	🧾 Command	🎯 Expected Result
🌐 Check IP address	ip a	Correct Kali IP displayed
📡 Test gateway	ping 10.0.0.1	Successful replies
🌍 Test Internet connectivity	ping 8.8.8.8	Successful replies
🔎 Test DNS resolution	nslookup networkwalks.com	Domain resolves
🧰 Verify Nmap	nmap --version	Nmap version displayed
🔄 Verify snapshot	Restore snapshot and run ip a	Baseline configuration restored
Example Results
•	IP Address: 10.0.0.2/24
•	Gateway: 10.0.0.1
•	DNS: 8.8.8.8

🐞 Problems Encountered & Solutions
•	Problem 1. Internet Connectivity After Static IP Configuration: After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.
o	Workaround:
Bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
The network connection was then restarted/rebooted and connectivity tested again. (Note: Network interface and connection names may differ between systems).

💡 What I Learned
1.	Virtual Machine Networking: Learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.
2.	Static IP Configuration: Learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.
3.	VM Snapshots: Learned that a clean snapshot should be created before performing risky or experimental activities to provide a known-good recovery point.
4.	Documentation: Learned that documenting commands, configurations, screenshots, problems, and solutions is an essential part of a professional cybersecurity project.


👤 Author & Project Information
•	Author: Tabuki Townsend (Batch 84) 
•	Program Name: Cybersecurity at Networkwalks
•	Week: 01 | Project: Cybersecurity & Pentesting Lab Setup
•	Repository: GitHub

