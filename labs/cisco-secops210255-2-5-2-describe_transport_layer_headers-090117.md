###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-4-describe_transport_layer_headers-MMDDYY
{EpisodeName}Describe Transport Layer Headers
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### Describe Transport Layer Headers
------------------------------------------------------------
* 2.2.d TCP
	- Basic Operations:
		+ TCP provides reliability, flow control and stateful
		  communication.
		+ Reliability is the chief benefit.
			- this is through acknowledgement at Layer 4 rather
			  than upper layer protocol--this is required.
			- if no acknowledgement is received, packets are
			  retransmitted. --drawback, it slows down traffic.
		+ Flow control addresses the issue using Windows.
		+ More fields in TCP header to maintain state and flow
		  control between sender and receiver
		+ TCP Three-Way Handshake (Wireshark)
``` 
Kali Linux 
Launch Wireshark
browse to itpro.tv
show sequencing information for 3 way handshake
```
	- Many upper layer protocols relay on TCP reliability.
		+ DNS Zone Transfers
		+ HTTP and HTTPS
		+ SMB
		+ SSL/TLS
		+ FTP
	- Security Vulnerabilities at the Headers:
		+ connection oriented (reliable) TCP knows when
		  problems occur using sequence and acknowledgement 
		  numbers to track data exchange.
		+ Port 0: anomalous, improper port setting
		+ Open TCP port as static source over multiple TCP 
		  connections. (tuple must be unique)
		+ SYN scan where source port increments but
		  destination port is 0 to elicit a RESET. This test
		  if host is alive. 
		+ TCP Checksums: Calculated by Source and checked by
	  destination only.
	- TCP Flags
		+ SYN - starts session
		+ FIN - ends session
		+ RESET stops a session
		+ ACK - data received by sender
		+ PSH - tells sender to write and send buffered data 
		  and tells destination to send to Layer 4. 
		+ URGENT data has the highest priority.
		+ Invalid flag combos
			- SYN and FIN flags set (violation of RFC
			  793)
			- sometimes just due to corruption along the 
			  data path to the destination.
* 2.2.e UDP
	- Port 0 is unusual activity
	- Source ports are generally above 1023 (ephemeral)
	- each new sending connection, different ephemeral
	  port selected.
	- destination normally responds with a "port unreachable"
	  message to non-listening UDP port. But the absense of the
	  "port unreachable" is assumed to be an open port.  This 
	  may be an inherent false positive.
	- UDP length field
		+ theorhetically, max length 65515
		+ Many applications limit length to 8192 or less.  
		  e.g. DNS limited to 512 bytes.