# Cybersecurity 
## What is cybersecurity? 

There are many definitions, but for our purposes cybersecurity is the mitigation of risk compromising, stealing, or corrupting data or network traffic. 
Big Box Sales. Inc
## Attackers and Attacks
## Types of Attackes
### Nation States
### Cybercriminals
### Hacktivist
### Script Kiddie
## Tactics, Techniques and Procedures (TTP's)
Red team vs. Blue team, Blackhat vs. Whitehat penetration testing, risk management frameworks, defense and countermeasures, and security information and event management (SIEM) are just ways cybersecurity canbe segmented. 

### What Does TTP Mean in Cybersecurity?

TTP stands for Tactics, Techniques, and Procedures, and this acronym is used when talking about the behavior of a threat actor. Here’s how the National Institute of Standards and Technology defines its individual elements:

Essentially, tactics describe what cybercriminals plan to achieve. Examples include obtaining access to sensitive information or making certain important resources unavailable to damage the victim financially or reputationally.

Techniques are the general strategies cybercriminals use to breach their victims’ defenses, and they roughly correspond to the major cyber threats, such as malware, phishing, man-in-the-middle attacks, password compromise, and others.

Finally, procedures are the specific steps cybercriminals follow to achieve their nefarious goals. They may correspond to specific software vulnerabilities, such as the recently discovered Microsoft Exchange server elevation of privilege vulnerability, or they may reflect gaps in the victims’ defenses.

According to MITRE, a not-for-profit organization providing a globally-accessible knowledge base of adversary tactics and techniques based on real-world observations, collecting and filtering data based on TTPs is an effective method for detecting malicious activity.

“This approach is effective because the technology on which adversaries operate (e.g., Microsoft Windows) constrains the number and types of techniques they can use to accomplish their goals post-compromise,” explains MITRE.

TTPs shouldn’t be confused with Indicators of Compromise, or IoCs for short. If TTPs describe what cybercriminals do, then IoCs talk about the consequences of their actions.

If cybercriminals were bank robbers, then TTPs would be the strategies used to reach the inside of the vault. IoCs, on the other hand, would be anything from a smashed lock to missing money.

We can illustrate the difference between IoCs and TTPs on a phishing attack whose goal is to steal login credentials:

When detected, IoCs ignite incident response activities to protect valuable systems from threat actors. TTPs give the security team the information needed to protect all possible attack vectors.
Should SMBs Study TTPs?

Small and medium-sized businesses rarely employ a cybersecurity team—let alone one large enough to dedicate time to the study of current and emerging TTPs.

Instead of trying to assemble such a team, SMBs are much better off outsourcing this activity to a managed security service provider (MSSP) that provides threat intelligence and threat detection services.

SMBs that have yet to implement beginning-to-end strategies to improve their cybersecurity defenses can especially benefit from a partnership with an experienced MSSP, borrowing its experience to implement cybersecurity best practices, such as:

Multi-factor authentication (MFA): Many TTPs used by today’s cybercriminals target weak authentication and login mechanisms. MFA, which strengthens the authentication process by adding one or more extra layers of protection, can block as much as 99.9 percent of identity attacks.
Cybersecurity awareness training: People remain the weakest link in the cybersecurity chain because their actions can sabotage even the most well-thought-out policies and controls. Cybersecurity awareness training can strengthen this link and make it less likely to break.
Endpoint protection: The proliferation of the hybrid work model has led to an explosion of end-points (laptops, tablets, smartphones, etc.), each of which represents a possible attack vector. Modern endpoint protection solutions help discover and defend these endpoints regardless of where they’re physically located.

At Aligned Technology Solutions, we understand the Tactics, Techniques, and Procedures cybercriminals use to accomplish their objectives, and we’re happy to share this knowledge with SMBs like yours. Book a consultation with us today.

### [Mitre&ATTACK Framework](https://attack.mitre.org/)


### The cyber kill chain -  7 Stages of a Cyber Kill Chain

Stage 1:  Reconnaissance:

Stage 2: Weaponization

Stage 3: Delivery

Stage 4: Installation

Stage 5: Lateral Movement

Stage 6: Command and Control (C2)

Stage 7: Execution

What is an Example of a Cyber Kill Chain?

The cyber kill chain example below shows the different stages at which a security team can detect and prevent a custom ransomware attack:

Step 1: Hackers run reconnaissance operations to find a weakness in the target system.
Step 2: Criminals create an exploit ransomware program and place it inside an email attachment. Hackers then send a phishing email to one or more employees.
Step 3: A user makes the mistake of opening and running the program from the inbox.
Step 4: Ransomware installs on the target network and creates a backdoor.
Step 5: The program calls to malicious infrastructure and notifies the attacker about the successful infection.
Step 6: Intruders move laterally through the system to find sensitive data.
Step 7: Attackers achieve C2 control and start encrypting target files.

