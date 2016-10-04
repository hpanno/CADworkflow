###Purpose and Overview
The Goal with this workflow is to replace the existing road layer in CAD with an updated version. The ECC tracks changes that need to be made in CAD in GitHub. We need to apply these edits to the current MasterMapGBD that is in CAD, as well as to the most current version of the county roads layer. 

---
###Getting Started/Basics
You need to utilize 2 different netowrks and different computers to complete this process. 

	Hardware       |Network         |Purpose                          |
	---------------|----------------|---------------------------------|
	Laptop         | County Network | To access CAD on the 99 machine |
	County Machine | County Network | To make the County Road edits   |
	
#####Other Items to know about:
	- Beyond Compare is located: C://>Users>Hpanno>Launch BeyondCompare
	- Old X is now the Z://
	- Need to be connected to TRN. It would be helpful to create 2 connections. One connection is to the CAL FIRE Editing Version and 		the other connection is to the Default. The default is only used as reference. 
---
###Logging On to the 99 Machine

	On the Laptop: 
	1.‘Cisco AnyConnect VPN Client’ → UN/PW
	2.‘Remote Desktop Connection’
		- Computer: slucad99
		- UN/PW 

---
###Creating a Backup on the 99 Machine and Prepping CAD Road dData for Editing

	Goal:
		- Create a back up of the road data currently being used in CAD in two places:
			+ On Old X
			+ On the 99 Machine
		- Put this data on a stick to be edited on the County Machine.

	1. MasterMapGDB is located:
		- C://>Users>Public>PublicDocuments>CALFIRE
	2. Navigate to the MasterMap.GDB
		- Create a zip file of the MasterMapGDB.
		- Using Beyond Compare, Overwrite the old MasterMapGDB.zip on Old X with the new one you just made (stored locally on the 			99 Machine.
			+ **(C://>Users>Public>PublicDocuments>CALFIRE Vs sftp://root@slugis.duckdns.org//mnt/ds/share_data/SLU/SLU_CAD)**
		- Back in Windows Explorer, make a copy of this zipped up GDB and add today's date to the copy. 
		- Click and Drag the MasterMapTODAYSDATE.GDB into the BackUps Folder.
		- Put the other zipped up version of the GDB (the one without the date) on a thumbdrive.
		
---
###Editing the MasterMap.GDB

	Goal:
		- Refernce GitHub to makes edits to the MasterMap.GDB we just pulled from the 99 machine. 
		- Incorporate the most recent version of the county roads to our edits.
		- Push all of the edits back to the county.
		- Run a model to convert this updated roads layer to reformat it to a schema CAD understands.
    
    	1. GitHub
		- Refer to CAD issues on GitHub to see issues being tracked by the ECC.
	2. In Arc
		- Pull in your version of the Roads layer from TRN.
		- Start Editing > Click Reconcile (favor by object; favor the Target Version) > Make edits > Save edits after each edit 		made. 
		- Create a backup of this newest version of the roads layer > Export to Y://_data>Transportation.
		
		CAL FIRE to CAD
		- In Y:\_data\SLU\SLU_CAD\Mastermap.gdb\Extent delete the current roads that the CAD system is using.
		- Bring in the Y:\_data\SLU\SLU_CAD\SLU_CAD_ROADS_SHELL.gdb\Roads_shell (which has CAD preferred schema) to The viewer
		- Copy and paste the Roads_Shell into the mastermap GDB and rename to ‘roads’
		
		Run the Model
		- Located: Y:\_data\Tools\CAL_FIRE_CAD.tbx\SLOCO_to_SLU_CAD
		- Right click and 'edit' the tool > Validate > Run --> this has just populated the roads features class
		Y:\_data\SLU\SLU_CAD\Mastermap.gdb\Extent
		
		Preparing Data
		- Make a zip of the MasterMapGBD to put back on the 99 Machine. Put on Stick. 
		
	Arc Tips:
		- Add imageryGISServer> arcgis on prvgis1> aerials>2014combined
		- Roads with a 4 digit Seg ID are county roads. If you ever have to make an edit to one of these roads let BJC know.
		- Roads can never have a connection through an intersection.

---
###Pushing Updated Road Data to CAD

	Goal:
		-
	1. 
		-
    
	

