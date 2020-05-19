---
title: Key
nav: true
---

# Create the key variable

------
Now we need to do the same process in  `QPSTrafficCamerasClean`  project data

{% capture text %}
- Go to  `QPSTrafficCamerasClean`  project open in another browser tab
- Perform a  `whitespace`  trim on  `Camera_Street`  and  `Suburb_1`  columns via  
- `Edit cells > Common transforms > Trim leading and trailing whitespace`
- At  `Camera_Street`  column  `>Edit column > Add a new column based on this column`
- Name it  `Camera_Street_Suburb`
- Concatenate (join up) the values from  `Camera_Street_Suburb`  and  `Suburb`  columns
- At the GREL expression input box type the command:  `value + ', ' + cells['Suburb 1'].value` 
- Preview and OK.
{% endcapture %} {% include card.md header="Add a new column with values from two columns" text=text %}

At present there are duplicates in the new  `Column Camera_Street_Suburb`,  probably due to Traffic Cameras being placed in multiple locations on long roads in the same suburb (or maybe other reasons, we don’t know of….) 

We need to deduplicate this key variable in  `QPSTrafficCamerasClean`  so that it contains only unique values to match with the values in the `QLDTrafficAccident_2018` project.  As the researcher of this data you want to identify if there were traffic cameras anywhere on the length of the road in that suburb, so it doesn’t matter if there was more than one possible location.  

To look at an example, let’s filter  `Camera_Street_Suburb`  by the term  `Anzac`.  Kippa-Ring has two cameras listed.

{% capture text %}
- Go to  `Camera_Street_Suburb`  `>Facet>Customized facets>Duplicates facet`
- Click on  `True`  in the facet to see all the duplicate values (how many?)
- Go to `Camera_Street_Suburb`  `>Edit cells>Blank down`
- Note that 69 rows have been blanked down
  (`Blank down`  will detect if two rows following each other have the same content. If they do, the second row will be “blanked out” and the cell values removed.)
-	Go to  `All` column  `>Edit rows>Remove all matching rows`
- 2316 records are remaining and the  `Camera_street_Suburb`  column has unique values. 
- `Filter`  by  `Anzac`  again to test the results.

This is one way to remove duplicates, see this advice from [Illinois University Library](https://guides.library.illinois.edu/openrefine/duplicates) for another.{% endcapture %} {% include card.md header="Remove duplicate rows" text=text %}

Now we can extend the dataset `QLDTrafficAccident_2018`  with a new variable  `Camera_Street_Suburb`  from the `QPSTrafficCamerasClean`  dataset. We will do this using a GREL expression `cell.cross`. The  `cell.cross`  function performs a cross or lookup between two columns in two datasets or the same dataset. It returns an array (list) of zero or more rows in the project i.e. matching against  `QPSTrafficCamerasClean`  for which the cells in their column i.e.  `Camera_Street_Suburb`  have the same content as cell  `Crash_Street_Suburb` . 

{% capture text %}
- Go to  `QLDTrafficAccident_2018`  project
- On  `Crash_Street_Suburb`  `>Edit Column>Add column based on this column>`
- name the new Column  `Camera_Street`
- enter this GREL expression:

     `cell.cross("QPSTrafficCamerasClean","Camera_Street_Suburb")[0].cells["Camera_Street"].value`
  
  - `("QPSTrafficCamerasClean","Camera_Street_Suburb")`  is the data we are looking up and matching.
  -`[0]`  counts from the first value. 
  - `.cells[“Camera_Street”].value`  is a command to add the value from the Camera Street variable to the new column, if there is a match.

- 251 rows have a new variable value added of a camera located in the street.
- Sort the new column  `Camera_Street`  to view the records that have data for this variable.

We could have added the data from the  `Camera_Street_Suburb column`.    If you would like undo and try this instead following the instructions above.

- Close both projects.

More information on  `cell.cross`  function [here](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions#crosscell-c-string-projectname-string-columnname)

More GREL support [here](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Functions) {% endcapture %}{% include card.md header="Match a key variable from two datasets & add a variable using GREL cell.cross" text=text %}


{% include button.md text="Watch video" link="   " color="info" %}

