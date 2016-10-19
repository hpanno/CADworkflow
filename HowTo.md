###Purpose and Overview
The Goal with this workflow is to replace the existing road layer in CAD with an updated version. The ECC tracks changes that need to 
be made in CAD in GitHub. We need to apply these edits to the current MasterMapGBD that is in CAD, as well as to the most current
version of the county roads layer. 

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
	- Need to be connected to TRN. It would be helpful to create 2 connections. One connection is to the CAL FIRE Editing Version
	and the other connection is to the Default. The default is only used as reference. 
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
		- Using Beyond Compare, Overwrite the old MasterMapGDB.zip on Old X with the new one you just made (stored locally on
		the 99 Machine.
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
		- Start Editing > Click Reconcile (favor by object; favor the Target Version) > Make edits > Save edits after each edit
		made. 
		- Create a backup of this newest version of the roads layer. Replace the current "ROADS_ALL" features class in
		Y:\\_data\Transportation\TRN_ROADS_ALL.gdb\ROADS_ALL with the newst version that was jsut edited. 
		
		CAL FIRE to CAD
		- In Y:\_data\SLU\SLU_CAD\Mastermap.gdb\Extent delete the current roads that the CAD system is using.
		- Bring in the Y:\_data\SLU\SLU_CAD\SLU_CAD_ROADS_SHELL.gdb\Roads_shell (which has CAD preferred schema) to The viewer
		- Copy and paste the Roads_Shell into the mastermap GDB and rename to ‘roads’
		
		Run the Model
		- Located: Y:\_data\Tools\CAL_FIRE_CAD.tbx\SLOCO_to_SLU_CAD
		- Right click and 'edit' the tool > Validate > Run --> this has just populated the roads features class
		Y:\_data\SLU\SLU_CAD\Mastermap.gdb\Extent
		- Don't save the model when you close out.
		
		Preparing Data
		- Make a zip of the MasterMapGBD to put back on the 99 Machine. Put on Stick. 
		
	Arc Tips:
		- Add imageryGISServer> arcgis on prvgis1> aerials>2014combined
		- Roads with a 4 digit Seg ID are county roads. If you ever have to make an edit to one of these roads let BJC know.
		- Roads can never have a connection through an intersection.
		- For labeling address ranges: [NAME]  & vbnewline & +"LF, LT: " +[L_F_ADD]+"-" +[L_T_ADD]  & vbnewline & +"RF, 
		RT: " +[R_F_ADD]+"-" + [R_T_ADD] 

---
###Pushing Updated Road Data to CAD

	Goal:
		- To push updated road layer to CAD.
	
	1. Putting Updated Road Layer on the 99 Machine
		- Remember, the road data can only be transferred from the Old X to 99. So, replace the mastermap GDB.zip on the old X
		(Data_SLU_SLUCAD) with the mastermap GDB.zip on the stick) via beyond compare
		- Refer to Section 18 in the "_w7" documentation. 
		
		- Open up GUT from Desketop. 
		- Select radio button for "Test". ALWAYS start with Test i.e. ALWAYS tell GUT to push roads to the TEst Environment
		first.
		- Check the file path to ensure you are pushing to the test environemnt.
		- Click "Start Validation"
		
		^^This "Start Validation" process turn the features class into a text file for CAD to read. ^^
		In an error pops up navigate (in Arc) to the file path given. Bring the "Road Errors" layer into the data frame. A text
		file with the errors will automatically pop up explaining the errors. Save this error message to reference later on when
		verifying your edits have been made. Once you have addressed all the errors:
		
		- Save Edits and close ArcMap.
		- Open GUT and re reun "Start Validation" (make sure you are still in TEST). 
		- Once the Validation process is successful right click on roads and select "Convert to geoseg.inp" --> this should be
		the only option you have. Do this for all items listed.
		- Close GUT.
		
		- Open GDI. 
		- On the Conversion Tab> Select "Start"
		^^ This is going to take 2-3 hous.^^
		- When the process has successfully complete click on "Copy files to ADS"
		- On the AVRR Tab Select "Create" then "Load"
		
		TEST your edits. Open the VIEW MAP AVRR TEST application. 
		- For Testing Addresses:
			+ ViewActions> AVRR> Query> Display
		- For Testing Routes:
			+ Mail Icon = locate. Type in an address and select "Center"
			
		Once you've tested the changes you've made and it all looks goovy:
		- Open GUT and select the radio button for "Live". Close out of GUT.
		- Open GDI. In the Conversion Tab select "Copy files to ADS".
		- In the AVRR Tab select "Create" and then "Load" to push the updated layer to Live CAD.
		
		
		
		
		
    
	

