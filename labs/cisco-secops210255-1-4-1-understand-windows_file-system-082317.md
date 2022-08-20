##Cisco Cybersecurity Operations (210-255)
{FileName}cisco-secops210255-1-4-understand-windows_file-system-MMDDYY
{EpisodeName}Understand Windows File System
{ShowName}Cisco Cybersecurity Operations
{Keywords}Threat analysis, computer forensics, CVSS, Vulnerability Scoring v.3.0, Threat Grid, NTFS, FAT
###Understand windows file systems
* 1.4 Define these items as they pertain to the Microsoft Windows File System
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
	   - large files supported and large partitions
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