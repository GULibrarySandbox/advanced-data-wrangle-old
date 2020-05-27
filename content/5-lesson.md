---
title: Tidy
nav: true
---

# Tidy data - a revisit 

-----

The  `QLDDriverReviverStations.csv` dataset lists *Driver Reviver* rest-stop locations and facilities available across Queensland. We are going to create an interactive map of this data, using geo.json.  However the geo.json tool cannot parse the data yet as it not tidy.

To create a [tidy](https://cran.r-project.org/web/packages/tidyr/vignettes/tidy-data.html) dataset, where:
- Each variable forms a column
- Each observation forms a row
- Each type of observational unit forms a table,

multi-value cells need to be split by the value.  

This task is helpful where there are multiple values in a cell that are not organised consistently, such as when survey respondents can select multiple, controlled values to answer a question.  The  `Site features`  column in the dataset `QLDDriverReviverStations.csv`  is an example of this. 

{% capture text %}
- Create a new project with dataset  `QLDDriverReviverStations.csv`  in OpenRefine
- Name project  `QLDDriverReviverStationsClean` 
- Go to  `Site features`  column `Facet > Text Facet >` to see multiple values in a messy state.

Let's first check if any rows have missing values.
- Go to  `Site features`  column
- `Facet> Customised Facet > Facet by blank`

There are no missing values.
{% endcapture %} {% include card.md header="Create project" text=text %}

There are a couple of ways to create new columns and move the values to these. The first method requires some cleaning of the data, followed by a GREL command `value.split` with a common separator. 

{% capture text %}
It appears the original spreadsheet has *hard* returns inside the cells. Remove these with:

- `Edit Cells> Common Transform  > Collapse consecutive whitespace` 

We want to perform a facet by splitting the value, using a common separator.  These values are separated by an asterix * which can be used.  It won't work yet as it has whitespaces around some of the instances. Let's remove these.

- `Edit Cells > Transform`  and 
- GREL expression:  `value.replace("* ","*").replace(" *","*")`{% endcapture %} {% include card.md header="Tidy the 'Site features' column" text=text %}

The next step is to split the values so they can be moved to separate columns. 

{% capture text %}
- `Facet > Custom text facet > using value.split(“*”)`  to see all value results.
- These include  `play area`,  `table`,  `universal access toilet`  and  `water`.
- Click on first Facet result  `Play area` , with 11 results
- Go to column  `Site features > Edit column> add column based on this column`
- Type new column name  `Play area`
- Click inside expression box, delete  `value`  and type `"Yes"`
- Preview and ok
- Repeat steps above for each of the items owned (can reuse GREL expression from  `history`  tab){% endcapture %} {% include card.md header="Add a new column based on split values" text=text %}

The image below shows the creation of the  `Play area`  column using the method described above.

{% include figure.html img="ORFacetSplit.JPG" alt="Custom Facet plus add a column" caption="Facet by GREL value.split & Add a column" width="100%" %}

{% include button.md text="Watch the steps above on this video" link="" color="info" %}


Below is an alternative method using GREL and a language known as Regular Expression or Regex, which searches for patterns in strings.  

{% capture text %}
- `Undo`  your steps back to Step `0. Create Project` to try this method.- 
- Go to column  `Site features` > `Edit column> add column based on this column`
- Type new column name  `Universal access toilet`
- Click inside expression box, enter GREL expression:
    
    `if(value.contains("Universal access toilet"),"Yes",value).replace(/.*[^Yes].*/,"")`
    
    This means...
    if (the value in the cell contains "Universal access toilet", replace it with "Yes" value), then replace (anything that is not "Yes" that is found one or more times in the cell, with "" ie. a blank).
    
- Preview and ok
- Repeat steps above for each of the items owned (can reuse expression from  `history`  tab)

This great [GREL cheat sheet](https://code4libtoronto.github.io/2018-10-12-access/GoogleRefineCheatSheets.pdf) from [code4lib Toronto](https://code4libtoronto.github.io/) has more details on building expressions using Regex.
{% endcapture %} {% include card.md header="Alternative method to add a new column using GREL" text=text %}

See how this works below.

{% include figure.html img="ORRegex.JPG" alt="Using Regex" caption="Using Regex" width="100%" %}

{% include button.md text="Watch the steps above on this video" link="https://vimeo.com/422342110/15f6fa71c1" color="info" %}


Let's now change the blank cells to a  `“No”`  value.
{% capture text %}
- Go to each new column and  `Facet > Text Facet`
- Hover over  `(blank)` and select edit 
- Change  `(blank)` to  `No` , ` apply` and close facet
- Repeat on each column{% endcapture %} {% include card.md header="Fill all blank cells in new columns with a value" text=text %}
Each location now has a column for the variables,  `table`,  `play area`,  `universal access toilet`  and  `water`,  with a  `yes` or  `no`  value.

The final step is to export specific variables from this tidy dataset to a .csv file which can be parsed (understood by) the geo.json tool used in the next lesson.

{% capture text %}
- Go to  `All` column  `>Edit Columns> Reorder Remove columns`
- Drag and drop the columns not needed including `Site Features`, `Site specific alerts`, `Site and Access Comments`, `GPS coordinates`, `Access Direction`, `Upcoming operation dates`, `signed`, `camping limitations` to the `remove` box.
- `Title`, `Latitude`, `Longitude`, `Location Description`, `Water`, `Universal access toilet`, `Table`, `Play area`, `Barbecue`  will remain
- Ok
- Click `Export` button, top right hand corner
- Select Comma-separated value dataset
- save file{% endcapture %} {% include card.md header="Export selected columns to .csv file" text=text %}


