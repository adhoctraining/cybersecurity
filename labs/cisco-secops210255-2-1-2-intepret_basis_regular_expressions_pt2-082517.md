###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-1-intepret_basis_regular_expressions-MMDDYY
{EpisodeName}Interpret Basic Regular Expressions
{ShowName}Cisco Cybersecurity Operations
{Keywords}Regular Expressions, regex
####Interpret Basic Regular Expression
------------------------------------------------------------
* 2.1 Interpret basic regular expressions
	+ What is it?
		- Sequence of characters than defines a search pattern.
		- This can be used with grep, markdown, filters like in
		  wireshark just to name a few examples.
		- Demo:
```
Use Router for basic primer for RegEx.
show run | include ^interface
show ip interface brief | ex un
show ip inteface brief | include un
show run | i ^interface | shutdown
show ip int brief | i 192\.168\.[1-2]\.10
show ip int brief | i 192\.168\.[12]\.10
show run | i ^ip_ (no space after _)
show run | i ^ *ip_  (no space after _)
```
	+ Why should I care and how do I do it?
		- Demo:
``` 
Use Wireshark and filter to show easy way to filter out what is not needed.  What if you need to change add a second string to the filter:
--first filter:  http
--second filter: http and ip.dst\==10.10.100.139
--second filter: http and ip.dst\==10.10.100.139 and ip.src\==69.64.49.212
**The Point** Works if you know exactly what you're 
looking for.
```
	+ When do I need it?
		- Demo:
```
When there is more uncertainty in the search string
show how to find information directly first!
example1 : "ip.src_host matches 173\.194\.113\.1[69][14]" (no quotes)
example2: "and tcp" (no quotes)  to regular expression match.
```