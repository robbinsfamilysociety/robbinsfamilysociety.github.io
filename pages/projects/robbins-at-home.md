---
layout: page
title: Robbins at Home
permalink: /projects/robbins-at-home/
menus: projects
---

> We are collecting the locations of all historical residences related to the Robbins family. Feel free to submit your data to [robbinsfamilysociety@gmail.com](mailto:robbinsfamilysociety@gmail.com).

{% assign url_parts = page.url | split: '/' %}
{% assign url_parts_size = url_parts | size %}
{% assign rm = url_parts | last %}
{% assign base_url = page.url | replace: rm %}

<ul>
{% for node in site.pages %}
  {% if node.url contains base_url %}
    {% assign node_url_parts = node.url | split: '/' %}
    {% assign node_url_parts_size = node_url_parts | size %}
    {% assign filename = node_url_parts | last %}
    {% if url_parts_size == node_url_parts_size and filename != 'index.html' %}
      <li><a href='{{node.url}}'>{{node.title}}</a></li>
    {% endif %}
  {% endif %}
{% endfor %}
</ul>

<div id='map'></div>
<script>
L.mapbox.accessToken = 'pk.eyJ1IjoidG9kcm9iYmlucyIsImEiOiJjaXpwdHgxbWowMHhoMndwN3V6dWJnYTd5In0.8VcUGZ3PuLMhewTm6MijAw';
L.mapbox.shareControl = true;
var map = L.mapbox.map('map', 'mapbox.satellite')
  .setView([40.2280, -100.0000], 4);

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
