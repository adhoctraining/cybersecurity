 ###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-0-network_intrusion_analysis-MMDDYY
{EpisodeName}
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### 2.0 Network Intrusion Analysis 22%
------------------------------------------------------------
* 2.1 Interpret basic regular expressions
	+ What is it?
		- Sequence of characters than defines a search pattern.
		- This can be used with grep, markdown, filters like in
		  wireshark just to name a few examples.
		- Demo:
```
Use Router for basic primer for RegEx.
show run | include ^interface | ^_ip address
```
	+ Why should I care and how do I do it?
		- Demo:
``` 
Use Wireshark and filter to show easy way to filter out what is not needed.  What if you need to change add a second string to the filter:
--first filter:  http
--second filter: http and ip.dst\==10.10.100.139
--second filter: http and ip.dst\==10.10.100.139 and ip.src\==69.64.49.212
**The Point** Works if you know exactly what you're 
looking for.
```
	+ When do I need it?
		- Demo:
```
When there is more uncertainty in the search string
example1 : "ip.src_host matches 173\.194\.113\.1[69][14]" (no quotes)
example2: "and tcp" (no quotes)  to regular expression match.
```
* 2.2 Describe the fields in these protocol headers as they
relate to intrusion analysis:
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
		- "Why Attack Layer 2?"
			+ This can be answered with 2 another question: "What OSI Layers do Filtering, Access Control Lists, Authentication and Application control protect? Answer, not Layer 2!! 
			+ Layer 2 is considered a trusted layer the Ethernet Layer header has inforamtion about what? Layers 1 and 2.
			+ Many of the attacks rely on lack of
			  authentication at Layer 2 during communications
			  (MITM possible).
			+ Wired attacks at Layer 2: CAM table exhaustion, ARP Spoofing, DHCP Exhaustion, and VLAN hopping.
			+ Wireless attacks at Layer 2: Hidden Node, Deauth, Fake Access points.
	+ 2.2.b IPv4
		- IP Version Number: if a packet with invalid IP version arrives at router, it should be discarded, no error message to host (RFC 1122).
		- Protocol number
		- Differentiated Service Byte (ToS)
		- Don't Fragment Flag (DF)
			+ insertion attack
		- More Fragments Flag (MF)
			+ mappiing technique used by trying to get an ICMP IP "reassembly time exceeded" message from target host.
			+ Attacker sends incomplete set of fragments to target. Target is listening is on the port scanned.
			+ After the first fragment received the target sets
			  a timer.  Attacker then doesn't send all the packets before the timer expires.  Target then sends a "IP reassembly time exceeded" back to sending host.
		- IP Numbers (IP addresses)
			+ IP addresses from same network address entering from outside.
			+ 127.0.0.1 should never be source address
			+ Internet Address source should never be RFC 1918
			+ Traffic leaving subnet should never have different IP address range than your subnet or a loopback.
			+ Broadcast traffic should not leave your subnet.
		- IP Identification Numbers
			+ Each new datagram must generate a unique ID
			  number.
			+ Fragments should all share the same
			  identification numbers (aka. Fragment ID number).
			  The receiving host uses this to reassemble all
			  fragments to datagram.
			+ more ambiguous because this can be manipulated.
		- TTL (Time to Live)
			+ insertion attack: manipulate TTL to be too low
			  before it reaches it's destination.
			+ TTL and IP Identity can be used to spot
			+ spoofing attack.
			     - identity TTL from same source
			     - small increments in ID
		- IP Checksum (RFC 1071):
			+ Divide IP header data into 16 bit fields.
				- Binary and then Complementary 1s operation
				  is calculated.
			+ Recomputed each hop from source to destination
			+ Not the same as TCP, UDP and ICMP checksums
			  which are only calculated at the destination.
	+ 2.2.c IPv6
		- multiple occurences of extension headers in Atomic
		  Fragments
			+ IPv6 header extensions are to occur only once
			  in datagram but some OS accept multiple atomic
			  fragments with same extentions. (RFC 2460)
		- nested fragements created from allowance of multiple
		  occurences of extension headers.
		- Malformed packets delivering payloads in fragments
		  other than the very first.
		- IP Fragmentation Overlapping accepted by many OS.
		  Overlapping IPv6 Extension headers creates new
		  attack vectors.
	+ 2.2.d TCP
		- Upper Layer Header field
		- connection oriented (reliable) TCP knows when
		  problems occur using sequence and acknowledgement
		  numbers to track data exchange.
		- More fields in TCP header to maintain state and flow
		  control between sender and receiver
		- Port 0: anomalous, improper port setting
		- Open TCP port as static source over multiple TCP
	       connections.
		- SYN scan where Source port increments but
		  destination port is 0 to elicit a RESET. This test
		  if host is alive.
		- used to circumvent firewalls, routers and IDSs 
		- TCP Checksums: Calculated by Source and checked by
		  destination only.
		- TCP Flags
			+ SYN - starts session, FIN - ends session, RESET
			  stops a session, ACK - data received by sender, PUSH - tells sender to write and send buffered data and tells destination to send to Layer 4. URGENT data has the highest priority.
			+ Invalid flag combos
				- SYN and FIN flags set (violation of RFC
				  793)
				- sometimes just due to corruption along the 
				  data path to the destination.
			+ ECN Flag
			+ OS Fingerprinting
			+ Retransmissions
			+ TCP Windows Size
	+ 2.2.e UDP
		- Port 0 is unusual activity
		- Source ports are generally above 1023 (ephemeral)
		- each new sending connection, different ephemeral
	       port selected.
		- destination normally responds with a "port unreachable" message to non-listening UDP port. But the absense of the "port unreachable" is assumed to be an open port.  This may be an inherent false positive.
		- UDP length field
			+ theorhetically, max length 65515
			+ Many applications limit length to 8192 or less.  e.g. DNS limited to 512 bytes.
	+ 2.2.f ICMP
		- No ports but Type and Code
		- identification and sequence numbers for DDoS or hidden protocol exchanges.
	+ 2.2.g HTTP
		- HTTP users headers to communicate between client and 
		  server. (create, use and end client and server
		  connection)
		- Attackers can launch attacks by adding **executable**
		  code within HTTP header (Firewalls do not check
		  content)
		- use netwitness (identify direct to IP host, non-standard unser-agent, no referrer)
		- content-type
		- user agent: 
		- uncommon header types
		- referrer field: something in it
