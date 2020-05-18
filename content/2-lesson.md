---
title: Create
nav: true
---

# Extract a sample of data to enhance
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
{% include card.md header="Upload data from your computer" text=text %}


{% capture text %}
- Choose `UTF8` as the method of encoding as this should convert any 'smart' formatting into plain text.
- Give the project a meaningful name such as `TrafficAccident_2018`
- If all looks fine, click `Create Project`.{% endcapture %}
{% include card.md header="Preview the data" text=text %}

We only want to work with traffic accident data from `2018` in the `Southern` `Local police region`, lets remove the others.

{% capture text %}
Step 1.
- Go to `Loc_Police_Region > Facet > Text facet` 
- Remove four choices leaving `Southern`  only (how do we do this?)
  - `Include`  the four locations
  - `All column > Edit rows > remove all matching rows` (5232 rows remaining)
- Close facet
Step 2.
- Remove all years apart from `2018` (how do we do this?)
  - Go to `Crash_Year > Facet > Text facet`
  - `Include` all years apart from 2018 (4164 matching rows)
  - Go to `All column > Edit rows > remove all matching rows` (1068 rows remaining)
- Close facet
- the dataset is reduce to a sample of 1068 locations.
