---
layout: post
title: GSoC and GUADEC
tags:
- GNOME
- Maps
- GSoC
- GUADEC
---

<img src="/public/img/maps.png" title="Maps" style="float:right;"/>

## GSoC ##

So, GSoC finished a week ago, and my project had been very interesting and a great learning experience
for me. There were a lot of ups and downs during the project, a lot of code had to be changed.
The main and exciting thing was I got to try many solutions to the problems I faced and my mentors
supported me a lot.

Regarding the project, Initially I was using libchmaplain to overlay, cache and render POIs, but
the solution that I reached was very hacky and their were a lot of dependencies on libchamplain.
(The way I was using caching module of libchamplain wasn't the way it was 
meant to be used. :stuck_out_tongue_winking_eye:)

So, I implemented my own memory and DB caching of tiles in Maps and used it, which is somewhat neat now.
The patches are under review and hopefully will be merged with the next release of Maps.

## GUADEC ##

I am thankful to GNOME Foundation for providing me travel sponsorship and accommodation for GUADEC.
This was my first visit to a place outside India and it felt really amazing. I met my mentor Mattias and
Dario (another GSoC student in Maps) and we hacked for 3 days on Maps, which was also a very nice experience for me.

<img 
	src="/public/img/sponsored-badge-shadow.png"
	title="GUADEC" 
	style="display: block;
    margin-left: auto;
    margin-right: auto;"/>