---
title: Add
nav: true
---

# Add and concatenate another column

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

{% include button.md text="Watch video" link="    " color="info" %}

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

{% capture text %}
{% endcapture %} {% include card.md header="Activity - sort by multiple columns" text=text %}


{% capture text %}
{% endcapture %} {% include card.md header="Activity - find & fix missing values by sorting" text=text %}

{% include button.md text="Watch video" link="   " color="info" %}

----

### Key Points

