##Cisco Cybersecurity Operations (210-255)
{FileName}cisco-secops210255-1-1-read_security_analysis_reports-MMDDYY
{EpisodeName}Read Security Analysis Reports
{ShowName}Cisco Cybersecurity Operations
{Keywords}Threat analysis, computer forensics, CVSS, Vulnerability Scoring v.3.0, Threat Grid, NTFS, FAT
###1.1 Read Security Analysis Reports 
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
			+ In a readable format
		- Demo:  
```
Cuckoo Sandbox Website
```
	+ Online Sandbox
		- Demo:
```
https://www.hybrid-analysis.com
have questionable file ready to uploaded
view results
similar results to what you would see in Cuckoo.
```