###Purpose and Overview
The Goal with this workflow is to replace the existing road layer in CAD with an updated version. The ECC tracks changes that need to be made in CAD in GitHub. We need to apply these edits to the current MasterMapGBD that is in CAD, as well as to the most current version of the county roads layer. 

---
###Getting Started/Basics
You need to utilize 2 different netowrks and different computers to complete this process. 

	Hardware       |Network         |Purpose                          |
	---------------|----------------|---------------------------------|
	Laptop         | County Network | To access CAD on the 99 machine |
	County Machine | County Network | To make the County Road edits   |
	
####Other Items to know about:
	- Beyond Compare is located: C://>Users>Hpanno>Launch BeyondCompare
		**(C://>Users>Public>PublicDocuments>CALFIRE Vs sftp://root@slugis.duckdns.org//mnt/ds/share_data/SLU/SLU_CAD)**
	- Old X is now the Z://
---
###Logging On to the 99 Machine

	On the Laptop: 
	1.‘Cisco AnyConnect VPN Client’ → UN/PW
	2.‘Remote Desktop Connection’
		- Computer: slucad99
		- UN/PW 

---
###Creating a Backup on the 99 Machine

	1. MasterMapGDB is located:
		- C://>Users>Public>PublicDocuments>CALFIRE
	2. Navigate to the MasterMap.GDB
		- Create a zip file of the MasterMapGDB.
		- Overwrite the old MasterMapGDB.zip on Old X with the new one you just made.
		- Back in Windows Explorer, make a copy of this zipped up GDB and add today's date to one of them. 
		- Click and Drag the MasterMapTODAYSDATE.GDB into the BackUps Folder.
		
---
###Editing the MasterMap.GDB
		
    
    
	

