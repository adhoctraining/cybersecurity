##Cisco Cybersecurity Operations (210-255)
{FileName}cisco-secops210255-1-0-endpoint\_threat\_analyis\_&\_computer_forensics-MMDDYY
{EpisodeName}
{ShowName}Cisco Cybersecurity Operations
{Keywords}Threat analysis, computer forensics, CVSS, Vulnerability Scoring v.3.0, Threat Grid, NTFS, FAT
###1.0 Endpoint Threat Analysis & Computer Forensics (15%)  
* 1.1 **Interpret the output report** of a malware analysis tool such as AMP ThreatGrid and Cuckoo Sandbox
	+ AMP ThreatGrid
		- Screen shot of an AMP Threat Grid View
	+ Cuckoo Sandbox
		- Helps to perform Sandbox Malware Analysis
		- Only works well when planned well
			+ What kind of files do I want to analyze?
			+ What volume of analyses do I want to be able 
			  to handle?
			+ Which platform do I want to use to run my
			  analysis on?
			+ What kind of information I want about the file?
		- Runs and Analyzes files to see what malware does
		  on an Isolated Windows OS, OSX, Linux and Android.
		- helps to understand how malwork works by seeing how
		  it work in realtime and the malware is not just a
		  static file.
		- results:
			+ Traces API calls performed by all processes
			  spawned by the malware.
			+ Files being created, deleted and downloaded by
			  the malware during its execution.
			+ Memory dumps of the malware processes.
			+ Network traffic trace in PCAP format.
			+ Screenshots of desktop taken during 
			  the execution of the malware.
			+ Full memory dumps of the machines
		- Demo:  
```
Cuckoo Sandbox 
```

* 1.2 Describe these terms as they are defined in the CVSS 3.0
	+ Question:
```
What is the CVSS 3.0 and why is it important?
```  
	+ CVSS (Common Vulnerability Scoring System)
		- Cisco [Common Vulnerability Scoring System (CVSS) Online Calculator, version 3.0]
		- First.org [Common Vulnerability Scoring System Version 3.0 Calculator]
		- The follow terms are all **base metrics** used to 
		  generate a score. Score between 0 and 10.
		- Two areas contribute toward the base metric score:
			+ Exploitability Metric
			+ Impact Metric
	+ Exploitability Metrics (reflect characteristics of the target that is vulnerable--vulnerability component. These components should show characteristics of what leads to a successful attack)
		- 1.2.a Attack vector (AV)
			+ Context in which the vulnerability exploitation
			  is possible.
			+ Metric value grows as the attacker is "farther"
			  away when exploiting the vulnerability.
			+ Network (N)
				- vulnerable component is tied to the network
				  stack and the attacker path follows the OSI
				  model.
				- "Remotely Exploitable": attack from a
				  remote network.
				- e.g. DoS attack using TCP packets from the
				  internet.
			+ Adjacent (A)
				- similar to the Network (N), tied to the
				  network stack, it is limited to being on
				  the same physical or logical network.
				- e.g. Bluetooth, 802.11 or same subnet
				- e.g. of attack here would be ARP flooding 
				  or IPv6 neighbor discovery flooding that
				  leads to denial of service.
			+ Local (L)
				- vulnerable component is not tied to network
				  stack.
				- Attack path is in the read, write and
				  execute capabilities.
				- Attacker may be logged on locally or on a
				  user's interaction to run a malicious file.
			+ Physical (P)
				- requires attacker to physically touch the
				  vulnerability component.
				- e.g. [Evil Maid attack]
				- Attacker has computer, briefly or
				  permanently.
				- e.g. cold boot attack--gaining access to
			       whole volume encryption keys.
		- 1.2.b Attack complexity (AC)
			+ condition beyond the **attacker's control** that
			  exist to exploit the vulnerability.
			+ e.g. collection of information, configuration
			  settings, exceptions, bad coding.
			+ The least complex attacks have higher values.
			+ Low (L)
				- Special access conditions and extenuating
				  cirumstances do not exist.
				- Attacker can expect repeatable success
				  against that vulnerability component.
			+ High (H)
				- The more complexity involved the more the 
				  attacker must to do things to overcome
				  before an attack can be successful.
				- e.g. reconnaissance, preparation to improve
				  attack success, man in the middle.
		- 1.2.c Privileges required
			+ Describes level of privilege that an attacker
			  must have to successfully exploit the
			  vulnerability.
			+ Higher metric if no privilege is required
			+ None (N)
				- Unauthorized prior to attack
				- doesn't require access to settings or files
				  to carry out attack.
			+ Low (L)
				- The attacker requires authorized low level 
				  privilege.
				- This provides basic user capabilities
			+ High (H)
				- Attacker requires authorized high level 
				  privileges
				- Provides administrative control over the 
				  vulnerable component.
		- 1.2.d User interaction (UI)
			+ requires a user, besides the attacker,
			  participate in the compromise of the vulnerable
			  component.
			+ None (N)
				- No user interaction needed to exploit
				  vulnerable component.
			+ Required (R)
				- requires a user to take some action before 
				  vulnerability is exploited.
				- e.g. Exploit possible during application 					  install
		- 1.2.e Scope (S)
			+ Technically, scope defines the limits of
			  computing privilege within software to access
			  computer resources (e.g. memory, CPU, HDD)
			+ the ability for a vulnerability in one software
			  component to impact other resources outside of
			  it's own means or privileges.  Scope change.
			+ e.g. a VM vulnerability that enables an attacker
			  to delete files on host OS.
			+ Unchanged (U)
				- Exploited vulnerability affects resources
				  maanged by the same authority.
				- vulnerability component and impacted
				  component are the same.
			+ Changed  ( C )
				- Exploited vulnerability that can affect 
				  beyond authorization privileges 
				- vulnerability component and impacted
				  component are different.
