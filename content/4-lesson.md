---
title: Facets
nav: true
---
# Facets & Clustering 

--------

### Facets
Faceting is a useful feature of OpenRefine and can help you:
- get an overview of the data in a project
- get counts of data in specific columns
- help you identify missing, misspelled or inconsistent data.

A common use case for your data might be where you want to know how many times a particular value appears in a column in your data.

A 'Facet' groups all the like values that appear in a column, and then allows you to filter the data by these values 
and edit the values for a number of records in one go.

The first facet to explore is  `Text facet`. It groups all the identical text values in a column and lists each value 
and the number of records in which that value appears. Facet information always appears in the left-hand panel 
in the OpenRefine interface.


{% capture text %}
Here we will use faceting to look at the values represented in the  `Crash_Month` column.

- Scroll over to the  `Crash_Month` column.
- Click the down arrow and choose  `Facet > Text facet`.

In the left panel, you will now see a box containing every unique value in the `Crash_Month` column,
along with a number representing how many times that value occurs in the column.  At the top of the box you can sort the results by name and count. A great feature for exploring a large dataset.

- Try sorting this facet by name and by count. How are they sorted? Name is alphabetical and count is largest first.
- Which months have the highest and lowest traffic related accidents? May is the highest, January the lowest.
- Close facet by clicking the  `x`  in top corner of the Facet panel.{% endcapture %} {% include card.md header="Activity – Looking at data through Facets" text=text %}


{% capture alert %}*Note:* Always close facets when you are finished with them, so as not to affect future facets or results.
{% endcapture %}
{% include alert.md text=alert color="warning" %}

You can also amend data with Facets.

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
