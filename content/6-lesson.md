---
title: Map
nav: true
---
# Visualise the data
----
#### Map the data using GeoJSON

We are now going to map the Driver Reviver data via its lat lon points.  You can use any spreadsheet tool and prepare a list of coordinate points (known as features).   

{% capture text %}
GeoJSON is popular open format for map data, and works across many tools. GeoJSON files can be used with Leaflet map code, Google Maps JS API code, Carto map tools, and more. Also, a GitHub repository will automatically display any GeoJSON files in a map view.

GeoJSON data must follow a structured format, but the file name may end with either .geojson or .json. The GeoJSON structured format orders coordinates in longitude-latitude format, the same as X-Y coordinates in mathematics. [(Dougherty, 2017)](https://datavizforall.org/convert-geojson.html){% endcapture %}
{% include alert.md text=text color=info %}

{% capture text %}
- Open [http://geojson.io](http://geojson.io)
- Find the  `QLDDriverReviverStationsClean.csv` file 
- `Drag the file` onto the map.  
- Look at features – change  `file view`  from  `JSON`  to  `table`  to see the data structured for the human eye. 
- Click on a  `point`  to show data 
- Untick  `Show style properties`  and save
- Save file as GEOJSON file into downloads.{% endcapture %} {% include card.md header="Map to GEOJSON" text=text %}

{% include button.md text="Watch video" link="https://vimeo.com/412607607/08380e8150" color="info" %}

----
#### Display the map using Github

We now need a website to display the map.  To do this we are going to upload our geoJSON file to the open source repository [Github](https://github.com/) that can host and share files, code and much more.

Here is an example of an interative [map](https://github.com/stapletonsl/ClassData2019/blob/master/OzUnis.geojson) created using geoJSON and hosted by Github. Click on the points for information about the locations.

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

{% include button.md text="Watch video" link="https://vimeo.com/412607607/08380e8150" color="info" %}
