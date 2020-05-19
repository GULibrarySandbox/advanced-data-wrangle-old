---
title: Map
nav: true
---
# Mapping data using GeoJSON

We are now going to map the Driver Reviver data via its lat lon points.  You can use any spreadsheet tool and prepare a list of coordinate points (known as features). 

You must include column headers lat and lon, or the fuller spelling, latitude and longitude.  The order of the columns does not matter.  
 
{% capture text %}GeoJSON is popular open format for map data, and works across many tools. GeoJSON files can be used with Leaflet map code, Google Maps JS API code, Carto map tools, and more. Also, a GitHub repository will automatically display any GeoJSON files in a map view.

GeoJSON data must follow a structured format, but the file name may end with either .geojson or .json. The GeoJSON structured format orders coordinates in longitude-latitude format, the same as X-Y coordinates in mathematics. This is the opposite of Google Maps and several other web map tools, which order points in latitude-longitude format. [(Dougherty, 2017)](https://datavizforall.org/convert-geojson.html){end capture}{% include alert.md text=text color=info %}


{% capture text %}
{% endcapture %}{% include card.md header="Activity - tranforming text to numbers" text=text %}


{% include button.md text="Watch video" link="https://vimeo.com/412607607/08380e8150" color="info" %}
