---
layout: post
title:  "Completing the #30DayMapChallenge"
date:   2020-12-01 12:00:00 +0100
tags: [GIS, cartography, QGIS, R]
permalink: /blog/:title.html
image: /assets/img/30DayMapChallenge-2020/header.png
---

As [promised]({% post_url 2020-10-31-30daymapchallenge %}), over the course of November I attempted to produce (and [tweet](https://twitter.com/Iawmatthew)) a map a day as part of the [#30DayMapChallenge](https://twitter.com/hashtag/30DayMapChallenge). I managed 22 out of the 30 days, the results of which are below. Sharing these comes with the emphatic caveat that each was produced in a day (indeed usually in only an hour or two), and so there are many elements I do not like and would change if I had more time. Maybe I'll go back and add to or otherwise improve some of them at a later date.

Over the course of the challenge I tried to document the data, tools, and methods I used, all of which is below alongside the maps. Mostly I stuck to QGIS for the mapmaking, matched with an embarrassingly frequent use of PowerPoint for final labelling/composition, and some occasional use of R to wrangle data before getting it into QGIS and make a few gifs at the end of the month.

Click below to go to a specific topic's map, or scroll down to see the full set. Most of the images are nice and big so feel free to open each in a new tab should you want to admire them in full detail!

* toc
{:toc}

# Points

Population in England and Wales, with a point for every ~10 people.

![points](/assets/img/30DayMapChallenge-2020/points.png)

**Data**: Output Area populations from the 2011 UK census (I can't remember exactly where I got this from now, but it's likely either the [ONS website](https://www.ons.gov.uk/) or [Nomis](https://www.nomisweb.co.uk/).  
**Tools**: QGIS  
**Methods**: roughly based on [this tutorial](https://www.maartenlambrechts.com/2018/02/13/one-person-one-dot-maps-and-how-to-make-them.html) by Maarten Lambrechts.

# Lines

All the roads in Great Britain

![lines](/assets/img/30DayMapChallenge-2020/lines-GB.png)

A closer view of of dense London 

![yet more lines](/assets/img/30DayMapChallenge-2020/lines-London.png)

A nice chunk of sparser Scotland by means of contrast

![will these lines ever stop](/assets/img/30DayMapChallenge-2020/lines-Scotland.png)

**Data**: Ordnance Survey's fantastic [Open Zoomstack](https://www.ordnancesurvey.co.uk/business-government/products/open-zoomstack) geopackage (this will be a recurring theme this month)  
**Tools**: QGIS  
**Style inspiration**: the book 'QGIS Map Design' by Anita Graser and Gretchen Peterson, specifically the bit about colour blending

# Polygons

Experimenting with carving up Great Britain in different ways (and styling at random):  
a) ceremonial counties

![polygons-ceremonial-counties](/assets/img/30DayMapChallenge-2020/polygons-ceremonial-counties.png)

b) voronoi polygons based on county towns of said counties

![polygons-voronoi](/assets/img/30DayMapChallenge-2020/polygons-voronoi.png)

c) parliamentary constituencies

![polygons-westminster](/assets/img/30DayMapChallenge-2020/polygons-westminster.png)

d) European NUTS 1 regions
![polygons-nuts-1](/assets/img/30DayMapChallenge-2020/polygons-nuts-1.png)

**Data**: Ordnance Survey's open [Boundary-Line](https://www.ordnancesurvey.co.uk/business-government/products/boundaryline) data and manually and somewhat haphazardly plotted county towns  
**Tools**: QGIS  
**Styling**: These maps were basically just excuses to play with Topi Tjukanov's [qlimt and qartoon styles](https://github.com/tjukanovt/qgis_styles)

# Hexagons

Average monthly daytime land surface temperature, November 2019 to October 2020

![hexagons are allegedly the bestagons](/assets/img/30DayMapChallenge-2020/hexagons.gif)

**Data**: [Land Surface Temperature](https://lpdaac.usgs.gov/products/mod11c3v006/) from the MODIS sensor on NASA's Terra and Aqua satellites  
**Tools**: QGIS, PowerPoint for labels, [ezgif.com](http://ezgif.com)  
**Methods**: the hex bin polygons take the mean value of all valid pixels in the underlying surface temperature raster

# Blue

![Alexa, play Eiffel 65](/assets/img/30DayMapChallenge-2020/blue.png)

**Data**: [Global Burden of Disease Study](http://ghdx.healthdata.org/gbd-results-tool) – I was surprised that subnational data was available for Kenya, Indonesia, and Brazil but not for any of the EU. I also haven't looked into the methodology so would be cautious in drawing any conclusions from this kind of global dataset  
**Tools**: R for data wrangling, QGIS for mapping, PowerPoint for labelling – the part that took the longest was finding and downloading and subsetting and reshaping the data as required before actually mapping it  
**Design inspiration**: [Our World in Data](https://ourworldindata.org/)'s global-scale choropleths ([for example](https://ourworldindata.org/grapher/life-expectancy?tab=map) – I stole the map projection and almost all the other design elements from these)


# Red

Distance to the nearest working McDonald's ice cream machine, as of earlier this afternoon (red: near, yellow: not so near, red dots: working machine, lots of red dots on top of each other: white dots, ⚠: broken machine)

![mcbroken.com renews my faith in the value of web mapping](/assets/img/30DayMapChallenge-2020/red.png)

**Data**: the sublime [mcbroken.com](http://mcbroken.com) – I love the data for this even if the map itself is very ugly  
**Tools**: QGIS  
**Methods**: buffer around the locations with working ice cream machines  
**Styling**: I was trying to go for a McDonald's red/yellow combo but the final result gives off the aura of some kind of fast food induced hellscape

# Green

A map of Cambridge's greenbelt, mapped from one of the little rural enclaves with a view of said belt from my window

![my best map](/assets/img/30DayMapChallenge-2020/green.png)

**Data**: greenbelt via the (now former) [Department for Communities and Local Government INSPIRE OGC WFS Service](https://data.gov.uk/dataset/f7f5e3a4-05a6-41f0-bc66-a36df6708fe0/dept-for-communities-and-local-government-inspire-ogc-wfs-service), everything else from OS [Open Zoomstack](https://www.ordnancesurvey.co.uk/business-government/products/open-zoomstack)  
**Tools**: QGIS, making use of the ability to combine multiple symbologies (namely shapeburst, striped fill, and outline for the greenbelt itself)  

I think this is probably my favourite of the maps I made over the course of the month.

# Yellow

Basically just the opposite of the [Blue](#blue) map

![Alexa, play REM](/assets/img/30DayMapChallenge-2020/yellow.png)

**Data**: [World Happiness Report](http://worldhappiness.report) 2020 (specifically, that in Figure 2.1) – can't say I've given much attention to the methodology so I don't think a dose of scepticism would go amiss. As with the depression map, lots of time was taken trying to get the data into the right format, especially matching countries named slightly different things in the data being mapped vs the shapefile with the country outlines  
**Tools**: R for data wrangling, QGIS for mapping, PowerPoint for labelling

# Monochrome

Buildings in London, coloured by height

![mono = one, chrome = chrome](/assets/img/30DayMapChallenge-2020/monochrome.png)

**Data**: London building heights from [Emu Analytics](https://www.emu-analytics.com/products/datapacks.php)  
**Tools**: QGIS, GIMP to colour the greyscale output (not that I couldn't have done that in QGIS, I just wanted to play around with different colourings more easily)

I find maps of building footprints a) visually pleasing (especially in dense/interestingly developed cities) and b) quite a nice way of getting a sense of the morphology of a city[^1]: it's interesting seeing the difference in both height and density north and south of the Thames in a way you can't quite perceive looking at (eg) Google Maps or a London A-Z. I also love being able to see the shape of something (eg the Thames, Great Britain) by either the negative space around certain features (eg buildings) or the aggregate of certain features (eg roads), which I suppose feeds into both a) and b).

At the risk of another unnecessary list, making the map made me realise a) how much I usually rely on colour (even when only trying to map one variable) and b) the importance of classification in choropleth maps (or similar): if you use equal intervals, almost everything save a few skyscrapers gets pushed down to the lowest bin, but if you use quantiles you can't differentiate those few extreme tall buildings from the others which may be half their height but are grouped together, so it takes some experimentation to get a colour mapping which manages to show the variation satisfactorily. Here the buildings are classified in 16 classes using the Jenks natural breaks classification (based on each building's maximum height).


# Grid

England/Wales gridded population

![grid](/assets/img/30DayMapChallenge-2020/grid.png)

**Data**: Output Area populations from the 2011 UK census (I can't remember exactly where I got this from now, but it's likely either the [ONS website](https://www.ons.gov.uk/) or [Nomis](https://www.nomisweb.co.uk/)  
**Tools**: QGIS – I was going to do it in R based on [this code](https://jschoeley.github.io/2018/06/30/bubble-grid-map.html) by Jonas Schöley but swiftly realised it would be quicker to do so in QGIS, and proceeded to do so  
**Methods**: (probably much more convoluted than necessary) – generate points per polygon (OA) based on population (ie create the 'Points' map), generate grid, count points in grid polygon, grid cells mapped as points with their size based on the point count^0.4

# 3D

Population in England and Wales mapped to height (and also colour for good measure) 

![now in 3D](/assets/img/30DayMapChallenge-2020/3D.png)

**Data**: Output Area populations from the 2011 UK census (I can't remember exactly where I got this from now, but it's likely either the [ONS website](https://www.ons.gov.uk/) or [Nomis](https://www.nomisweb.co.uk/)  
**Tools**: QGIS  
**Methods**: (probably much more convoluted than necessary) – generate points per polygon (OA) based on population (ie create the 'Points' map), generate grid, count points in grid polygon, plot height and coclour based on a Jenks natural breaks classification with 15 classes

This day (which included various other aborted attempts prior to the final output) made me realise how hard it is to do 3D mapping (especially of any variable other than terrain) well.


# Map not made with GIS software

US unemployment trends by state, "mapped" with sparklines in Excel

![better than making maps in MS Paint?](/assets/img/30DayMapChallenge-2020/excel-1.png)

The recent spikes (vertical black lines at the right of cells) 'squish' the y-axis somewhat (the max value is Nevada in April this year with 30.1% unemployment), so below is a version with each cell/state setting their own y-axis range:

![at least it crashes less than ArcGIS](/assets/img/30DayMapChallenge-2020/excel-2.png)

**Data**: [US Bureau of Labor Statistics](https://www.bls.gov/web/laus.supp.toc.htm) – I chose US data purely because it was easier to make a 'grid' map (where each state is a spreadsheet cell) from 50 states than 650 Parliamentary constituencies (or whatever other spatial division any UK data would be in)  
**Tools**: Excel  
**Methods**: pivot table to wrangle the data, sparklines to map the trend for each state in a cell of the spreadsheet

# Raster

Average monthly daytime land surface temperature, November 2019 to October 2020 (basically a non-hexbin version of the Hexagons map)

![raster](/assets/img/30DayMapChallenge-2020/raster.gif)

**Data**: [Land Surface Temperature](https://lpdaac.usgs.gov/products/mod11c3v006/) from the MODIS sensor on NASA's Terra and Aqua satellites  
**Tools**: QGIS, PowerPoint for labels, [ezgif.com](http://ezgif.com) 

# Climate change

Participation in the 2016 Paris Climate Agreement

![increasingly hot stuff](/assets/img/30DayMapChallenge-2020/climate.png)

**Data**: [UN Treaties Collection](https://treaties.un.org/Pages/ViewDetails.aspx?src=TREATY&mtdsg_no=XXVII-7-d&chapter=27)  
**Tools**: R for light data wrangling, QGIS for mapping, PowerPoint for labelling  
**Colour scheme**: kinda ugly QGIS defaults but oh well

# Connections

Connections between students' term/home time addresses (in four parts!)

Map 1: all of GB – rather cluttered but shows the main axes of movement

![Great Britain](/assets/img/30DayMapChallenge-2020/connections-GB.png)

Map 2: movement to/from Nottingham (although I'm slightly suspicious that there don't appear to be *any* movements between there and Wales)

![Nottingham](/assets/img/30DayMapChallenge-2020/connections-notts.png)

Map 3: to/from Cambridge

![Cambridge](/assets/img/30DayMapChallenge-2020/connections-cambridge.png)

Map 4: to/from London

![London](/assets/img/30DayMapChallenge-2020/connections-london.png)

**Data**: Origin and destination of people who moved from a student term time address in the year before the 2011 census (I mapped those aged 18+) via [Nomis](https://www.nomisweb.co.uk/census/2011/SM01UK), [UK Data Service](https://www.statistics.digitalresources.jisc.ac.uk/dataset/2011-census-geography-boundaries-local-authorities) for Local Authority boundaries  
**Tools**: R for data wrangling, QGIS for mapping  
**Methods**: calculate LA centroids and export to csv, use R to make a table with start/end geocode and number of moves count for each LA pair, create a linestring for each pair (using the centroid csv as lookup for the geometry), export the table with WKT linestrings as a csv and import to QGIS, set alpha level based on the natural log of number of moves between each LA pair:  
![expression](/assets/img/30DayMapChallenge-2020/connections-expression.png)  
**Inspiration**: James Cheshire's [flow mapping](https://jcheshire.com/visualisation/mapping-flows/)

# Historical map

I didn't have time to get as far as I would have liked so this is very much a work in progress: ceremonial counties in GB in a vaguely 'historical' style (late C19 / early C20 maybe?)

![historical](/assets/img/30DayMapChallenge-2020/historic.png)

**Data**: countries from the excellent [naturalearthdata.com](http://naturalearthdata.com), ceremonial counties from Ordnance Survey's open [Boundary-Line](https://www.ordnancesurvey.co.uk/business-government/products/boundaryline) data, county towns (rather haphazardly) mapped by me  
**Tools**: QGIS for everything  
**Tasting notes**: The text buffers detract from the historical look, but without it the (mostly automatically placed) labels aren't very legible so I've kept it for now – hopefully at some point I'll have time to go back and properly place the labels (including counties/countries) and add more bits

For this day I think I probably spent more time looking at old maps to get styling ideas than I gave myself to actually make the map (hence it is rather unfinished)…

# NULL

A lazy entry: a conspicuous line of missing data in the European Settlement Map, seen here remorselessly slicing Cambridge in twain

![NULL](/assets/img/30DayMapChallenge-2020/null.png)

**Data**: [European Settlement Map 2015](https://ghslsys.jrc.ec.europa.eu/ESMVisualisation.php)

# Population

A recycled map (see Points), but newly labelled: population in England and Wales, with a point for every ~10 people

![population](/assets/img/30DayMapChallenge-2020/population.png)

**Data**: Output Area populations from the 2011 UK census (I can't remember exactly where I got this from now, but it's likely either the [ONS website](https://www.ons.gov.uk/) or [Nomis](https://www.nomisweb.co.uk/), place labels from OS [Open Zoomstack](https://www.ordnancesurvey.co.uk/business-government/products/open-zoomstack)  
**Tools**: QGIS


# Water

The Wet Hemisphere™ ft annoying rendering artefact where Antarctica struggled to wrap itself around the bottom of the world

![wet wet wet](/assets/img/30DayMapChallenge-2020/water.png)

**Data**: [7+GB of beautiful bathymetric data](http://doi.org/10/dtg3) courtesy of the British Oceanographic Data Centre  
**Tools**: QGIS  
**Methods**: [this very helpful tutorial](http://www.statsmapsnpix.com/2019/09/globe-projections-and-insets-in-qgis.html) by Alasdair Rae to get a globe projection in QGIS

# Landuse

A somewhat arbitrarily generalised map of modal land cover in the UK

!['landcover' or 'land cover'?](/assets/img/30DayMapChallenge-2020/landcover.png)

**Data**: Land Cover Map 2015 by the UK Centre for Ecology & Hydrology, in particular [this dataset](https://doi.org/10.5285/711c8dc1-0f4e-42ad-a703-8b5d19c92247) for Great Britain and [this dataset](https://doi.org/10.5285/c38b3986-b67e-40e9-9026-85ddbe3830d3) for Northern Ireland, plus the country outlines and hillshade from [naturalearthdata.com](http://naturalearthdata.com)  
**Tools**: QGIS  
**Methods**: 1km dominant land cover (aggregate classes so fewer categories) rasters → 'Sieve' processing algorithm → polygonize the result → GRASS v.generalize with method=chaiken (nice because GRASS maintains the topology) → choose colours at semi-random

This took quite a while to work out a methodology to get the (vector) output I wanted from the (raster) original data – while I'm mostly happy with the final result there are a few places (eg around Southampton) where you can make out a part of the original pixelly grid that stubbornly refused to smooth. Also the country outline doesn't match the data (eg around Orkney), but that is entirely my fault and could be very easily remediated were I not rushing.

# Elevation and/or Map with a New Tool

A big slice of the Peru-Chile trench and Andes, nauseatingly spinning:

![elevation](/assets/img/30DayMapChallenge-2020/elevation.gif)

**Data**: [7+GB of beautiful bathymetric (and elevation) data](http://doi.org/10/dtg3) courtesy of the British Oceanographic Data Centre  
**Tools**: QGIS, Tyler Morgan-Wall's {[rayshader](https://www.rayshader.com/)} package for R  
**Methods**: Methods: crop bathymetric DEM (.tif) in QGIS, create a separate .png to colour the bathymetry, mostly follow [this rayshader tutorial](https://wcmbishop.github.io/rayshader-demo/)

# A map

A final map: another use of rayshader, this time to map the Grand Canyon

![Grand Canyon 1](/assets/img/30DayMapChallenge-2020/grand-canyon-1.gif)

And another bonus render just for good measure: a zoom into the position of the previous gif, this time with some satellite imagery to get a better feel of the nicely stratified geology and the vegetation on the plateaus

![Grand Canyon 2](/assets/img/30DayMapChallenge-2020/grand-canyon-2.gif)

**Data**: NASA 1-arcsec SRTM (via [Derek Watkins' SRTM Tile Downloader](http://dwtkns.com/srtm30m))  
**Tools**: QGIS, Tyler Morgan-Wall's {[rayshader](https://www.rayshader.com/)} package for R  
**Methods**: crop DEM in QGIS, vary `render_depth(focus=)` in rayshader to slide the focus (using a function from [this rayshader tutorial](https://wcmbishop.github.io/rayshader-demo/) to easily calculate the values for each gif frame)  
<br>

---

I really enjoyed not only having an excuse to do lots of mapping myself, but also seeing all the maps produced by everyone else (if you're in the mood for browsing, have a scroll through either the [hashtag on twitter](https://twitter.com/hashtag/30DayMapChallenge) or [this gallery](https://david.frigge.nz/30DayMapChallenge2020/maps.html) assembled by David Friggens). I think a particular value of the challenge was in forcing myself to produce and publish something within a set (and short) period of time – without these constraints I hesitate to publish anything that isn't just the way I want it, and so have quite a collection of half-finished projects that are yet to reach my exacting standards.

[^1]: See also the [Nolli Map](https://www.youtube.com/watch?v=EeJZR3Pv9tM) and the use of [figure-ground](https://en.wikipedia.org/wiki/Figure-ground_diagram) maps in urban design.