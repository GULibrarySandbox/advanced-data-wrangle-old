---
title: Find
nav: true
---
# Find a suitable variable

--------

The aim of this lesson is to enhance the  `TrafficAccident_2018` project data by adding a new variable, to explore if traffic cameras are located in any of the same streets as accidents in 2018.  The  `QPSTrafficCamerasClean.csv`  dataset contains street locations of cameras, so could be a good match.

We need to identify a common value in each of the datasets that we can match on.  A key variable.  To do this we need to explore both datasets to see if a key or very similar variable is available that we can work with. 

{% capture alert %} Note: The `QPSTrafficCamerasClean.csv`  dataset doesn’t provide geolocation, latitude (lat) or longitude (long) points. This maybe because the traffic camera sites are mobile and can move from one end of a road to another.  It is therefore not possible to match on lat or long.  

The original open dataset required cleaning to transform it to a useable format. Some `suburb name` observations contained multiple values such as `Brisbane/Spring Hill`, perhaps to indicate the street location was on the border of two suburbs.  

In these cases, for the purpose of the training, the values have been modified to the first suburb listed so that there is only one value in a cell.{% endcapture %}
{% include alert.md text=alert color="success" %}

Let's open another instance of OpenRefine to explore the  `QPSTrafficCamerasClean.csv` dataset.  

{% capture text %}
- Add the url  `http://127.0.0.1:3333/`  to a new tab in your browser.  
- Create a new project using  `QPSTrafficCamerasClean.csv`  dataset
- Name it  `QPSTrafficCamerasClean`
- Look at both datasets, what variables do they have in common?
  - `Camera_Street`  and  `Suburb_1`  in  `QPSTrafficCamerasClean`
  - `Crash_Street`  and `Suburb`  columns in  `QLDTrafficAccident_2018`
 
These could be used as a key to match on.  A key is a unique, matching value in one column from each dataset.  However, we cannot match on one of these columns alone as the values within are not unique, eg. there are common street names in multiple suburbs. To check this:

- Go to `Camera_Street > Facet > Text Facet`{% endcapture %} 
{% include card.md header="Find a key variable" text=text %}

One solution to the problem above is to match on a combination of values in both columns.  This is when it becomes useful to combine information from multiple columns (variables) into one column using a process called *concatenation*. 

This method allows you to combine the contents of two columns, and add a specific string to a column’s values, such as a common separator.

Before we can concatenate each of the two columns we need to undertake a few cleaning steps with each dataset.

Let’s work on each dataset one at a time.  Working with  `QLDTrafficAccident_2018` first.

{% capture text %}
- Go to `QLDTrafficAccident_2018` project
- Perform a `whitespace trim`  on  *both* `Crash_Street`  and  `Suburb`  columns via `Edit cells > Common transforms > Trim leading and trailing whitespace`.
- Go to  `Suburb`  column  `>Edit Column>Move Column Left`
- Repeat this step until the  `Suburb`  column is next to  `Crash_Street`

It is important when amending or enhancing data to retain values until you are satisfied that transformations have worked accurately. So we will duplicate one column from each dataset and work with it. 

- At  `Crash_Street`  column  `>Edit column > Add a new column based on this column`
- name it  `Crash_Street_Suburb`

Let’s concatenate the values from `Crash_Street_Suburb`  and `Suburb`  columns.

- At the GREL expression input box type the command:  
  `value + ', ' + cells['Suburb'].value` 
  - `value`  indicates the values in the current column.
  - `cells[‘Suburb’].value`  indicates to add cell values from the ‘named’ column you would like to combine with.
  - ` + ‘, ’  + ` adds an additional string in the results, in this case a common separator with white space `, `
  - Note: we can use either  `“`  or  `‘` in a GREL expression to wrap around a string of text.
- Preview and OK.{% endcapture %} 
{% include card.md header="Add a new column with values from two columns " text=text %}

The image below shows the GREL expression in action. 

{% include figure.html img="AdvGREL.jpg" alt="Add a column with values from two columns using GREL" caption="Advanced GREL" width="100%" %}

{% include button.md text="watch this video to work through the activities" link="    " color="info" %}

----

