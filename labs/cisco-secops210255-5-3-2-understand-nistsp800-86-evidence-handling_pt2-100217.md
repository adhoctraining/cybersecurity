FileName:cisco-secops210255-5-3-1-understand-nistsp800-86-evidence-handling-MMDDYY
ShowName:Cisco Cybersecurity Operations
TopicName: 5.0 Incident Handling
EpisodeName:Understand NIST SP800-86 Evidence Handling
Description: In this episode, Zach and Ronnie describe Evidence Handling as documented in NIST SP800-86. They explore it's importance and key in forensics.
Keywords: computer security incident, incident handling, incident response, information security
#### Understand NIST SP800-86 Evidence Handling
---

* 5.4 Describe these concepts as they are documented in 
  NIST SP800‐86
	+ 5.4.a Evidence collection order
		- Recommended steps to be included in evidence
		  collection use standard process:
			+ Identify Data Sources
			+ Develop Data Aquisition Plan
			+ Acquire the Data
			+ Verify Data Integrity
		- Prioritize based on Value of Data, volatility and
		  amount of effort required.
	+ 5.4.b Data integrity
		- Should use a write-blocker during backups and imaging to prevent the computer from writing to the its storage media.
		- Should use hashes for verification
		- Backups accessed read-only
	+ 5.4.c Data preservation
		- Criteria for determining volatile OS data preservation
		  should be made in advance of the collection.
		- This may be based on the effort required to collect
		  the volatile OS data.
	+ 5.4.d Volatile data collection
		- Risks associated with such collection should be
		  weighed against the potential for recovering important
		  information.
			+ Should know how each tool can affect or alter
			  system during collection of data.
			+ Should use a forensic tool that enables accurate
			  data collection
