---
title: Layout
nav: true
---
# The Layout of OpenRefine

-----
{% include button.md text="Watch video" link="https://vimeo.com/412542634/f5b1ced9b9" color="info" %}


OpenRefine displays data in a tabular format. Each row will usually represent a 'record' or 'observation' in the data, 
while each column represents a type of information or 'variable'. This is very similar to how you might view data 
in a spreadsheet or database. As with a spreadsheet, the individual bits of data or 'values' live in 'cells' at the intersection 
of a row and a column. OpenRefine displays only a limited number of rows of data at one time. Ten is the default.

However, the program is working on ALL rows - the limit of the number of rows displayed saves memory being wasted.

You can adjust the number of rows displayed by choosing between 5, 10, 25 and 50 at the top left of the table of data. 
You can navigate through the records by using the previous/next/first/last navigation options at the top right of the table of data.

### Working with data in OpenRefine

Most options to work with data in OpenRefine are accessed from drop-down menus at the top of the data columns. 
When you select an option in a particular column (e.g., to make a change to the data), it will affect all the 
cells in that column. If you want to make changes across several columns, you will need to do this one column at a time.

###  Rows and Records

OpenRefine has two modes of viewing data: 'Rows' and 'Records'. In Rows mode, each row represents a single record in the data set.  In Records mode, OpenRefine can link together multiple rows as belonging to the same Record. 
This is useful when working with `xml` files, MARC records, as well as `csv` files. We will see an example of this later.

{% include figure.html img="ORLayout.png" alt="OpenRefine layout" caption="OpenRefine layout" width="75%" %}

### Undo / Redo

OpenRefine provides Undo and Redo operations to make changes to your data work, no matter how far along you have gone. Find out how this works in the [GREL](https://griffithunilibrary.github.io/intro-data-wrangle/content/6-lesson.html) activities. 

### Saving projects

Projects are saved automatically as you work on them,  so there is no need to save copies as you go along. 

### Opening existing projects

To open an existing project in OpenRefine, click  `Open Project`  from the main OpenRefine screen (in the left-hand menu). 
When you click this, you will see a list of the existing projects and can click on a project's name to open it.

### The sample dataset

The data in this workshop open data published by QLD Transport & Main Roads and downloaed from the Queensland Government's [open 
data portal](https://data.qld.gov.au). The original dataset presents 17 years of traffic accidents, their location, 
type of accident, level of injury, and other features, with over 300,000 observations.  

The data used in this lesson is a smaller four-year subset and has had changes made for training purposes.
