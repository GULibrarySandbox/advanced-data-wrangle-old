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

There are no missing values but it appears the original spreadsheet has *hard* returns inside the cells. Remove these with:

- `Edit Cells> Common Transform  > Collapse consecutive whitespace` 

We want to perform a facet by splitting the value, so we need to remove some extra characters and create a common separator.

- Remove the  `“* “`  with  `Edit Cells > Transform`  and 
- GREL expression:  `value.replace("* ",";").replace(" *",";")`  to replace the whitespace around the  ` *`  with a common separator.{% endcapture %} {% include card.md header="Tidy the 'Site features' column" text=text %}

The next step is to split the values so they can be moved to separate columns. There is a little more cleaning required to remove whitespaces around the separator ` ;`  .  The GREL expression to split the values won’t work with this as a separator unless it is represented consistently in each cell.

{% capture text %}
- Remove the  `“; “`  with  `Edit Cells > Transform` and 
- GREL expression:  `value.replace("; ",";").replace(" ;",";")`
- `Facet > Custom text facet > using value.split(“;”)`  to see all value results.
- These include  `play area`,  `table`,  `universal access toilet`  and  `water`.
- Click on first Facet result  `Play area` , with 11 results
- Go to column  `Site features > Edit column> add column based on this column`
- Type new column name  `Play area`
- Click inside expression box, delete  `value`  and type `"Yes"`
- Preview and ok
- Repeat steps above for each of the items owned (can reuse GREL expression from  `history`  tab) 

(Below is an alternative method to this which uses Regular Expression, a sequence of characters that define a search, in GREL.  Undo your steps to try this method){% endcapture %} {% include card.md header="Add a new column based on split values" text=text %}

{% capture text %}
- Go to column  `Site features` > `Edit column> add column based on this column`
- Type new column name  `Universal access toilet`
- Click inside expression box, enter GREL expression:
  `if(value.contains("Universal access toilet"),"Yes",value).replace(/.*[^Yes].*/,"")`
- Preview and ok
- Repeat steps above for each of the items owned (can reuse expression from  `history`  tab){% endcapture %} {% include card.md header="Alternative method to add a new column based on split values" text=text %}

Let's now change the (blank) cells a “no” value.
{% capture text %}
- Go to each new column and  `Facet > Text Facet`
- Hover over  `(blank)` and select edit 
- Change  `(blank)` to  `No` , ` apply` and close facet
- Repeat on each column{% endcapture %} {% include card.md header="Fill all blank cells in new columns with a value" text=text %}
Each location now has a column for the variables,  `table`,  `play area`,  `universal access toilet`  and  `water`,  with a yes/no value.

The final step is to export specific variables from this tidy dataset to a .csv file which can be parsed by geo.json.

{% capture text %}
- Go to  `All` column  `>Edit Columns> Reorder Remove columns`
- Drag and drop the columns `Site Features`, `Site specific alerts`, `Site and Access Comments`, `GPS coordinates`, `Access Direction`, `Upcoming operation dates`, `signed`, `camping limitations` to the `remove` box.
- `Title`, `Latitude`, `Longitude`, `Location Description`, `Water`, `Universal access toilet`, `Table`, `Play area`, `Barbecue`  will remain
- Ok
- Click `Export` button, top right hand corner
- Select Comma-separated value dataset
- save file{% endcapture %} {% include card.md header="Export selected columns to .csv file" text=text %}

{% include button.md text="Watch the steps above on this video" link="https://vimeo.com/412605933/d8be2a9d15" color="info" %}
