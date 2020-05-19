---
title: Tidy
nav: true
---

# Tidy data - a revisit 

-----

To create a [tidy](https://cran.r-project.org/web/packages/tidyr/vignettes/tidy-data.html) dataset, where:
- Each variable forms a column
- Each observation forms a row
- Each type of observational unit forms a table,

multi-value cells need to be split by the value.  

This task is helpful where there are multiple values in a cell that are not organised consistently, such as when survey respondents can select multiple, controlled values to answer a question.  The  `Site features`  column in the dataset `QLDDriverReviverStations.csv`  is an example of this.  Let's explore:

{% capture text %}
- Create a new project with dataset  `QLDDriverReviverStations.csv`  in OpenRefine
- Name project  `QLDDriverReviverStationsClean` 

To split the values in  `Site features`  across multiple columns we need to standardise the content.
- Go to  `Site features`  column
- Identify missing values with  `Facet> Customised Facet > Facet by blank`

It appears the original spreadsheet has *hard* returns inside the cells remove these with:

- `Edit Cells> Common Transform  > Collapse consecutive whitespace` 

Now we want to perform a facet by splitting the values, but we need to clean the cells up first.

- Clean up the cells to remove the  `“* “`  with  `Edit Cells > Transform`  and 
- GREL expression:  `value.replace("* ",";").replace(" *",";")`  to replace the whitespace around the  ` *`  with a common separator.

There is still a bit more cleaning to do to remove the whitespaces around the separator ` ;`  .  The GREL expression won’t work with this as a separator unless it is represented consistently in each cell.

- Remove the “; “ with  `Edit Cells > Transform and 
GREL expression:  `value.replace("; ",";").replace(" ;",";")`
- `Facet > Custom text facet > using value.split(“;”)`  to see all value results{% endcapture %} {% include card.md header="Activity - transforming data using GREL" text=text %}




{% capture text %}
Use the strategy above to remove the right-hand bracket (")") from the  `Suburb_PostCode`  column.
- `value.replace(")", "")`{% endcapture %} {% include card.md header="Activity - remove another character" text=text %}

It is easy to re-use GREL expressions, as OpenRefine provides a history of commands. You can select them and reuse as is or make changes. Let's try this with the remainder of the unnecessary characters in the  `Suburb_PostCode`  column. You want only to have a separator left between our two values in each cell.  The comma is the separator in this variable.

{% capture text %}
- at  `Suburb_PostCode` column, select  `Edit cells > Transform ...`
- click the  `History`  tab
- click on the first  `Reuse`  option
- click inside the expression box, change character  `")",""` to `", ",","`  (i.e. comma & space character to comma no space character)
- preview to check correctness
- click  `OK`.{% endcapture %} {% include card.md header="Activity - repeat transformation steps by using History" text=text %}

{% include button.md text="Watch video" link="https://vimeo.com/412605118/b259dd9e3c" color="info" %}

-----

Let's explore the  `Suburb_PostCode`  column to see which postcodes were the most or least prominent traffic crash locations.

### Splitting cells

Splitting multi-valued cells will enable faceting by text. This is also useful for splitting full names in first and last name columns and more.

{% capture text %}
- Click down arrow at the top of the  `Suburb_PostCode`  column.
- Choose  `Edit cells > Split multi-valued cells`
- At the separator Expression box, check that the correct separator, i.e. a comma, is specified.
- Click  `OK`.

Note that the rows are still numbered sequentially and that there are now 55056 rows, which no longer reflects one row per accident record. These are compound data objects.

- Click the  `Records`  option to change to  `Records`  mode and then go back to  `Rows`.

Note how the numbering changes as you toggle – indicating that several rows are related to the same record. This method is useful for  `JSON`  and  `xml`  files which have compound data objects.

It would be possible to use a text facet to see this data, but this is not the most efficient method.{% endcapture %} {% include card.md header="Activity - splitting cells" text=text %}

-----

### Undo and Redo

It is common while exploring and cleaning a dataset to discover after you've made a change that you really should have done something else first. OpenRefine provides *Undo* and *Redo* operations to make this easy, no matter how far along you have gone.

{% capture text %}
- Click where it says  `Undo / Redo`  on the top left side of the screen. All the changes you have made so far are listed here.
- Click on the previous step, to remove the split in the cell values of  `Suburb_PostCode`  column.
- Visually confirm that the columns data has been re-joined.

Go back a step
- before moving on to the next lesson,  `Undo`  to the step **before** we first used GREL to remove all the extra characters in  `Suburb_PostCode`.
- Go back to  `Facet/filter tab`.{% endcapture %} {% include card.md header="Activity - Undo" text=text %}

-----

### Join up GREL commands

Let's perform the earlier clean up steps and customised text faceting for  `Suburb_PostCode`  column. We can do this more efficiently by joining up the GREL expressions.

{% capture text %}
- select  `Suburb_PostCode`  column.  All three cleaning steps can be performed by combining  `value.replace`  expressions.
- select  `Edit cells > Transform ...`
- in the Expression box, enter  `value.replace("(", "").replace(")", "").replace(", ", ",")`
- click *Preview*
- click `OK`{% endcapture %} {% include card.md header="Activity - join up GREL commands" text=text %}

-----

### Split multi value cells into multiple columns (tidy data)

Let's split  `Suburb_PostCode`  data into two columns one for suburb and another for postcode.

{% capture text %}
- select  `Suburb_PostCode`  column
- edit  `Column > Split`  into several columns ...
- keep the Separator as a comma, and split the data into two columns
- leave the *After Splitting* boxes checked
- Click  `OK`.

The original column has now been replaced with two columns for different values.

A column named  `Suburb_PostCode 1`  contains the names of suburbs.

A column named  `Suburb_PostCode 2`  contains postcodes in green characters.  

The change in colour denotes that OpenRefine has changed the underlying *format* of the data from *text* to *number*.

Let's edit the column headings to represent the data more accurately.

- go to  `Suburb_PostCode 1`
- select  `Edit Column > Rename this column`  and enter  `Suburb`  as the new column name
- repeat the process for  `Suburb_PostCode 2`  to rename the column to  `Postcode` .{% endcapture %} {% include card.md header="Activity - joining up GREL commands" text=text %}


{% include button.md text="Watch video" link="https://vimeo.com/412605933/d8be2a9d15" color="info" %}
