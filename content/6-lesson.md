---
title: Map
nav: true
---
# Mapping data using GeoJSON

We are now going to map the Driver Reviver data via its lat lon points.  You can use any spreadsheet tool and prepare a list of coordinate points (known as features). 

You must name the column headers lat and lon, or the fuller spelling, latitude and longitude.  The order of the columns does not matter.  

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
