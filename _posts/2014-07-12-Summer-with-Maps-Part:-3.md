---
layout: post
title: Summer with MAPS Part 3
tags:
- GNOME
- Maps
- GSoC
- GSoC Reports
---

Hi all!!

<img src="/public/img/maps.png" title="Maps" style="float:right;"/>

This is my third report on my work with GNOME-Maps on POIs.
Its almost a month now from my previous post.

## What Was Done !! ##

* Previously, I used ChamplainTileSource to render and place the POI icons. So, the location of the POI was limited to the Tile. So, the issue of cutting of POI icons came up when the POIs were close to the tile boundaries. So, instead of placing the Markers seperately on each Tile, a ChamplainMarker Layer was used which covers the MapView and the issue was solved. ChamplainTileSource is still used for caching and POI rendering purposes. This work will further be modified and be based on Damians work on Popover.

* Added Icons from the Maki POI icon library and used them in GNOME Maps. Still unsure and in disussion whether we should use icons provided by Geocode-Glib or remove the dependency from it.

* Splitted up the work done into Patches and submitted it for reviews. ([Support for POIs](https://bugzilla.gnome.org/show_bug.cgi?id=731587))


## Whats Next !! ##

* Clean up and base all my patches submitted so far on Damians work on Popover.[Use GtkPopover instead of ChamplainMarker](https://bugzilla.gnome.org/show_bug.cgi?id=722871)

* Implement Popover Design for POIs

* Get POI info from Wikipedia if available

* Plugin Routing (i.e, Select this as a start, destination or VIA point)

* Plugin Damians CheckIn Patches in the POI Popovers (i.e, let users checkin on this place)

* GUADEC :smiley: