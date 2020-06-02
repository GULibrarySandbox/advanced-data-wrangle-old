---
title: Map
nav: true
---
# Visualise the data
----
#### Map the data using GeoJSON

Now for the next exciting step, to map the  `Driver Reviver`  data via latitude and longitude points.  You can use any spreadsheet tool to prepare a list of coordinate points (known as features).   

{% capture text %}
GeoJSON is popular, open format for map data, and works across many tools.  A GitHub repository can automatically display any GeoJSON files in a map view using [Open Street Map](https://www.openstreetmap.org).

GeoJSON data must follow a structured format, and the file name may end with either .geojson or .json. The GeoJSON structured format orders coordinates in longitude-latitude format, the same as X-Y coordinates in mathematics. [(Dougherty, 2017)](https://datavizforall.org/convert-geojson.html){% endcapture %}
{% include alert.md text=text color=info %}

{% capture text %}
- Open [http://geojson.io](http://geojson.io)
- Find the  `QLDDriverReviverStationsClean.csv` file 
- `Drag the file` onto the map.  
- Look at features – change  `file view`  from  `JSON`  to  `table`  to see the data structured for the human eye. 
- Click on a  `point`  to show data 
- Untick  `Show style properties`  and save
- Save file as GEOJSON file into downloads.{% endcapture %} {% include card.md header="Map data with GEOJSON" text=text %}

{% include button.md text="See how to map the data with GeoJSON.io in this video" link="https://vimeo.com/425012075/174f63e945" color="info" %}

----
#### Display the map using Github

We now need a website to display the map.  To do this we are going to upload our geoJSON file to the open source repository [Github](https://github.com/) that can host and share files, code and much more.

Here is an example of an interactive [map](https://github.com/stapletonsl/ClassData2019/blob/master/OzUnis.geojson) created using geoJSON and hosted by Github. Click on the points for information about the locations.

In this next activity learn how Github works and create a repository to host the map via Github's tutorial. The first step is to register for an account.

{% capture text %}
- Go to [https://github.com/](https://github.com/)
- Register for Github account or login if you have one already. 
- Or you can use another hosting service you can embed into.
- Do *Hello World tutorial* [https://guides.github.com/activities/hello-world/](https://guides.github.com/activities/hello-world/)
- Go to your newly created  `Hello World` repository
- Select  `Upload file`
- `Drag and drop`  your newly created  `map.geojson`  file 
- Name it  `Driver Reviver Stations`
- You have just published in interactive map with data!{% endcapture %} {% include card.md header="Upload map to Github" text=text %}


See the steps illustrated below.


{% include figure.html img="ADORGithub.JPG" alt="Upload a file to Github repo" caption="Upload a file to Github" width="100%" %}


{% include figure.html img="ADORGitUpload.JPG" alt="Upload a file to Github repo" caption="Select the map.Geojson file" width="100%" %}
