Filename: cisco-secops-3-3-1-identify-cybersec-elements-and-frameworks-MMDDYY
Show Name: Cisco CyberSecurity Operations
Topic Name: 3.0 Incidence Response
Episode Name: Identify Cybersec Elements and Frameworks
Description: In this episode, Zach and Ronnie help identify server profiling elements and link data types to 3 of the compliance frameworks: PCI, HIPPA and SOX.  Lastly, they also identify elements that must be protected according to PCI-DSS.
Keywords: SP 800-41,HIPPA, SOX, PCI, PCI Security, Data Incident Response Program, Cisco Web Security, Cisco PCI Solution for Retail

---

### Identify CyberSec Elements and Frameworks
* 3.6 Identify these elements used for server profiling
	+ 3.6.a Listening ports
		- an open port by a running application to allow for inbound connections
		- netstat 
		- unauthorized listening ports indicates intrusion
		- Use `netstat -an`
	+ 3.6.b Logged in users/service accounts
		- `w`, `who`, `whoami`, last
	+ 3.6.c Running processes
	+ 3.6.d Running tasks
	+ 3.6.e Applications
		- `nmap -v`
* 3.7 Map data types to these compliance frameworks
	+ 3.7.a PCI
		- Protects cardhold data wherever it's processed, stored or transmitted.
	+ 3.7.b HIPPA (Health Insurance Portability and
	  Accountability Act)
		- Provides data privacy and security for safeguarding medical inforamtion and ensures patient confidentiality for all health care data.
	+ 3.7.c SOX (Sarbanes-Oxley)
		- Protects shareholders and general public from accounting errors and fraudulent practices and improve the accuracy of corporate disclosures.  Prevent shareholders from being mislead by corporations about their financial status.
* 3.8 Identify data elements that must be protected with regards 
    to a specific standard (PCI‐DSS)
	+ PAN 
	+ Cardholder name
	+ Service Code
	+ Expiration Dates
	+ Card Security Code
	+ PIN