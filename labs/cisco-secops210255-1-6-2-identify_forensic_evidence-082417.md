##Cisco Cybersecurity Operations (210-255)
{FileName}cisco-secops210255-1-6-identify_forensic_evidence-MMDDYY
{EpisodeName}Identify Forensic Evidence
{ShowName}Cisco Cybersecurity Operations
{Keywords}Threat analysis, computer forensics, CVSS, Vulnerability Scoring v.3.0, Threat Grid, NTFS, FAT
###Identify Forensic Evidence
* Define some terms and review basic forensic evidence procedures.
	+ Computer Forensics: 
		- "[Forensics] is the process of using scientific knowledge for collecting, analyzing, and presenting evidence to the courts. (The word forensics means “to bring to the court.” ) Forensics deals primarily with the recovery and analysis of latent evidence."
		- US-CERT defines it: "as the discipline that combines elements of law and computer science to collect and analyze data from computer systems, networks, wireless communications, and storage devices in a way that is admissible as evidence in a court of law."
	+ Chain of Custody
	+ [Order of Volatility] (RFC 3227, 2.1)
		- CPU, cache and register content
		- Routing table, ARP Cache, process table, kernel stats
		- Memory
		- Temporal File System /swap space
		- Data on Hard Disk
		- Remotely Logged data
		- Data contained on arhival media.
* 1.6 Compare and contrast three types of evidence 
	+ 1.6.a Best evidence 
		- Best Evidence Rule: the best evidence offered in court
		  is the original.  Electronic evidence has issues.
			+ What if evidence only resides on RAM?
			+ Can Electronic Data Corrupt?
			+ Can Electronic Data be damaged during
			  investigation?
			+ must remember images and order of volatility
		- Must turn to the [Federal Rules of Evidence Article X,
 Rule 1001].
			+ paragraph 3 Original... "If data is stored in a computer or similar device, any printout or other output **readable by sight**, show to reflect the data accurately.
	+ 1.6.b Corroborative evidence 
		- Evidence that supports a theory
		- Evidence that confirm a proposition
	+ 1.6.c Indirect evidence 
		- circumstantial evidence
			- expert testimony
			- fingerprints, DNA
			- a conclusion must be drawn from the evidence
		       presented.
* 1.7 Compare and contrast two types of images 
	+ must follow "golden rule of electronic evidence": never modify the original medial if at all possible.
	+ Must produce image that is exactly the same as original.
	+ Emphasis in forensics are on accuracy and evidence
	  integrity and security.
	+ Hashing is our friend: it generates a digital fingerprint
	+ 1.7.a Altered disk image 
	+ 1.7.b Unaltered disk image
		- Bit by Bit copy of all sector
* 1.8 Describe the role of attribution in an investigation 
	+ it is about assigning blame
		- option 1: look at the evidence and see if we can
		  extrapolate and attribute the result to an 1.8a
		  asset or 1.8b threat actor
		- option 2: look at the evidence and try to apply it
		  to the suspect as the 1.8a asset or 1.8b threat actor
	+ every examination process must not be skipped or
	  overlooked.
	+ must be careful the tools used to determine attribution
	+ may not be able to confidently lead to attribution.
* Miscellany
	+ Must work with Manufacturer...e.g. iPhone cannot be accessed for evidence collection without manufacturing password form from Apple!

[Order of Volatility]:https://tools.ietf.org/html/rfc3227
[Forensics]:https://www.us-cert.gov/sites/default/files/publications/forensics.pdf
[Federal Rules of Evidence Article X, Rule 1001]:http://www.uscourts.gov/sites/default/files/Rules%20of%20Evidence.

