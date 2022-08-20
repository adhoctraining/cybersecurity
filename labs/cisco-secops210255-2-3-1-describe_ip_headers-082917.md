###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-3-1-describe_ip_headers-MMDDYY
{EpisodeName} Describe IP Headers
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### Describe IP Headers
------------------------------------------------------------
* 2.2.b IPv4
	- IP Version Number: if a packet with invalid IP version arrives at router, it should be discarded, no error message to host (RFC 1122).
	- IP Header Length
		+ 4 bit field on length of IP header (min 20 bytes)
	- Service Type (ToS)
		+ DSCP (Differentiated Service Code Point)
		+ ECN (Explicit Congestion Notification)
		+ Level of Service
	- Datagram Length (Total Length) **Tricky**
		+ 2 bytes (2^16 = 65,536 bytes max IP packet)
	- IP Identification Numbers
		+ Each new datagram must generate a unique ID number.
		+ Fragments should all share the same identification numbers (aka. Fragment ID number). The receiving host uses this to reassemble all fragments to datagram.
		+ more ambiguous because this can be manipulated.
	- Don't Fragment Flag (DF)
		+ insertion attack
	- More Fragments Flag (MF)
		+ mapping technique used by trying to get an ICMP IP
		  "reassembly time exceeded" message from target host.
		+ Attacker sends incomplete set of fragments to target.
		  Target is listening is on the port scanned.
		+ After the first fragment received the target sets
		  a timer.  Attacker then doesn't send all the packets
		  before the timer expires.  Target then sends a "IP
		  reassembly time exceeded" back to sending host.
	- TTL (Time to Live)
		+ insertion attack: manipulate TTL to be too low before
		  it reaches it's destination.
		+ TTL and IP Identity can be used to spot
		+ spoofing attack.
			- identity TTL from same source
			- small increments in ID
	- Protocol number
		+ 1 = ICMP
		+ 6 = TCP
		+ 17 = UDP
	- Header Checksum (RFC 1071):
		+ Divide IP header data into 16 bit fields.
			- Binary and then Complementary 1s operation
			  is calculated.
		+ Recomputed each hop from source to destination
		+ Not the same as TCP, UDP and ICMP checksums
		  which are **only calculated at the destination**.
	- IP Numbers (IP addresses)
		+ IP addresses from same network address entering from
		  outside.
		+ 127.0.0.1 should never be source address
		+ Internet Address source should never be RFC 1918
		+ Traffic leaving subnet should never have different IP address range than your subnet or a loopback.
		+ Broadcast traffic should not leave your subnet.
* 2.2.c IPv6
	- Version: 4 bit field,  should be a '6' not '4'
	- Traffic Class: 8 bits, similar to type of service field in
	  IPv4
	- Flow Label: 20 bits IETF doesn't specify about how to
	  mangage and process flow labels.
	- Payload Length: 16 bits Payload and Extension Headers
	- Next Header: 8 bits tells us the transport layer protocol,
	  indicates **which extension headers**
	- Hop Limit: 8 bits replaces the TTL
	- Src Address: 128 bit, Hex format
	- Dst Address: 128 bit, Hex format
	- Multiple occurences of **extension headers** in Atomic
	  Fragments 
		+ not examined or processed until the packet reaches 
	       the destination node
		+ Processing Order is important:
``` 
Simple Diagram on Processing Order of Extension 
Headers
```
		+ IPv6 header extensions are **to occur only once**
		  in datagrams but some OS accept multiple atomic
		  fragments with same extentions. [RFC 2460] There are
		  some exceptions
		+ Length of these extension headers is variable
	- Nested fragements created from allowance of multiple
	  occurences of extension headers.
	- Malformed packets delivering payloads in fragments
	  other than the very first payload.
	- IP Fragmentation Overlapping accepted by many OS.
	  Overlapping IPv6 Extension headers creates new
	  attack vectors.
[RFC 2460]:https://www.ietf.org/rfc/rfc2460.txt