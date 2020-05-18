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

{% include button.md text="Watch video" link="    " color="info" %}

------

### Sorting data

Using `Crash_Street`, let's explore data using sorting.

{% capture text %}
- in  `Crash_Street`  column select drop-down menu and  `Sort`.   Options include:
  - sort by text
  - sort by numbers
  - sort by dates
  - sort by booleans (TRUE or FALSE values). 
- select  `text`
- additional options will then appear for you to fine-tune your sorting, select  `a-z`
- you can also specify what order to put *blanks* and *errors* in the sorted results.
-  `Ok`

When performing the first sort, you will notice the drop-down menu for the selected column shows  `Sort ...` 

If you try to re-sort a column that you have already used, the drop-down menu changes slightly, to  `> Sort`  without the  `...`, to remind you that you have already used this column. Additional options include:

  - `Sort > Sort ...` - This option enables you to modify your original sort.
  - `Sort > Reverse` - This option allows you to reverse the order of the sort.
  - `Sort > Remove sort` - This option allows you to undo your sort.
- remove this sort.{% endcapture %} {% include card.md header="Activity - sort by text" text=text %}



{% capture text %}
{% endcapture %} {% include card.md header="Activity - sort by multiple columns" text=text %}


{% capture text %}
{% endcapture %} {% include card.md header="Activity - find & fix missing values by sorting" text=text %}

{% include button.md text="Watch video" link="   " color="info" %}

----

### Key Points

