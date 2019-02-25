This is a documentation of issues that I've come across while completing a CAD push and the fixes.


Received "WARNING 000405: No records within table"

Only 30 of the 40470 records transfer over from ROADS_ALL to Roads. 

Description of WARNING 000405: No records within table:
There were no records available in the table on which to perform the operation. This warning can occur, obviously, when using an empty feature class or table, but it may also occur when working with a layer or table view containing an empty selection set. If a selection was applied against the layer or table view (for example, Select Layer By Location, Select Layer By Attribute) and it resulted in no records being selected, this warning will occur.

Solution
Use Get Count to return the number of available records or features within the input dataset. If the input is a layer or table view and there is a selection, it will return the number of selected records or features. Reexamine the query used to create the selection to ensure it is correct.
