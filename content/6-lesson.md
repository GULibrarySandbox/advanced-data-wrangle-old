---
title: GREL
nav: true
---

# Transforming data using GREL 

(General Refine Expression Language)

-----

Transformations in OpenRefine enable manipulations of data in columns. Such types of changes include:

- Splitting data from a single column into multiple columns (e.g., splitting an address into multiple parts) to enable tidy data – one variable per column.

- Standardising the format of data in a column without changing the values (e.g., removing punctuation or standardising a date format)

- Extracting data from a longer text string (e.g., finding DOIs within a bibliographic citation)

It can be difficult to read, ingest and process data which has multiple values within the one cell.  OpenRefine has methods to split those values into multiple cells or columns. OpenRefine has several ways to do this. 

First we will split data using the in-built programming capabilities of GREL within OpenRefine.  GREL stands for *General Refine Expression Language*. GREL expressions are a little like Excel formulae, although they tend to focus on text manipulations rather than numeric functions.

{% capture text %}
Look at the data in  `Suburb_PostCode`  column.  It has more than one value in each cell. The values include the *suburb name* and a *postcode* inside brackets (). This is difficult to process and analyse and needs splitting to make the data tidy. Before we can split the values into individual columns, we first need to remove the extra characters such as *brackets* and *leading (or trailing) whitespace*.

Let's remove all the unnecessary characters by using the GREL command  `value.replace`.

`Value.replace`  is the *command*. What needs to be added to make the *command* work are what are called *arguments* in programming speak. In this case, the arguments are the values of *what needs to be replaced*, and then *what it needs to be replaced with*. The argument is written inside brackets like this  `("value to replace","new value")`.

- Click the down arrow at the top of the  `Suburb_PostCode`  column.
- Select  `Edit Cells > Transform ...` . 

This will open a window in which you can enter a *GREL expression*. An expression is a combination of the *command* you will be using, plus the *arguments* you will be using to modify the command, i.e. the values that will be changed.

- In the Expression box, type  `value.replace("(", "")`  to remove all left brackets by replacing them with nothing.

In this case, the second value is empty since we want to remove the bracket, i.e. replace the bracket with nothing. You do not need to add any spaces within the expression. If you do, and they appear inside the quote marks, they will be added or removed, depending on within which set of values they appear.

The *Preview* screen will display on the left the cell value as it is before transformation, and on the right, what the value will be after the expression has run. This allows you to correct any errors in writing the expression, e.g., adding spaces where they are not needed, using unmatching quote marks. 
- Click  `OK`.

The  `Suburb_PostCode`  column should now contain no left brackets.{% endcapture %} {% include card.md header="Activity - transforming data using GREL" text=text %}

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