Reconnaissance
Topology discovery
OS fingerprinting
Service discovery

Discovery Scan
One of the first steps in penetration testing is reconnaissance. Reconnaissance is the process of gathering information to obtain a better understanding of a network. It enables you to create list of target IP addresses and devise a plan of attack. Once you have a list of IP addresses, you can run a discovery scan to learn more about those hosts. A discovery scan identifies the operating systems that are running on a network, maps those systems to IP addresses, and enumerates the open ports and services on those systems.

A discovery scan is the internal Metasploit scanner. It uses Nmap to perform basic TCP port scanning and runs additional scanner modules to gather more information about the target hosts. By default, the discovery scan includes a UDP scan, which sends UDP probes to the most commonly known UDP ports, such as NETBIOS, DHCP, DNS, and SNMP. The discovery scan tests approximately 250 ports that are typically exposed for external services and are more commonly tested during a penetration test.

During a discovery scan, Metasploit Pro automatically adds the host data to the project. You can review the host data to obtain a better understanding of the topology of the network and to determine the best way to exploit each target. Oftentimes, the network topology provides insight into the types of applications and devices the target has in place. The more information that you can gather about a target, the more it will help you fine-tune a test for it.

How a Discovery Scan Works
A discovery scan can be divided into four distinct phases:

Ping scan
Port scan
OS and version detection
Data import
Ping Scan
The first phase of a discovery scan, ping scanning, determines if the hosts are online. The discovery scan sets the -PI option, which tells Nmap to perform a standard ICMP ping sweep. A single ICMP echo request is sent to the target. If there is an ICMP echo reply, the host is considered ‘up’ or online. If a host is online, the discovery scan includes the host in the port scan.

Port Scan
During the second phase, port scanning, Metasploit Pro runs Nmap to identify the ports that are open and the services are available on those ports. Nmap sends probes to various ports and classifies the responses to determine the current state of the port. The scan covers a wide variety of commonly exposed ports, such as HTTP, telnet, SSH, and FTP.

The discovery scan uses the default Nmap settings, but you can add custom Nmap options to customize the Nmap scan. For example, the discovery scan runs a TCP SYN scan by default. If you want to run a TCP Connect Scan instead of a TCP SYN Scan, you can supply the -sT option. Any options that you specify override the default Nmap settings that the discovery scan uses.

OS and Version Detection
After the discovery scan identifies the open ports, the third phase begins. Nmap sends a variety of probes to the open ports and detects the service version numbers and operating system based on how the system responds to the probes. The operating system and version numbers provide valuable information about the system and help you identify a possible vulnerability and eliminate false positives.

Packet capture
Email harvesting
Social media profiling
Social engineering
DNS harvesting
Phishing

Infrastructure
Wireless vs. wired
Virtual vs. physical
Internal vs. external
On-premises vs. cloud

Tools 
Netdiscover
NMAP
Wireshark
Hydra
TTP  (Tactics, Techniques, and Procedures)
Essentially, tactics describe what cybercriminals plan to achieve. Examples include obtaining access to sensitive information or making certain important resources unavailable to damage the victim financially or reputationally.
Techniques are the general strategies cybercriminals use to breach their victims’ defenses, and they roughly correspond to the major cyber threats, such as malware, phishing, man-in-the-middle attacks, password compromise, and others.
Finally, procedures are the specific steps cybercriminals follow to achieve their nefarious goals. They may correspond to specific software vulnerabilities, such as the recently discovered Microsoft Exchange server elevation of privilege vulnerability, or they may reflect gaps in the victims’ defenses.
Host scanning
Network mapping
Packet analyzer
Vulnerability scanner
Packet analysis
Protocol analysis
Traffic analysis
Netflow analysis
Wireless analysis

References
Johnson, C., etal. October 2016. NIST SP 800-150 -  Guide to Cyber Threat Information Sharing. https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-150.pdf



## Data Breaches
### Target
### Equifax
### The Office of Personnel Management

Security
Network Security
Labs 
C:\Users\pcmechanix\Downloads\personal.cloud\Cisco SECOPS_210-255\Cisco SECOPS
* 4.1.1.7 Lab - Tracing a Route.docx
* 4.1.2.10 Lab - Introduction to Wireshark.docx
* 4.4.2.8 Lab - Using Wireshark to Examine Ethernet Frames.docx
* 4.5.2.10 Lab - Exploring Nmap.docx
* 4.5.2.4 Lab - Using Wireshark to Observe the TCP 3-Way Handshake.docx
* 4.6.2.7 Lab - Using Wireshark to Examine a UDP DNS Capture.docx
* 835 4.6.4.3 Lab - Using Wireshark to Examine TCP and UDP Captures.docx
* 717 4.6.6.5 Lab - Using Wireshark to Examine HTTP and HTTPS Traffic.docx
* 5.1.1.7 Lab - Using Wireshark to Examine Ethernet Frames.docx




