---
title: Resources
nav: true
---
# Resources & alternative methods
----

#### References

Little, John (2018). Cleaning data with OpenRefine. [https://libjohn.github.io/openrefine/demonstration.html](https://libjohn.github.io/openrefine/index.html)

Dougherty, Jack (2017). Hands-On data visualization: interactive storytelling from spreadsheets to code, [https://handsondataviz.org/index.html](https://handsondataviz.org/index.html)

Williamson, Evan (2017). Fetching and parsing data from the Web with OpenRefine, The Programming Historian (6), [https://programminghistorian.org/en/lessons/fetch-and-parse-data-with-openrefine](https://programminghistorian.org/en/lessons/fetch-and-parse-data-with-openrefine)

University of Illinois Library (2020). OpenRefine guide. [https://guides.library.illinois.edu/openrefine/](https://guides.library.illinois.edu/openrefine/)

----

#### Aternative methods for splitting multi-value cells 

Activity 10 (alternative): Splitting multi-value cells by value
To split the values in Site features across multiple columns we need to standardise the content with the following steps. 
8.	Go to Site features column
9.	Identify missing values with Facet> Customised Facet > Facet by blank
10.	It appears that the original spreadsheet has hard returns inside the cells, lets remove these via Edit Cells> Common Transform  > Collapse consecutive whitespace 
Now we want to perform a facet by splitting the values and if the values are controlled and you know what all the options are you could use this method.
Activity 11 (alternative) : Add a new column based on split values
7.	Go to column  Site features > Edit column> add column based on this column
8.	type new column name Universal access toilet
9.	Click inside expression box, enter GREL expression:
if(value.contains("Universal access toilet"),"Yes",value).replace(/.*[^Yes].*/,"") 
10.	Preview and ok
11.	repeat steps above for each of the items owned (can reuse expression from history tab)

----


