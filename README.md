CYBERSECURITY-LAB-ENVIRONMENT-SETUP

Building an isolated virtual lab for penetration testing and ethical hacking practice

Project Overview
The aim of the project is to setup a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled environment where cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security-testing activities can be performed safely and repeatedly.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

Objectives

The main objectives of this project are to:

Install and configure VirtualBox.

Install/import Kali Linux as a virtual machine.

Create a private NAT Network for the cybersecurity lab.

Configure network connectivity for Kali Linux.

Assign a consistent IP address to the Kali VM.

Verify network connectivity and DNS resolution.

Take a clean VM snapshot for recovery.

Document the complete setup process.

Prepare the environment for future cybersecurity projects.

🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

Network reconnaissance

Port scanning

Vulnerability assessment

Packet analysis

Web security testing

Exploitation practice


Security-tool experimentation
⚠️ Important: This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

🏗️ Lab Architecture
<img width="1346" height="616" alt="image" src="https://github.com/user-attachments/assets/a7f7f7c4-dcb9-42cb-8155-3c6828d54780" />


Additional target machines can be added to the same virtual network in future projects.

⚙️ Lab Configuration

🧩 Component	⚙️ Configuration
🖥️ Host OS	Windows 10
🧠 Host RAM	16 GB
⚡ Processor	Intel Core i5
🧰 Hypervisor	VirtualBox 7.2.2
🐉 Security OS	Kali Linux 2026.3
🧠 Kali RAM	2048 MB
🌐 Virtual Network	NAT Network
📡 Network Address	10.0.0.0/24
🐧 Kali IP Address	10.0.0.2/24
🚪 Default Gateway	10.0.0.1
🌍 DNS Server	8.8.8.8
🔮 Future VM Range	10.0.0.3–10.0.0.99

🪜 Lab Setup Procedure

Step 1. Install 7-Zip
7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive.

Tool: 7-Zip

Step 2. Install VirtualBox
VirtualBox was installed as the hypervisor.

Step 3. Create the NAT Network
A dedicated NAT Network was created in VirtualBox.

Configuration: Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled
<img width="1920" height="1080" alt="Screenshot 2026-10-25 215820" src="https://github.com/user-attachments/assets/087c2d09-9be3-4341-9cb5-3accae50a711" />


A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

Step 4. Import Kali Linux
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:

Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
The VM was allocated:

RAM: 2048 MB

\<img width="970" height="593" alt="Screenshot 2026-10-25 221438" src="https://github.com/user-attachments/assets/60030854-eea0-42f6-b931-9f9e54c8dfb2" />


<img width="812" height="620" alt="Screenshot 2026-10-29 102334" src="https://github.com/user-attachments/assets/0ed7b2d4-0516-4a67-ae8f-18187b8763a9" />

 A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

Step 5. Configure the Kali Linux Network
The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

IP Address: 10.0.0.2

Subnet Mask: 255.255.255.0

Gateway: 10.0.0.1

DNS: 8.8.8.8


<img width="741" height="606" alt="Screenshot 2026-10-30 124130" src="https://github.com/user-attachments/assets/8175fad0-7e0d-46dc-bcda-a49f99b19ca1" />

Step 6. Create a Clean VM Snapshot
After completing the initial configuration, a VirtualBox snapshot was created.
<img width="1065" height="615" alt="Screenshot 2026-10-30 123959" src="https://github.com/user-attachments/assets/dd62660c-ef00-4328-85b3-adf753ab7d67" />

Kali Linux VM Setup
The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

🔎 Lab Verification
✅ Test	🧾 Command	🎯 Expected Result
🌐 Check IP address	ip a	Correct Kali IP displayed
📡 Test gateway	ping 10.0.0.1	Successful replies
🌍 Test Internet connectivity	ping 8.8.8.8	Successful replies
🔎 Test DNS resolution	nslookup networkwalks.com	Domain resolves
🧰 Verify Nmap	nmap --version	Nmap version displayed
🔄 Verify snapshot	Restore snapshot and run ip a	Baseline configuration restored
Example Results
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
🐞 Problems Encountered & Solutions
Documenting problems is an important part of the project.

Problem 1. Internet Connectivity After Static IP Configuration
After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
The network connection was then restarted/rebooted and connectivity was tested again.

Important: Network interface and connection names may differ between systems. Students should first identify their actual connection name before running an nmcli command.

💡 What I Learned
Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:

1. NAT vs NAT Network
A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

2. Virtual Machine Networking
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

3. Static IP Configuration
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

4. VM Snapshots
I learned that a clean snapshot should be created before performing risky or experimental activities in order to retain the original state of the machine.

5. Documentation
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

🔐 Security & Ethical Use
This laboratory is intended strictly for education purposes only.

🔗 Tools & Resources
7-Zip: https://7-zip.org/download.html
VirtualBox: https://virtualbox.org/wiki/Downloads
Kali Linux: https://kali.org/get-kali
👤 Author
Eti-Ima Imo Ebisoh
Cybersecurity Intern at networkwalks cohort B084

LinkedIn:www.linkedin.com/in/eti-ima-imo-ebisoh-03b56b2a3


📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
