---
layout: single
title:  "Reviving an old Pioneer stereo"
date: 2020-06-20
tags: [electronics, soldering]
excerpt: "Or: The Case for Hoarding Old Electronics"
read_time: true
---

Around this time last year, I was walking around a [warehouse filled with crates of records](https://www.kingstonsymphony.ca/concerts-events/calendar/vinyl-records-sale/), when my girlfriend spotted something interesting in a pile of old audio equipment.

It was an old stereo receiver, a Pioneer VSX-5300.  I checked the label:  8 dollars, and the front display was dead.  Without thinking twice, I bought it and loaded it into the back of my car, along with a pair of speakers and a handful of LPs.

![Stereo]({{ "/assets/images/stereo1.jpg" | relative_url }})

Anyone who knows me or has had the misfortune of living with me knows that I bring home lots of assorted electronic junk, usually salvaged from the trash.  This stereo had seen better days.  A bit of googling told me this model was from about 1988, and it looked the part.  The power cord was held together with marrettes, and as promised, the display didn't work.   I figured even if it wasn't fixable, eight bucks wasn't bad for a metal box filled with useful components.

I had no idea what was wrong with it — whether the LCD was *really* dead, or if it was just a loose wire or something — but eventually I figured it out.  After a bit of "percussive maintenance", I noticed that the display would flicker on if I pressed hard on the top half of the display.  This got me thinking there was some kind of loose connection inside.   At this point, I couldn't resist opening it up, so I unscrewed the cover and dove in, doing my best to keep away from the scary-looking capacitors.

{% capture fig_img %} ![Caps]({{ "/assets/images/stereo3.jpg" | relative_url }}) {% endcapture %}
{{ fig_img | markdownify | remove: "" | remove: ""}} <photocaption>I wouldn't mess with these.</photocaption>

Getting to the front-panel PCB — the one that connects to the display — is a task that involves disconnecting a lot of old, non-standard ribbon cable connectors, probably the most tedious part of this job.  Luckily, after doing some more research, I found some forum posts that explained how to deal with the ribbon cables.  For anyone reading this and trying to do the same type of repair:  for the WHITE ribbon cable connectors, you have to press down on the connector with a screwdriver while pulling the cable.  For the GREY connectors, you have to lift up the connector itself to unlock it, *then* pull out the cables.  

My favourite part about this thing: on the back, there's a physical switch to enable a "station name" feature, which lets you assign a 4-character name to each radio station preset.  But if you enable it, you only get to save ten stations instead of 30!  

I can only imagine that this thing didn't have enough EEPROM to store both the station names AND the radio presets, and the designers had to deal with that limitation by adding a hardware switch.  I don't envy the embedded systems engineers of the 80s.

![Switch]({{ "/assets/images/stereo6.jpg" | relative_url }})

The front-panel PCB contains the main microcontroller, the buttons, and the pin header that drives the front display.  Once the front panel PCB was exposed, I could see the problem: some of the solder joints had very fine circular cracks around the base, and they were only making contact when the display was pressed in.  Fixing it was just a matter of re-soldering those joints.  Afterward, the display worked like a charm.

If you're looking at the PCB from the top down, you'll want to look for a row of ten or so pins toward the left side of the board.

{% capture fig_img %} ![Solder joints]({{ "/assets/images/joint.jpg" | relative_url }}) {% endcapture %}
{{ fig_img | markdownify | remove: "" | remove: ""}} <photocaption>Look out for joints with hairline cracks like these.  Current only flows through them when pressure is applied to the PCB and the crack is closed.  Melting the joint and letting it harden again is usually all you need to do to fix it.</photocaption>

So, for anyone who came here in the hopes of figuring out how to do this task (you'll need a screwdriver and a soldering iron):
	
1. Unscrew and remove the top cover.  
2. Unscrew the front panel (3 screws on top and 3 on the bottom).
3. Now, you'll notice that a bunch of ribbon cables have to be disconnected to get the front panel completely free.  Disconnect those the way I mentioned above.
4. The grounding wire for the volume knob LED - aka, the black wire coming from the volume dial soldered to the right side of the chassis - also needs to come out.  De-solder it or rip it out.
5. Now that the front panel is free, examine the PCB for any cracked joints, and re-solder them.  This should fix the dead display.

Installation is the reverse of removal.  Enjoy.



![the Stereo]({{ "/assets/images/stereo7.jpg" | relative_url }})
