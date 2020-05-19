---
title: Map
nav: true
---
# Mapping data using GeoJSON

We are now going to map the Driver Reviver data via its lat lon points.  You can use any spreadsheet tool and prepare a list of coordinate points (known as features). 

You must include column headers lat and lon, or the fuller spelling, latitude and longitude.  The order of the columns does not matter.  
 
{% capture text %}GeoJSON is popular open format for map data, and works across many tools. GeoJSON files can be used with Leaflet map code, Google Maps JS API code, Carto map tools, and more. Also, a GitHub repository will automatically display any GeoJSON files in a map view.

GeoJSON data must follow a structured format, but the file name may end with either .geojson or .json. The GeoJSON structured format orders coordinates in longitude-latitude format, the same as X-Y coordinates in mathematics. This is the opposite of Google Maps and several other web map tools, which order points in latitude-longitude format. [(Dougherty, 2017)](https://datavizforall.org/convert-geojson.html){% include alert.md text=text color=info %}


{% capture text %}
{% endcapture %} {% include card.md header="Activity - tranforming text to numbers" text=text %}

#### Numeric facets

Sometimes there are non-numeric values or blanks within a column which may represent errors in data entry. We can find these by using a  `Numeric`  facet.

{% capture text %}
- Go to the  `Postcode`  column which was transformed to numbers.
- Edit a few cells, replacing the numbers with text, such as "bc", and make a few other cells blank.
- Apply a numeric facet to the column you edited.

Notice that there are several checkboxes in this facet,  `Numeric`,  `Non-numeric`,  `Blank`,  `Error`.

Below these are counts of the number of cells in each category. You should see checks for  `Non-numeric`  and  `Blank`  if you changed or deleted some values.

- experiment with checking or unchecking these boxes to select subsets of your data.
- when finished exploring, close this facet by clicking the  `x`  in the upper left corner of its panel.

Note that closing a facet will not undo the edits you have made to the cells in this column.

- Use the  `Undo / Redo`  function to reverse these changes.{% endcapture %} {% include card.md header="Activity - numeric facet" text=text %}


{% include button.md text="Watch video" link="https://vimeo.com/412607607/08380e8150" color="info" %}