* 2.3 Identify the elements from a NetFlow v5 record from a
  security event
	- 9 versions of netflow 
	- NetFlow v5 is first commonly deployed on routers but restricted to IP v.4 flows.
		- Key fields: Src/Dst IP, Src/Dst Port, IP Proto, ToS and Input Interface
		- Accounting: Packets, Octets, Start/End time, Output Interface.
		- Other: Bitwise OR of TCP flags, Src/Dst AS and IP Mask.
		- Packet format adds sequence numbers for detecting lost exports.
	- NetFlow v5 fields:
		+ AS
		+ Proto/Port
		+ Src Prefix
		+ Dst Prefix
		+ Prefix
		+ Destination
		+ Source/Destination
		+ Full Flow
	- Demo:
		+ Router Configuration:
			- (interface) `ip flow egress` 
			- (interface) `ip flow ingress` 
			- `ip flow-export version 5` 
			- `ip flow-export destination 10.0.46.200 2002` 
			- `ip flow top-talkers`
				+ `top 10` 
				+ `sort-by bytes` 
			- version specific 
				+ prior to IOS 12.4 `ip route-cache flow` 
				+ after IOS 12.4 `ip flow [ingress/egress]
			- verify: 
				+ `show ip cache flow` 
				+ `show ip flow top-talkers`
* 2.4 Identify these key elements in an intrusion from a 
  given PCAP file
	+ 2.4.a Source address
	+ 2.4.b Destination address
	+ 2.4.c Source port
	+ 2.4.d Destination port
	+ 2.4.e Protocols
	+ 2.4.f Payloads
* 2.5 Extract files from a TCP stream when given a PCAP file 
  and Wireshark
	+ Explain When and Why
		- Intrusion Prevention System Alert Analysis
		- Sguil
	+ Explain How
		- Wireshark> File > extract objects
* 2.6 Interpret common artifact elements from an event to
  identify an alert
	+ 2.6.a IP address (source / destination)
	+ 2.6.b Client and Server Port Identity
	+ 2.6.c Process (file or registry)
	+ 2.6.d System (API calls)
	+ 2.6.e Hashes
	+ 2.6.f URI / URL
* 2.7 Map the provided events to these source technologies
	+ 2.7.a NetFlow
	+ 2.7.b IDS / IPS
	+ 2.7.c Firewall
	+ 2.7.d Network Application Control
	+ 2.7.e Proxy logs
	+ 2.7.f Antivirus
* 2.8 Compare and contrast impact and no impact for these items
	+ 2.8.a False Positive
	+ 2.8.b False Negative
	+ 2.8.c True Positive
	+ 2.8.d True Negative
* 2.9 Interpret a provided intrusion event and host profile 
  to calculate the impact flag generated by Firepower 
  Management Center (FMC)
	+ Impact Flag of 0:
		- Observed: Generic information, Events not on profiled
		  network
		- Action: None but noted
	+ Impact Flag of 4:
		- Observed: Previously unseen on protected network
		- Action: Gather more information, check for
		  connections
	+ Impact Flag of 3:
		- Observed: Event observed but relevent port or
		  protocol not used
		- Action: Gather more information, verify associated
		  ports are closed
	+ Impact Flag of 2:
		- Observed: Event has no associated vulnerability, port
		  or protocol is in use.
		- Action: Investigate; Find exposed host
	+ Impact Flag of 1:
		- Observed: Indication of Compromise; Host is
		  vulnerable
		- Action: Take all measures; host is compromised or
		  vulnerable.
	+ FMC Demo:
```
		- Hide Address Bar (in recording) Zoom IN
		- Show Where Impact Flag is configured
			+ Policies> Actions> Alerts
		- Show 
		  
[Frame Type]:https://en.wikipedia.org/wiki/EtherType
