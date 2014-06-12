---
layout: post
title: Summer with MAPS Part 2
tags:
- GNOME
- Maps
- GSoC
- GSoC Reports
---

Hi all!!

<img src="/public/img/maps.png" title="Maps" style="float:right;"/>

This is my second report on my work with GNOME-Maps on POIs.
For the past week I have been working on Supporting different POI icon types in Maps.
Geocode-glib provides a few pois (around 11) but the subset of POIs we will be selecting to display will be larger than that. So somehow we needed to add support for these extra icons also.

The icons used in the Maps application for displaying specific place types like railway stations, schools, bars and a few others are taken from geocode-glib place-type.
So, there is a dependency for these icons on geocode-glib.

So, My mentor([Mattias](https://plus.google.com/+MattiasBengtsson)) and me had a little chat with [Bastien](https://plus.google.com/+BastienNocera) (hadess) and he suggested to include the icons in the Maps application itself rather than I providing patches for each of those, and later if a place type becomes necessary for other application it might be good option to move it to geocode-glib later.

So, I extended the GeocodePlace and made a Place class for the maps itself which can be used to fit our needs. Thus, removing the dependency on icons from the geocode-glib library.
This class will have its own function for getting and loading the icons for the specified type and it can be extended to support any other function that needs to be associated with a Place, say for example, information about a place from wikipedia or any other source, chekins, or some images of a place etc (A Map application can really have a lot of features!!).

The icon set I am using is [Maki Icons](https://github.com/mapbox/maki) which is also used by geocode-glib.

## Whats Next ##

I will be rebasing my code to the latest Maps commit and will be submitting the first batch of patches for review on bugzilla.
And a bit of work on UI Popover for the POIs.

## GUADEC ##

I am thankful to GNOME for providing me travel sponsorship and accomodation for GUADEC.
This will the first time I will be taking part and I am really excited about it.

<img 
	src="/public/img/sponsored-badge-shadow.png"
	title="GUADEC" 
	style="display: block;
    margin-left: auto;
    margin-right: auto;"/>
