---
layout: post
title:  "New Project: Robbins at Home"
author: "Tod Robbins"
date:   2017-02-27 10:00:00 -0700
categories: update
---
I've had a fuzzy project idea floating in my head for a while now. The basic gist of the project is the documentation of all historical residences of Robbins family members starting with Daniel and Hope Robbins. If we can establish a latitude/longitude of a residence, whether the physical structure remains extant or not, through documentation then I think it would be useful to collate those locations into a database rendered as a map.

To initiate the project, here is the last residence of my great-great-great-grandmother, Hannah Libby Carter Robbins:

<div id='map'></div>
<script>
L.mapbox.accessToken = 'pk.eyJ1IjoidG9kcm9iYmlucyIsImEiOiJjaXpwdHgxbWowMHhoMndwN3V6dWJnYTd5In0.8VcUGZ3PuLMhewTm6MijAw';
var map = L.mapbox.map('map', 'mapbox.streets')
  .setView([40.2338, -111.6585], 14);

var featureLayer = L.mapbox.featureLayer({
  'type': 'FeatureCollection',
  'features': [
    {
    'type': 'Feature',
    'geometry': {
      'type': 'Point',
      'coordinates': [-111.671379,40.228241]
    },
    'properties': {
      'name': 'Hannah Libby Robbins<br>ca. 1930',
      'description': '409 S 700 W<br>Provo, UT 84601',
      'marker-color': '#00abff',
      'marker-size': 'large'
    }
  }]
})
.addTo(map);

featureLayer.eachLayer(function(layer) {
  var content = '<h2>' + layer.feature.properties.name + '<\/h2>'
  + '<p>' + layer.feature.properties.description + '<\/p>';
  layer.bindPopup(content);
});
</script>
