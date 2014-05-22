---
layout: post
title: Summer with MAPS Part 1
tags:
- GNOME
- Maps
- GSoC
- GSoC Reports
---

<b>Hi all!!</b>

This is my first report on working on GNOME Maps.
I have worked on a few features which I will be describing below.

## Querying of POIs ##

I wrote a gjs overpass query manager (a wrapper perhaps) that fetches the POIs provided by OSM using the [Overpass Query Language](http://wiki.openstreetmap.org/wiki/Overpass_API/Overpass_QL).
Basically, it can be configured to add types of POIs(tags) that needs to be fetched from the overpass, takes as input a [Bounding Box](http://wiki.openstreetmap.org/wiki/Bounding_Box) and it will generate the corresponding URL containing the query that can be understood by Overpass.

The code can be found [here](https://github.com/rishirajsinghjhelumi/GNOME-Maps/blob/poi-testing/src/overpass.js).

#### A simple usage demo ####

```javascript
let QM = new Overpass({
	'timeout' : 600,
	'outputCount' : 1000,
	'outputFormat' : 'json'
});

QM.addSearchTag('amenity', 'pub');
QM.addSearchTag('amenity', 'hospital');
QM.addSearchTag('amenity', 'fast_food');
QM.addSearchTag('amenity', 'restaurant');
QM.addSearchTag('amenity', 'library');

let bbox = {
	'bottom': 41.7,
	'left': -0.4,
	'top': 41.8,
	'right': -88.3
};
let queryUrl = QM.getQueryUrl(bbox);

log(queryUrl);

```

This URL can then be queried to the server that will return the POIs as a JSON.

## Selection of POIs ##

I wrote a couple of scripts to get the tags available in OSM and getting the count information relating to that tag.
[Taginfo](taginfo.openstreetmap.org) provided a wealth of information regarding the tags.
The selection of POIs is an ongoing process. [Mattias](https://plus.google.com/+MattiasBengtsson), [Jonas](https://plus.google.com/103582536569221580484), [Andreas](https://plus.google.com/107646837068615384568) and myself are working on selecting the best set of POIs that will be shown to the user.

## Overlaying of POIs ##

POIs are shown on a separate layer, i.e., a layer on top of the map-tiles layer (the layer which displays the map images). This layer contains only the clickable location markers corresponding to a POI, clicking on them provides information regarding the POI. 

## Caching of POIs ##

The caching of POIs is done so that when the user pans away from a place, and then returns the overpass is not queried.
It is done in a similar fashion like the tiles image caching in maps.
[Libchamplain](https://wiki.gnome.org/Projects/libchamplain) provides apis for caching, so that you can write your own virtual functions on what to cache, and it will do the rest, both in memory and file system.

## Rendering of POIs ##

Since I was caching POIs, that are nothing but a place marker in the form of JSON data, a POI renderer was required by libchamplain so that it knows how to render the data that it has cached.

One of my tasks will be to make this renderer as generalised as possible, so that it can be used for User Checkins (another Maps project by [Damian](https://plus.google.com/+DamiánNohales)) also, and possibly other things that have place information encoded as JSON.

<hr/>
Meanwhile, my next task would be to write a function that selects an icon for a given poi type. This function would exist in [geocode-glib](https://developer.gnome.org/geocode-glib/stable/) library, and will be using [Maki POI Icons](https://github.com/mapbox/maki).

I will be writing another blog soon depicting more functionality I add.
