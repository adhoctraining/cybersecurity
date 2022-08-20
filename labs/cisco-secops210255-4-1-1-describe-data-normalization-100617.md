File Name:cisco-secops210255-4-1-1-describe-data-normalization-MMDDYY
Show Name:Cisco Cybersecurity Operations
Topic Name: 4.0 Data and Event Analysis
Episode Name:Data Normalization and 5-Tuple
Description:In this episode, Zach and Ronnie discuss the process of data normalization and why we should do it.  They also discuss making data values into universal format for data analysis.  
{Keywords}Data Normalization, Data Values, Universal Format.

---

###Data Normalization

* 4.1 Describe the process of data normalization
	+ "What is the goal of data normalization?"
		- Data normalization is to rid redundant data
		  while keeping data integrity
		- Data should only reside in a single place.
		- Eliminate ambiguous data.
	+ Process is to run data through Data Normalization
		- First Normal Form (1NF)-smallest meaningful unit
		- Second Normal Form (2NF)-all fields dependent on
		  primary key
		- Third Normal Form (3NF)-no data field should be
		  dependent on another field besides the primary key.
* 4.2 Interpret common data values into a universal format
	+ Need both method of interpreting common data values into a universal format and data model.
		- The method provides commonality of where certain data
		  is stored in the same place as same data from another
		  system.
		- The data model provides the structure so that data 
		  can be queried to present the information from
		  multiple events.
	+ Example is SIEM and different data sources:
		- SIEM is essentially the data model
		- each source provides a method that maps their data 
		  to the language and structure of the SIEM.