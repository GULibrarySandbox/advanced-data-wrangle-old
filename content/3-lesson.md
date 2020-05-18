---
title: Add
nav: true
---
# Add a new variable to enhance the data

--------

### 

We want to enhance this dataset by adding a new variable, to explore if traffic cameras are located in any of the same streets as accidents in 2018.  We can do this by using the  `qpsactive_parkedmscamera.csv`  dataset.

We need to identify a common value in each of the datasets that we can match on.  A key variable.  To do this we need to explore both datasets to see if a key or very similar variable is available that we can work with. 

Lets open up another instance of OpenRefine to do this.  

{% capture alert %} Note: The `qpsactive_parkedmscamera.csv`  dataset didn’t provide geolocation, lat or long, as the traffic camera sites are mobile and can move from one end of a road to another, so we cannot match on this.  The dataset also needed a bit of cleaning to get it to a format to use. Some `suburb name` observations contained multiple values such as `Brisbane/Spring Hill`, perhaps to indicate the street location was on the border of two suburbs.  In these cases, for the purpose of the training, the values have been modified to the first suburb listed so that there is only one value in a cell.{% endcapture %}
{% include alert.md text=alert color="warning" %}

{% capture text %}
- Add the url  `http://127.0.0.1:3333/`  to a new tab in your browser.  
- Create a new project using  `QPSTrafficCamerasClean.csv`  dataset
- Name it  `QPSTrafficCamerasClean`
- Look at both datasets, what variables do they have in common?
  - `Camera_Street`  and  `Suburb_1`  in  `QPSTrafficCamerasClean`
  - `Crash_Street`  and `Suburb`  columns in  `QLDTrafficAccident_2018`{% endcapture %} 
{% include card.md header="Find a key variable" text=text %}


In this next activity you want to limit to a sub-set of this data, with records about *crashes* which resulted in *fatalities* or *hospitalisation*.
{% capture text %}
- Scroll to  `Crash_Severity`  Column.
- Click the down arrow and choose  `Facet > Text facet`. Unique values will be displayed in left hand panel.
- Click on the choices in the facet, or hover over them,  `edit`  and  `include`  functions appear.
- Hover over values  `Fatal and Hospitalisation`  and use  `include`  function to narrow results just to those records.
- Check how many records display? Answer should be 27528.
- Now use  `Exclude`  to return to all records.
- Use  `include`  function again for values  `Medical treatment and Minor injury`  (with 35002 results).
- Remove all these records from the dataset.
- Select  `All column > Edit rows > Remove all matching rows`.
- These two variables are now displayed in red and missing counts. Click reset.
- How many records are now available? (27528)
- Close the facet.{% endcapture %} {% include card.md header="Activity - amending data through Facets" text=text %}

You can also edit values using the facets feature. 
{% capture text %}
- Use faceting to look at the  `Crash_Day_of_Week`  Column.
- What are the results? Do you see different representations of the same value?
- Hover over  `MON SUN & SAT`  and choose  `Edit cells`  to alter the abbreviated values to full words.
- Do you now have seven values for the days of the week? 
- Close facet{% endcapture %} {% include card.md header="Activity – fixing errors with Facets" text=text %}

{% include button.md text="watch this video to work through the activities" link="https://vimeo.com/412540178/a0a65e0c0f" color="info" %}

----

#### More on Facets

As well as 'Text facets' and 'timeline facets', OpenRefine also supports other types of facet. These include:

- Numeric facets
- Customized facets
- Scatterplot facets

`Numeric`  and `Scatterplot`  facets display graphs instead of lists of values. The numeric facet graph includes 'drag and drop' controls you can use to set a start and end range to filter the data displayed. These facets are explored further in Examining Numbers in OpenRefine.

`Custom`  facets provide a range of different facets including:

- `Word`  facet - this breaks down text into words and counts the number of records each word appears in
- `Duplicates`  facet - this results in a binary facet of 'true' or 'false'. Rows appear in the 'tru' facet if the value in the selected column is an exact match for a value in the same column in another row.
- `Text length`  facet - creates a numeric facet based on the length (number of characters) of the text in each row for the selected column. This can be useful for spotting incorrect or unusual data in a field where specific lengths are expected (e.g., if the values are expected to be years, any row with a text length of more than 4 for that column is likely to be incorrect.)
- `Facet by blank`  - a binary facet of 'true' or 'false'. Rows appear in the 'true' facet if they have no data present in that column. This is useful when looking for missing data.

{% capture text %}
Use a  `Custom facet`  to find out how many records are missing crash type data.
{% include modal.md button="Quiz 1 Solution" color="success" title="Quiz 1 Solutions" text="Select  `Facet > Customized facets > Facet by Blank or Null`. 
Result 13" %}{% endcapture %} {% include card.md header="Quiz 1. What data is missing in  `Crash_Type`  column?" text=text %}

--------

### Common Transformations

Words with spaces at the beginning or end are particularly hard for we humans to tell from strings, but the blank characters will make a difference to the computer. We usually want to remove these at the beginning of a project.  OpenRefine provides a tool to remove blank characters from the beginning and end of any entries that have them.

{% capture text %}
- Create a new text facet for the column  `Local_Police_Region`. You should see some choices that appear identical (Central and South Eastern have two choices). One of these choices must include either leading or trailing whitespace.
- To remove the whitespace, choose  `Edit cells > Common transforms > Trim leading and trailing whitespace`.
- There should now be five choices in your text facet.

Other common transformations include changing letter case, data formats and more.  

Take a look at the other options with  `Edit cells > Common transforms >` .{% endcapture %} {% include card.md header="Activity – remove whitespace with common transformation" text=text %}

--------

### Clustering

Another very useful feature of OpenRefine is Clustering.  In OpenRefine, clustering means 'finding groups of different values that might be alternative representations of the same thing'. For example, the text strings 'New York', 'new york'  or 'New Yrok' very likely refer to the same concept.

Clustering is a very powerful tool for identifying and fixing datasets which contain misspelled or mistyped entries.

OpenRefine has several clustering algorithms built in. Let's experiment with them.
{% capture text %}
- Create a Text Facet for  `Crash_Nature`, scroll through the list.  You will notice a number of values that are likely mis-typed entries due to various factors.
- Click the  `Cluster`  button, on the top right of the facet. In the resulting pop-up window, different edit options and algorithms are available via drop down boxes.
- Select the  `key collision`  method and  `fingerprint`  keying function. It should identify one cluster with 3 value options.
- Click the  `Merge?`  box beside the cluster, then click  `Merge Selected and Re-cluster`  to apply the corrections to the dataset.
- Try selecting different Methods and Keying Functions combinations, to see if new merges are suggested.
- There may be a few more clusters, to fix misspellings, typos, capitalisation, hyphens, etc.
- How many choices are now shown in the facet? Depending on your merges, there may be 13 choices remaining.
- Close the facet.{% endcapture %} {% include card.md header="Activity – fixing errors via Clustering" text=text %}
{% capture alert %}*Note:* Some merges are not necessary. Nearest neighbour with a radius of 2.0 with find *Struck by external load* with *Struck by internal load*.  These are valid values, there is no need to merge these.
{% endcapture %}
{% include alert.md text=alert color="warning" %}

{% include button.md text="Watch video" link="https://vimeo.com/412536655/cfbb96bb38" color="info" %}

----

### Different clustering algorithms

Detailed information on the different clustering algorithms and combinations is available here: [https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth](https://github.com/OpenRefine/OpenRefine/wiki/Clustering-In-Depth).
