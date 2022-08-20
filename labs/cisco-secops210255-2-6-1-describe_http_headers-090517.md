###Cisco Cybersecurity Operations (Exam 210-255)
============================================================
{FileName}cisco-secops210255-2-6-describe_http_headers-MMDDYY
{EpisodeName}Describe HTTP Headers
{ShowName}Cisco Cybersecurity Operations
{Keywords}Cisco FMC, Wireshark, Cisco IOS Netflow
#### Describe HTTP Headers
------------------------------------------------------------
* 2.2.g HTTP
	+ HTTP Basics Review:
		- Header information is controlled by the client user, this makes it easy for an attacker to manipulate 
		- HTTP users headers to communicate between client and 
		  server. (create, use and end client and server
		  connection)
		- GET--retrieves resource from web server
		- POST--performs actions and sends data into body of the
		  message. 
		- Method, user-agent and cookie are fields that
		  vulnerable to attacks.
		- input based attacks
		- + Attackers can launch attacks by adding
	       **executable** Code within HTTP header (Firewalls do
		  not check content)
	+ HTTP Methods:
		- Not every server uses every method
		- GET: requests a resource from web server
			+ vulnerability--passes parameters through URL 
			  and easy to manipulate
		- POST: sends data to the webserver (e.g. filling out a
		  form)
		- HEAD: works like GET requests returns only
		  headers in response.
		- PUT: sends replacement document 
			+ used to send any kind of malicious data to server
		- DELETE: when client is trying to delete document from
		  Web Server
			+ can remove any resource from web server
			+ delete configuration files.
		- TRACE: client is requesting that servers inbetween
		  announce themselves to the client.
		- OPTIONS: used to determine what other methods are
		  available to retrieve documents on web server
			+  Attacker gains inforamtion about methods that
			   can be used for attack.
		- CONNECT: creates HTTP tunnel for requests.
			+ Attacker can use this to connect through a proxy
			  to gain access to unrestricted resources.
		- content-type
			+ browsers do content-sniffing.  This mechanism can
			  be manipulated by attackers to trigger XSS
			  attacks.
		- user agent: The client sends information about the
		  browser, host OS and language.
			+ can be spoofed by an attacker to retrieve content
			  meant for a different browser or even certain
			  type of devices.
			+ modify firefox:
```
				- about:config, accept the risk
				- search `useragent`
				- right click: `general.useragent.override`
				- Mozilla/5.0 (compatible; Googlebot/2.1;
				 +http://www.google.com/bot.html)
```
		- referer field: something in it (RFC 2616)
			+ privacy issue if data is in this field.
			+ can reveal to a site the last site that was
			  visited.
			+ if a site has bad coding
				- session tokens
				- username/password
				- additional input as part of URL
	+ Cookies:
		- Enable Webserver to send data to client that the
		  client will store to resubmit to browser. e.g. ITProTV
		- mostly used to identify user and remember the session
		  state
		- Cookie Components:
			+ Cookie header line in HTTP Response
			+ Cookie header line in HTTP Request
			+ Cookie kept on client and managed by browser
			+ Database at Website
	+ Double Encoding:
		- Common character used in web application attacks:
			+ "../" Directory Traversal
			+ "<", "/", and ">" XSS 
			+ etc.
			+ refer to Simple Diagram
		- Recognition is key