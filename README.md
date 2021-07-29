
Automated cleanup of ultralibrarian footprints
rough initial working version

To run:
python ./cleanup.py

modify source XML locations in cleanup.py

Ultralibrarian Footprints are downloaded as XML files. The XML file defines the footprint params. To create the actual Allegro footprints, a batch file is run. The batch file opens Allegro, and executes the skill script called "builder.ile". Builder.ile is "obfuscated" skill code, and easily restored to human readable format. Builder.ile parses the xml file and creates the footprints and padstacks, and associates with STEP file if present. Ultralibrarian includes a lot of extra crap in the footprints, which needs to be manually deleted. This is the start of automating the process, by cleaning up the source XML.

The meat of the cleanup is in Footprint_Parser.py. There changes can be made to your liking. Runner is cleanup.py

Script makes thes changes to XML file:
Removes the following layer-
*'DEVICE TYPE/SILKSCREEN_TOP'    
*'DEVICE TYPE/ASSEMBLY_TOP'    
*'USER PART NUMBER/SILKSCREEN_TOP'      
*'COMPONENT VALUE/SILKSCREEN_TOP'    
*'TOLERANCE/SILKSCREEN_TOP'    
*'MANUFACTURING/NO_PROBE_TOP'    
*'PACKAGE KEEPOUT/TOP'    
*'ROUTE KEEPOUT/TOP'   

Replaces the following layer: 'MANUFACTURING/NO_PROBE_TOP' with 'PACKAGE GEOMETRY/DFA_BOUND_TOP'

rewrites the changes to XML file in done/ dir




