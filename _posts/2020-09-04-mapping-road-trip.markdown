---
layout: post
title:  "Mapping A Road Trip"
date:   2020-09-04 12:00:00 +0100
tags: [GIS, QGIS, cartography]
permalink: /blog/:title.html
---

In the absence of any foreseeable holiday (thanks, coronavirus!), I took the opportunity to relive (in a fashion) a journey I made last summer, mapping the 5,397-mile road trip around the west of the United States. 

<figure>
<img src="/assets/img/poster export 3000px.png" alt="Road trip map">
<figcaption>The final product</figcaption>
</figure>

For unnecessarily higher res images:
- [10000 × 7064 PNG (22.4 MB)]({{ site.baseurl }}{% link /assets/img/poster export 10000px.png %})
- Full size SVG (size MB)

When printed nicely as an A1 poster it also served as an excellent (belated) birthday present for the two friends I travelled with. This specification (A1 = 594mm × 841mm = eight A4 sheets) informed the design, and also presented a bit of a novel challenge, since this was the first time I had designed something this large. Size isn't really something I give much conscious thought to when making something that will be either on a screen, or A4/A3 size, but when the output gets this big I found that I can struggle to visualise how the final product will look, especially whether text and images will be too small/large once at the intended scale.

# Data collection

Before embarking on the trip last summer, I explored a few options for tracking the path we took: I needed something that could give me a relatively accurate track of the route, that would effectively record non-stop for three weeks without my having to actively intervene at any point. In the end I settled on using [Esplorio](https://esplor.io/), an iPhone app that records a continuous GPS track, optimised so as to minimise battery usage, which can be exported once the trip is finished[^1]. This was ideal for the task, as it didn't require me to buy a stand-alone GPS tracker, didn't add another device to charge every day, and could essentially be left to its own devices (pun intended), leaving me free to focus on our assorted American adventures.


# Mapping it out (ft QGIS)

Once I had the GPX track of my phone's location over the course of the three-week trip, I opened it in QGIS and had a look at where exactly I'd been.


<!-- ![USA route in QGIS](/assets/img/USA route in QGIS.png) -->
<figure>
<img src="/assets/img/USA route in QGIS.png" alt="USA route in QGIS">
<figcaption>If some of the screenshots have different layers visible in the layer pane it's because some were taken as I went and some were only taken as I was writing up this post</figcaption>
</figure>

Because the trip's dates in Esplorio comprised all the time from leaving up to returning to the UK, the GPS also included our routes to/from Heathrow, and around Reykjanesbær in Iceland, where we stopped for a night each way to/from Denver (although it seems to have stopped recording almost as soon as we were in the air, so the [apparent routes]({{ site.baseurl }}{% link /assets/img/Full route in QGIS.png %}) between each airport are just straight lines linking the last point recorded at take-off and the first as we landed).

I was pleased with the Esplorio data: aside from a few gaps (perhaps when my phone was completely turned off or the app had crashed), it very clearly traced the route we travelled over our 20 days in the country. The data plotted my location roughly every 20 seconds when we were moving (and less frequently when stationary in the interest of optimising file sizes and battery use). For the gaps in the data, I manually corrected the route in QGIS so that the whole route was mapped to roughly the same fidelity (see below). This level of detail was probably unnecessary for the scale of the poster, but a) I am a completionist and b) this may not be the only thing I produce using this data (although equally don't hold your breath). 

![Perfectionism-induced manual route correction](/assets/img/route correction x8.gif)

For most of the gaps the course of the missing route was obvious; for a couple instances when I was unsure I used the 'Places' view in the macOS Photos app to double check — clearly all the photos taken out of the car window weren't entirely useless!

![I once went on a school trip where we took a coach from Rome to Naples and I 'mapped' the route on my iPad by taking photos at regular intervals throughout the journey… clearly a sign of things to come](/assets/img/photos app map.png)

Once I had the entire route correctly plotted, I clipped it to only show its American part, excluding anything before/after we flew into/out of Denver. At this point (and indeed at many points throughout the process), I spent a long time browsing and scavenging for any and all sources of inspiration to inform the direction of my mapmaking – I'll highlight below some which most directly inspired certain elements of my final design.

The base of the map is simply national and state borders, the data for which is from [gadm.org](https://gadm.org/). I used the 'shared polygon edges' [tool from SAGA](http://www.saga-gis.org/saga_tool_doc/2.1.4/shapes_polygons_22.html) (in QGIS) to just get the internal (nation) state borders, meaning that the dashed borders did not stretch along the coastline (where no lines were needed delineate the states' borders). I did consider including some kind of hillshade/elevation information, or plotting the road network (beyond those along which we travelled), but in the end decided on a more simplistic approach. This hopefully made the poster less cluttered with less relevant details, allowing more space to show the places we *did* go, and in any case reduced the list of things that had to be done within the GIS!

The light greens and blue colour scheme took inspiration from [this](https://www.bekcruddace.co.uk/portfolio/guardian-travel-road-trip-maps/) set of illustrated road trip maps, alongside a few printed maps I had to hand. The only other area I did shade differently was that of the seven National Parks we visited, using data from [here](https://public-nps.opendata.arcgis.com/datasets/nps-boundary-1). The route line style was inspired by a [1946 map of 'Western Vacationlands'](https://www.davidrumsey.com/luna/servlet/detail/RUMSEY~8~1~321614~90090774:Western-Vacationlands) from the excellent David Rumsey Map Collection, which uses a bold red line to plot the Union Pacific's railway routes through several of the same locations we drove to:

<figure>
<img src="/assets/img/Western Vacationlands crop.png" alt="Detail from 'Western Vacationlands' map">
<figcaption>Detail from ‘Western Vacationlands’ map</figcaption>
</figure>

I chose to use a [California-centred version of the Albers projection](https://epsg.io/3311), hence the state/national borders defined by lines of latitude are visibly curved. I also added a fairly subtle glow effect around the coast to somewhat increase the land/sea contrast, inspired by one of Daniel Huffman's [tutorials](https://youtu.be/8ZOEo8fsM9s?t=1569).

# Pretty pictures (ft PowerPoint and Inkscape)

Once I'd got all the main cartographical steps out of the way, I exported everything from QGIS (as a vector image so everything would scale up to a big poster without getting pixelly) and opened it in my longtime image editor of choice …PowerPoint.
While PowerPoint is underrated as an image editor (especially in the absence of any of Adobe's pricier offerings), it is a bit of a Stockholm syndrome situation: PowerPoint does *technically* support SVGs, but a) doesn't yet have the option of exporting directly to an SVG in the PowerPoint for Mac version I have, and b) when it exports to PDF (the workaround I used to preserve the vector components, it inexplicably rasterises some elements but not others. And while it can cope well with a few simple SVG icons, if you have detailed vectors (ie coastlines, state borders, the GPS path) alongside hundreds of other text boxes, high-res photos, shapes, etc on one slide, you will discover that this is not a workflow for which PowerPoint has necessarily been designed. Simplifying the geographical elements as much as possible (while preserving the desired geographical accuracy) in QGIS before exporting helps somewhat (as does pointing a desk fan at the laptop), but the sluggishness seemed mostly unavoidable.

All this to say that PowerPoint will not be my first port of call for any future projects of a similar nature.

<figure>
<img src="/assets/img/PowerPoint proficiency.png" alt="Where's Clippy when you need him?">
<figcaption>Where's Clippy when you need him?</figcaption>
</figure>

One thing PowerPoint did make very easy was the map's title. Trying to generate/emulate some kind of all-American aesthetic, I drew up a shortlist of a few iconic American styles to inform my eventual design:
- I drew inspiration from the album art of Sufjan's and *Michigan* and *Illinois* records, the former's handwritten title (and map on the back of the LP) and the latter's pastiche of a comic book art style befitting the [Man of Metropolis](https://genius.com/Sufjan-stevens-the-man-of-metropolis-steals-our-hearts-lyrics)
- An alternate potential style was a wild west / cowboy aesthetic (reminiscent of our visit to the gold rush ghost town of Rhyolite, Nevada), but in the end this didn't fit in with the other styles
- The final title was the stylistic lovechild of retro 50s diner signs and the iconic (and stylistically similar) 'Welcome to Fabulous Las Vegas' sign. The former seemed to nicely encapsulate the notion of the all-American road trip; the latter inspired the ②⓪①⑨ circles

The title was modeled on one of the diner signs but built from scratch with shapes/text in PowerPoint.

![Titular inspirations](/assets/img/Title development.png)


All the labelling was also done in PowerPoint, which makes it easy to slightly curve the text (as in the Lincoln City or Hoover Dam labels) such that it remains obvious what point the text refers to while overall keeping the text relatively horizontal. I also made use of a glow effect (of the same colour as the background) as a way to subtly increase the labels' legibility in cases where they straddled a border (eg for Vancouver or the Hoover Dam, which both straddle state lines). The fonts were mostly pilfered from  [this collection](https://www.netcredit.com/blog/maps-iconic-us-road-trips/) of 'minimalist' road trip maps (again covering many of the same locations we visited), especially the faint, bold state names with wide kerning. I think label placement is one of those things that most people give little thought to when it's done well, but which can become glaringly conspicuous when not. Although the map is relatively sparsely labelled it took a bit of tessellation to fit in the California or Wyoming labels without obscuring our route or other labels, and I now have a newfound appreciation for whoever has the thankless task of labelling A-Z road maps!

<figure>
<img src="/assets/img/labels.png" alt="Not quite as challenging a labelling task">
<figcaption>Not quite as challenging a labelling task (but more of a challenge than it looks…)</figcaption>
</figure>

Once everything had been mapped and labelled, I wanted to add plenty of peripheral graphics that would recall the places we went and things we did, initially picturing something similar to many of Nate Padavick's [illustrated maps](http://www.idrawmaps.com/). Keenly aware of the severe limits to my artistic talent, I tried to keep the (illustrated) graphic elements relatively simple (and resist the temptation to attempt to recreate something like [this](https://www.digitalartsonline.co.uk/tutorials/adobe-illustrator/design-vector-map/#1)). One way of achieving this was by using photos in place of illustrated graphics where possible, which had the added bonus of depicting us alongside all the places we'd been to! Style wise, I copied a [hand-drawn road trip map](http://drawntheroadagain.com/the-final-tally/) in cropping the photos to circles and linking them with a line to where they were taken. 
Once I had selected the best 24 photos of the >1,500 taken over the course of the trip and placed them around map, I filled in the remaining negative space with a few final things: a couple of graphical in-jokes, a few quotes, and several icons from [flaticon.com](https://www.flaticon.com/)[^2] .

Finally, the text at the side highlights some 'statistics' about the journey. This element was inspired by a similar thing on [this](http://web.archive.org/web/20150401014509/http://papercut.fr/2010/03/laxnyc-map/) road trip map (yes, I did spend many hours googling 'road trip maps' and stealing the best ideas from each). The typeface used is [Highway Gothic](https://en.wikipedia.org/wiki/Highway_Gothic), the font used in most roadsigns in the US. The typeface has a range of weights/widths, allowing some words to be squished and others to take up more space, hopefully allowing for better alignment of the words.

![Can't say I prefer mine but I gave it a go ¯\_(ツ)_/¯](/assets/img/sidetext.png)

# Marks out of ten

This has been my first real attempt at producing anything like this, and one with which I'm *mostly* happy. That being said, my inner perfectionist is forever keen to highlight any shortcomings.

If I were to redo the map (which I daren't start doing else I'll never get anything else done) I might change up the illustrations a bit – at the moment they feel like they're a bit haphazardly placed to fill empty spaces (which isn't entirely untrue). I'm also not entirely satisfied with the text block on the left – while I like the idea, the spacing (which was purely determined by nudging everything around in PowerPoint until it looked 'about right') seems a bit off, especially with the different font sizes/weights. The [design](http://web.archive.org/web/20150319110113im_/http://papercut.fr/wp-content/uploads/2010/03/LAxNYC-map-zoom1.png) I based it on was left-aligned, and I think that by trying to have it fully justified I produced a problem previously not present.
Aside from possibly being slightly trypophobia-inducing, I think the circular photos work well on the whole. When the poster is viewed at the intended size, the photos are large enough to show the smaller details of some scenes, while being just about small enough to fit in ample photos from the course of the trip.

When I started writing up this blog I assumed it would be a brief undertaking that I could dash off before finally deleting all the tabs I've opened in the course of making the poster, but I seem to have accidentally written a few thousand words… So if you've made it this far, well done, you're likely the only one!

[^1]: This feature was free when I used the app, but they've since added a [Pro](https://esplor.io/pro.html) service which is now needed to export the GPX as I did. So anyone wishing to follow my methodology now has the choice between paying $49.99/year for the service or finding an alternative… if you do happen upon anything free/cheaper that closely replicates the functionality please do let me know!

[^2]: Flaticon asks that the author of each icon is credited, so in the interest of fair attribution: the gambling icon was made by [Eucalyp](https://www.flaticon.com/authors/eucalyp); the Las Vegas, waterpark, Route 66, and pancake icons were made by [Smashicons](https://www.flaticon.com/authors/smashicons); the cactus icon was made by [Pixel Perfect](https://www.flaticon.com/authors/pixel-perfect); the pine tree, Joshua tree, desert road, potato, wave, sunscreen, US flag, pizza, lighthouse, poker, passport, plane tickets, mountain, Democrat, and Republican icons were made by [Freepik](https://www.flaticon.com/authors/freepik); the forest icon was made by [Prettycons](https://www.flaticon.com/authors/prettycons); the seal icon was made by [surang](https://www.flaticon.com/authors/surang), all from [www.flaticon.com](https://www.flaticon.com/).