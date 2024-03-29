Open the command prompt and enter systeminfo.exe > c:\Desktop\systeminfo.txt. 
<p>

Things to look at regarding a slow computer:
- Remove unsused software and bloatware
- Look at startup programs. Use the task manager. Turn off re-boot and re-start one at a time
- Check out flle fragmentation.
- System Cleaning and hygeine:
  - WinDirStat
  - A file that you may want to remove is hybefile.sys. Don't just re,ove it. It is the hibernation file. You can turn off hibernation with the powercfg.exe  hibernate /off 
  - Scan for malicious software.
  - search %appdata% and review for indicators of compromise
  - Run Microsoft Defender
- System file repair
  - run chkdsk to scan for errors
  - run sfc /scannow (system file scanner)
<br>
ref: [Dave's Garage](https://www.youtube.com/watch?v=Bwh6cVJHKSo)
<br>
Clear up temp and cache:

- create a restore point
- search %temp% to find temp files and delete
- go to the Windows folder and find /software distribution/download and delete the info. This is leftover files from software that is installed.
- clear file history
- run prefetch - delete them all
- run as administrator the command prompt:
  - type WSreset.exe to reset the Windows store (Windows 10)
  - type ipconfig /flushdns
- run disk clean up
- open system control panel, goto storage and make sure storage sense is on and check the configuration
<br>
referenence: [Liron Segev](https://www.youtube.com/watch?v=U4132uo1oXc)
<p>
Go to:

- https://christitus.com/clean-up-windows-10/ and run the debloat script
- bmrf.org/repos/tron/

<br>
reference: [Clean Up Windows 10 3 Steps For A Faster Computer](https://www.youtube.com/watch?v=mWHiP9K8fQ0)

