---
title: Create
nav: true
---

# Obtain a sample of data to enhance
----

{% capture text %}
**Windows**: double-click on the `openrefine.exe` file. Java services will start automatically on your machine, and OpenRefine will open in your browser. Be sure to use either Chrome or Firefox, as OpenRefine does not play well with Microsoft Edge or Safari.

**Mac**: OpenRefine can be launched from your Applications folder.

**Linux**: navigate to your OpenRefine directory in the command line and enter `./refine`.

Once OpenRefine is launched in your browser, the home screen displays options to `Create Project`, `Open Project`, or `Import Project`. 

Select `Create a project`.

**If launch fails**

If OpenRefine does not automatically open within your browser after launch, point your browser at `http://127.0.0.1:3333/` or `http://localhost:3333` to launch the program.{% endcapture %}
{% include card.md header="Launch OpenRefine" text=text %}


{% capture text %}
- Choose `Create Project`
- Select `Get data from this Computer`.
- Select `Choose Files` and browse to select the file `QLDTrafficAccidentCleanData_2014_2018.csv` you saved to your `Downloads` folder.
- Either click `Open` or double-click on the filename to import it into OpenRefine.
- Click `Next`.{% endcapture %}
{% include card.md header="Create a project by uploading data from your computer" text=text %}


{% capture text %}
- Choose `UTF8` as the method of encoding as this should convert any 'smart' formatting into plain text.
- Give the project a meaningful name such as `TrafficAccident_2018`
- If all looks fine, click `Create Project`.{% endcapture %}
{% include card.md header="Data preview" text=text %}


### Key Points

- Use the `Create Project` option to import new data to work on.
- You can control how data is imported by changing options on the import screen.