* 1.3 Describe these terms as they are defined in the CVSS 3.0
	+ Impact Metric
		- properties of the impacted components
		- scored according to component that suffers the worst
		  outcome.
		- if no scope change, only the vulnerability component
		  should be used in scoring
		- If scope change, either vulnerability component or impact component should be used in scoring  
	+ 1.3.a Confidentiality 'Impact' ( C )
		- impact to the ability that limits access and
		  disclosure to only authorized users, prevent
		  disclosure.
			+ High (H): total loss of confidentiality.
				- resources of impacted component is
				  open to the attacker.
				- e.g. Administrator's password is exposed or
				  private key to encryption is exposed.
			+ Low (L): some loss of confidentiality.
				- access to some restricted information is
				  obtained. Attacker does not control what
				  information is obtained.
				- e.g. unintentional exposure
			+ None (N): no loss of confidentiality
	+ 1.3.b Integrity 'Impact' (I)
		- impact to integrity if a vulnerability is successfully exploited. Integrity refers to the trustworthiness and veracity of information.
			+ High (H): Total loss of integrity or complete
			  loss of protection.  Attacker modifies
			  "protected" files.
			+ Low (L): Data modification is possible but
			  attacker does not control what or how much can
			  be modified.  No serious impact on target of
			  attack.
			+ None (N): Attack target has no loss of
			  integrity.
	+ 1.3.c Availability (A)
		- Attack Target Availability is impacted when a successful attack happens.  Accessibility
			+ High (H): Total loss of availability.  Attacker
			  is able to fully deny access to target.
			+ Low (L): Reduced availability.  Attacker cannot completely deny service to authorized users.
			+ None (N): No impact to targeted system.
* 1.4 Define these items as they pertain to the Microsoft 
  Windows file system (basic understanding of the functionalities and capabilities of Windows file systems)
	+ Inside view of file systems and how it handles data.
	+ Question:  ```What does a file system do for us?```  
 		- organizes data on a disk--hierarchical  
 		- manage free space on storage device or media.  
 		- format for specifying path to data  
 		- shows how & where to store and retrieve data
		  logically, and update data  
	+ 1.4.a FAT32 (introduced in Windows 95 R2)
		- File Allocation Table - keeps track of allocation
		  status: allocated, unallocated, end of file and bad
		  sector.  
		- 32 bit addressing for disk clusters  
		- 4GB max file size  
		- Volumes up to 2TB  
		- No Encryption and No Compression  
	+ 1.4.b NTFS
	   - creates metadata files: $MFT, $Bitmap, $LogFile and
	     $Boot
	   - encryption and compression
	   - permissions
	   - disk quotas
	   - Recovery
	   - Performance and Reliability
	   - Windows preferred file system
 	+ 1.4.c Alternative data streams
 		- [Alternate Data Stream]
 		- Information can be hidden in ADS  
		- Demo:
