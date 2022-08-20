##Cisco Cybersecurity Operations (210-255)
{FileName}cisco-secops210255-1-5-understand_the_linux_file_system-MMDDYY
{EpisodeName}Understand Linux File System
{ShowName}Cisco Cybersecurity Operations
{Keywords}Threat analysis, computer forensics, CVSS, Vulnerability Scoring v.3.0, Threat Grid, NTFS, FAT
###Understand Linux File System
* 1.5 Define these terms as they pertain to the Linux file 
system  
	+ 1.5.a EXT4
		- Most current version of the native Linux file systems
		- Backward compatible with previous EXT2 and EXT3.
	+ 1.5.b Journaling  
		- EXT 3,4, and ReiserFS
		- File system that maintains special file to fix
		  inconsistencies that result from improper shutdown.
		- Metadata is written to the journal before data is 
		  written to the HDD.  If System crashes the changes
		  fully committed, no problem. but the ones that haven't
		  been written to the hard drive need to be identified 
	+ 1.5.c MBR
		- Used by the BIOS to load and start from HDD.
		- Only a single OS can write to MBR during installation
	+ 1.5.d Swap file system
		- Disk space that is reserved to be used as virtual
		  memory.
		- when Linux kernel runs out of memory, kernel moves
		  inactive processes into swap freeing the active memory
		  for active processes.
	+ 1.5.e MAC
		- HFS+
		- Used by OSX and Mac OS
		- compatible with Linux file systems.
* Demo
	+ Use ubuntu and the terminal to show
		- Disk Partition info:
			+ `cd /dev`  describe the `sd` and subsequent parts
			+ the structure is partition table this required to
			  boot ubuntu.
			+ multiple utilities are available for management: 
			  `parted, gparted, fdisk, and gdisk.` 
				- mbr: size limits, max 4 parts, only 1 if
				  corrupted on disk, disk could be unreadable.
				- gpt: newer, no real restriction on size and
				  number of part. GPT is on every partition,
				  not a single point of failure
		- use `sudo parted -l` to show partition information
		- use `cat /etc/fstab` to display details on previously
		  mounted devices
			+ note UUID and details shown