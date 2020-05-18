---
title: Scripts
nav: true
---
# Use scripts to automate processes

A script is a series of programming steps to automate the execution of tasks.

### How OpenRefine documents changes made to data

As you conduct your data wrangling, OpenRefine saves every change you make to the dataset. 

{% capture text %}Note:
OpenRefine makes and uses a copy of your raw dataset and this original raw dataset remains unchanged.{% endcapture %}
{% include alert.md text=text color=secondary %}

These changes are saved in a format known as [JSON](https://en.wikipedia.org/wiki/JSON)(JavaScript Object Notation). You can export the JSON script and apply it to other data files. If you had 20 files to clean, and they all had the same type of errors (e.g., misspellings, leading white spaces) and all files had the same column names, you could save the JSON script, open a new file in OpenRefine, paste in the script, and run it to apply the changes to the new dataset. This gives you a quick way to clean all your related data.

{% capture text %}
- Open  `Undo / Redo`  tab
- Select  `Extract ...`

Currently all the operations you have made to the dataset are highlighted within the script window.

- Select the steps that you want to apply to other datasets by using the `check boxes`.
- `Copy` the code from the right-hand panel and `paste` it into a text editor (like *NotePad* on Windows or *TextEdit* on Mac). 
- Save it as a plain text file
  - in *TextEdit*, do this by selecting  `Format > Make plain text` 
  - and save the file as a  `.txt` file.{% endcapture %} {% include card.md header="Activity - save the data wrangling steps as a script" text=text %}

### Import a script to use with another dataset

Let's practise running the script you just created on a new dataset. We'll test this on an raw, uncleaned version of the dataset we've been working with.

{% capture text %}
Create a new project in OpenRefine using the  `QLDtrafficAccidentsOpenDataVer1.csv`  dataset you downloaded at the start of the workshop.
- Click on OpenRefine Symbol (top left-hand corner of screen), to open the menu page
- select  `Create Project`  tab
- select  `Get data from this Computer` tab >  `browse`  button
- browse to select the file `QLDtrafficAccidentsOpenDataVer1.csv` you saved to your `Downloads` folder.
- either click `Open` or double-click on the filename to import it into OpenRefine.
- click  `Next`
- give the project a different name 
- select  `Create Project`
- click the  `Undo / Redo`  tab (left-hand menu) >  ` Apply`
- paste in the contents of  `.txt`  file you saved.
- click  `Perform operations`  button{% endcapture %} {% include card.md header="Activity - import and use a script on another dataset" text=text %}


{% include button.md text="Watch video" link="https://vimeo.com/412608736/a3ea7cc31c" color="info" %}

---- 

The dataset should now be the same as your other cleaned dataset.

For convenience, we used the same dataset.  You could use this process to clean related datasets.

For example, you could apply your changes to data that you had collected over different time periods or data that was collected by different researchers (provided everyone uses the same column headings). The data in this file was generated from a database, so the column headings for subsequent data downloads should be the same. 
