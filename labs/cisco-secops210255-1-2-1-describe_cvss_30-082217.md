##Cisco Cybersecurity Operations (210-255)
{FileName}cisco-secops210255-1-2-describe_cvss-MMDDYY
{EpisodeName} Describe CVSS 3.0 
{ShowName}Cisco Cybersecurity Operations
{Keywords}Threat analysis, computer forensics, CVSS, Vulnerability Scoring v.3.0, Threat Grid, NTFS, FAT
###1.2. Describe CVSS 3.0 Terminology
* 1.2 Describe these terms as they are defined in the CVSS 3.0
	+ Question:
```
What is the CVSS 3.0 and why is it important?
```  
	+ CVSS (Common Vulnerability Scoring System)
		- Cisco [Common Vulnerability Scoring System (CVSS) Online Calculator, version 3.0]
		- First.org [Common Vulnerability Scoring System Version 3.0 Calculator]
		- 
	+ The follow terms are all **base metrics** used to 
	  generate a score. Score between 0 and 10.
	+ Textual Severity Reatings: None ()), Low(0.1-3.9), Medium(4.0-6.9), High (7.0 - 8.9) and Critical (9 - 10)
	+ Additional Metrics (UI and PR--privilege required, and scope)
	+ CIA metrics updated to have scored of (None, Low or High)
		- Two areas contribute toward the base metric score:
			+ Exploitability Metric
			+ Impact Metric
	+ Exploitability Metrics (reflect characteristics of the target that is vulnerable--vulnerability component. These components should show characteristics of what leads to a successful attack and rarely changes if ever.)
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

[Common Vulnerability Scoring System (CVSS) Online Calculator, version 3.0]: https://tools.cisco.com/security/center/cvssCalculator.x
[Common Vulnerability Scoring System Version 3.0 Calculator]:[https://www.first.org/cvss/calculator/3.0]