###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-7-identify_netflow_v5_records-MMDDYY
{EpisodeName}Identify NetFlow v5 Records
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### Identify Netflow v5 Records
------------------------------------------------------------
* 2.3 Identify the elements from a NetFlow v5 record from a
  security event
  	- What is NetFlow?
		+ is a technology that provides visibility into the 
		  how the network is working in many ways:
			- Application and Network Utilization
			- Network Productivity
			- Impact of network changes
			- Network anomalies and security vulnerabilities
			- compliance issues
		+ it helps to an administrator or analyst to understand
		  who, what, when, where and how network traffic flows.
		+ it increases awareness of network which reduces "blindspots"
		+ Allows administrators to see how the network is used
		  to improve or change network for better utilization.
	- Analyst can examine the IP flows across entire enterprise
	- Captures every IP flow going through Netflow capable devices:
		+ IP 5-tuple information
		+ Communication time
		+ Amount of data transferred
		+ for each particular IP flow, we can see who, what,
		  where, how, and when.
		+ helps to identify weird or out of place traffice on 
		  network and alert us.
	- Should help the analyst to answer:
		+ how long the data flow was active
		+ the application (undefined is not good)
		+ no return traffice from server
		+ Find where the originating traffic is from.
	- 9 versions of NetFlow 
	- NetFlow v5 is first commonly deployed on routers but
	  restricted to IP v4 flows. (18 data elements)
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
		+ A Flow Record answers the question: "What data do I want to measure?"
			- a combination of key and non-key fields is a
			  record.
			- used to identify packets to be collected
			- defines types of counters gathered per flow
			- `show running-config flow record`
		+  A flow exporter answers: "Where do I want to send flow data?"
			- `show running-config flow exporter` 
				+ note destination IP
				+ note destination port (default: UDP/2055)
				+ note source IP/vlan
				+ note template data timeout: this is the 
				  freq in secs the switch will advertise a
				  template to the exporter telling which
				  fields are exported.
		+ Flow monitor answers: "How do I want to cache the
	       information?
			- Monitor references the Flow record and exporter.
			- this is applied on an interface on switch
			- `show running-config flow monitor` 
		+ Application: "Which interface/vlan to monitor?" 
			- `show running-config interface gigabitethernet 1/0/1`
				+ note the `cts manual` : if using security
				  groups then this must be part of the
				  configuration
		+ Netflow Information
		+ Specific NetFlow Host Communications