---
title: Key
nav: true
---

# Create the new variable

------
The concatenation (join up) process is now required for  `QPSTrafficCamerasClean`  project data.

{% capture text %}
- Go to  `QPSTrafficCamerasClean`  project, open in another browser tab
- At  `Camera_Street`  column  `>Edit column > Add a new column based on this column`
- Name it  `Camera_Street_Suburb`
- Join up the values from  `Camera_Street_Suburb`  and  `Suburb`  columns
- At the GREL expression input box type the command:
  `value + ', ' + cells['Suburb 1'].value` 
- Preview and OK.
{% endcapture %} {% include card.md header="Add a new column with values from two columns" text=text %}

At present there are duplicates in the new  `Column Camera_Street_Suburb`,  probably due to traffic cameras being placed in multiple locations on long roads in the same suburb (or maybe other reasons, we don’t know of….).

We need to deduplicate this key variable in  `QPSTrafficCamerasClean`  so that it contains only unique values to match with the values in the `QLDTrafficAccident_2018` project.  In the analysis we want to identify if there were traffic cameras anywhere on the length of specific roads in specific suburbs, so it doesn’t matter if there was more than one possible location on the road.  

To look at an example, filter  `Camera_Street_Suburb`  by the term  `Anzac`.  The suburb Kippa-Ring has two cameras listed in Anzac Avenue.

{% capture text %}
- Go to  `Camera_Street_Suburb`  `> Facet > Customized facets > Duplicates facet`
- Click on  `True`  in the facet to see all the duplicate values (how many?)
- Go to `Camera_Street_Suburb`  `> Edit cells > Blank down`
- Note that 69 rows have been blanked down
  (`Blank down`  will detect if two rows following each other have the same content. If they do, the second row will be “blanked out” and the cell values removed.)
-	Go to  `All` column  `> Edit rows>Remove all matching rows`
- 2316 records are remaining and the  `Camera_street_Suburb`  column has unique values. 
- `Filter`  by  `Anzac`  again to test the results.

This is one way to remove duplicates, see this advice from [Illinois University Library](https://guides.library.illinois.edu/openrefine/duplicates) for another.{% endcapture %} {% include card.md header="Remove duplicate rows" text=text %}

{% include button.md text="Watch the steps above on this video" link="https://vimeo.com/422326756/622764409f" color="info" %}

------

Now we can extend the dataset `QLDTrafficAccident_2018`  with a new variable  `Camera_Street_Suburb`  from the `QPSTrafficCamerasClean`  dataset. We will do this using a GREL expression `cell.cross`. The  `cell.cross`  function performs a cross or lookup between two columns in two datasets or the same dataset. It returns an array (list) of zero or more rows in the project i.e. matching against  `QPSTrafficCamerasClean`  for which the cells in their column i.e.  `Camera_Street_Suburb`  have the same content as cell  `Crash_Street_Suburb` . 

{% capture text %}
- Go to  `QLDTrafficAccident_2018`  project
- On  `Crash_Street_Suburb`  `> Edit Column> Add column based on this column>`
- name the new Column  `Camera_Street`
- enter this GREL expression:

     `cell.cross("QPSTrafficCamerasClean","Camera_Street_Suburb")[0].cells["Camera_Street"].value`
  
  - `("QPSTrafficCamerasClean","Camera_Street_Suburb")`  is the data we are looking up and matching. 
  - `[0]`  counts from the first value. 
  - `.cells[“Camera_Street”].value`  is a command to add the value from the Camera Street variable to the new column, if there is a match.

- 251 rows of traffic accident observations now have a new variable & value added of a camera located in the same street.
- `Sort`  the new column  `Camera_Street`  to view the records that have data for this new variable.

**Extra**
Let's now change the results of the cell.cross results from the name of the Camera_Street value to a boolean value of "Yes".
- Select the new column, in this case, `Camera_Street` and `Edit Cells > Transform >`
- GREL Expression:

    `if(value.contains(/./),"yes",value)`
  - This means if the value contains `(/./)` (any character found in the cell), replace it with `Yes` value.
- `Sort` `Camera_Street` again to view changes to the records.
- Close both projects.

We could have added the data from the  `Camera_Street_Suburb column` using the same steps above.{% endcapture %}{% include card.md header="Match a key variable from two datasets & add a variable using GREL cell.cross" text=text %}

The image below shows the GREL cell.cross expression in action. 
 
{% include figure.html img="ORCellCross.JPG" alt="Add a column matching with a key id using GREL cell.cross" caption="Add a column matching with a key id using GREL cell.cross" width="100%" %}

Find more information on the  `cell.cross`  function [here](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions#crosscell-c-string-projectname-string-columnname) and more GREL functions [here](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Functions).


{% include button.md text="Watch the GREL cell.cross activity on this video" link="https://vimeo.com/422324961/6cc1733109" color="info" %}

----

<p align="center">
  <a href="https://griffithunilibrary.github.io/Advanced-data-wrangle/content/3-lesson.html"><-- BACK</a> |
  <a href="https://griffithunilibrary.github.io/Advanced-data-wrangle/content/5-lesson.html">NEXT --></a>
</p>
