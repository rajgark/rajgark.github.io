---
title: The Physics Behind Photosensors
tags: [Physics Behind, Photography, Optics/Photonics]
style: fill
color: secondary
comments: true
description: A dive into modern CMOS Imaging architecture
mathjax: true
---
<br>
### Prelude
I took a class on scientific imaging where we examined imaging systems ranging from atomic scale imaging to astral imaging, as well as using $Mathematica$ for image processing & analysis. This class was an amalgamation of my hobby and academic interest, so I'm going to share one of the coolest bits of knowledge I've gained from the course (credit to Dr. deHarak). While CMOS architectures are broad, I'm focusing on the CMOS image sensor here.
<br>
### Brief Introduction to Photodetectors
The building block of most imaging systems, this is the foundational pillar of consumer cameras. From mobile cameras to $15,000 professional cameras to $80000 cinema cameras, this is the reason it all works. The core issue at hand here is finding a way to convert light to either an applied voltage or a current, depending on the specific operation. At the p-n junction (these are the two types of semiconductor materials, doped accordingly to produce holes for electrons to pass through the junction) an incoming photon exceeding a threshold of energy hits the diode and excites an electron $\to$ causing it to move $\to$ which fills the hole $\to$ thus allowing for the flow of current through the junction to the cathode. Interestingly, the absorption of light is a quantum phenomena where electrons are excited to higher energy levels, leading them to be more mobile.
<br>
Based on this, intuitively we know that absorption of light depends entirely on the _exposure time_ of the diodes to the light source. Since this generates a current due to conversion of light to an electrochemical potential leading to a direct current, there's a density equation at hand here:
$$\mathscr{F} = \frac{\sigma V}{L}$$
<br>
$$\sigma = q(n\mu_n + p\mu_p)$$