```
create ADSDemo.txt with ADS on C:\. 
type: ADSDemo.txt:ADStest
type: echo "Hidden ADS Data" > ADSDemo.txt:ADStest
type: dir (observe the file size)
type: more < ADSDemo.txt:ADStest "Hidden ADS Data"
type: dir /r (lists ADS associated with files)
```
	+ 1.4.d MACE
		- Each file has time stamp for `Create, Modify, Access
		  and Entry Modified`
		- Only in NTFS and tracked. Stored in UTC format.
	+ 1.4.e EFI
		- UEFI based-devices to deploy Windows
		- HDD or SSD must be formated to include Windows
		  partition to use GPT.
		- Windows needs a system partition, this is the `EFI
		  system partition` (ESP) The computer boot to this
		  partition.
		- Size: >100 MB and formated with FAT32
	+ 1.4.f Free space  
	+ 1.4.g Timestamps on a file system 
		- 64 bit value based on 100ns intervals from 12:00a.m. January 1, 1601.
		- NTFS (UTC)
		- FAT (Local Time)
		- File Time stamp is correctly reported when the handle
		  that makes change is closed. 
* 1.5 Define these terms as they pertain to the Linux file 
  system  
	+ 1.5.a EXT4
		- Most current version of the native Linux file systems
		- Backward compatible with previous EXT2 and EXT3.
	+ 1.5.b Journaling  
		- EXT 4, ReiserFS
		- File system that maintains special file to fix inconsistencies that result from improper shutdown.
		- Metadata is written to the journal before data is 
		  written to the HDD.  If System crashes the changes fully committed, no problem. but the ones that haven't  been written to the hard drive need to be identified 
	+ 1.5.c MBR
		- Used by the BIOS to load and start from HDD.
		- Only a single OS can write to MBR during installation
	+ 1.5.d Swap file system
		- Disk space that is resevered to be used as virtual memory.
		- when Linux kernel runs out of memory, kernel moves inactive processes into swap freeing the active memory for active processes.
	+ 1.5.e MAC
		- HFS+
		- Used by OSX and Mac OS
		- compatible with Linux file systems.
* 1.6 Compare and contrast three types of evidence 
	+ 1.6.a Best evidence 
		- Best Evidence Rule: the best evidence offered in court is the original.  Electronic evidence has issues
		- Must turn to the Federal Rules of Evidence Article X, Rule 1001.
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
	+ Must produce image that is exactly the same as original.
	+ Emphasis in forensics are on accuracy and evidence
	  integrity and security.
	+ 1.7.a Altered disk image 
	+ 1.7.b Unaltered disk image 
* 1.8 Describe the role of attribution in an investigation 
	+ it is about assigning blame
		- option 1: look at the evidence and see if we can
		  extrapolate and attribute the result to an 1.8a
		  asset or 1.8b threat actor
		- option 2: at the evidence and try to apply it to the
		  suspect as the 1.8a asset or 1.8b threat actor
	+ the every examination process must not be skipped or
	  overlooked.
	+ must be careful the tools used to determine attribution
	  may not be able to confidently lead to attribution.

[Common Vulnerability Scoring System (CVSS) Online Calculator, version 3.0]: https://tools.cisco.com/security/center/cvssCalculator.x
[Common Vulnerability Scoring System Version 3.0 Calculator]:[https://www.first.org/cvss/calculator/3.0]
[Evil Maid Attack]: https://www.schneier.com/blog/archives/2009/10/evil_maid_attac.html
[Alternate Data Stream]:https://blog.malwarebytes.com/101/2015/07/introduction-to-alternate-data-streams/
