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
I took a class on scientific imaging where we examined imaging systems ranging from atomic scale imaging to astral imaging, as well as using _Mathematica_ for image processing & analysis. This class was an amalgamation of my hobby and academic interest, so I'm going to share one of the coolest bits of knowledge I've gained from the course (credit to Dr. deHarak, and the textbook _Principles of Digital Image Processing by Burger & Burge_). While CMOS architectures are broad, I'm focusing on the CMOS image sensor here, specifically the Active-Pixel Sensor (known as APS-C).
<br>
### Brief Introduction to Photodiodes
The building block of most imaging systems, this is the foundational pillar of consumer cameras. From mobile cameras to 15,000 dollar  professional cameras to 80,000 dollar cinema cameras, this is the reason it all works. The core issue at hand here is finding a way to convert light to either an applied voltage or a current, depending on the specific operation. At the p-n junction (these are the two types of semiconductor materials, doped accordingly to produce holes for electrons to pass through the junction) an incoming photon exceeding a threshold of energy hits the diode and excites an electron $$\to$$ causing it to move $$\to$$ which fills the hole $$\to$$ thus allowing for the flow of current through the junction to the cathode. Interestingly, the absorption of light is a quantum phenomena where electrons are excited to higher energy levels, leading them to be more mobile.
<br>

Based on this, intuitively we know that absorption of light depends entirely on the _exposure time_ of the diodes to the light source. Keep in mind that the camera is essentially capturing a 3-dimensional world onto a 2-dimensional time dependent continuous distribution of varying photon energies onto an $$\mathbb{NxN}$$ array of photodiodes (or $$\mathbb{NxM}$$; the geometry is manufacturer specific).

###### Tangent On Discretization...
A reason this phenomena is so interesting is more biological/neurological than anything else. Our eyes are in a state of continuous spatial sampling while temporal sampling is handled by an entirely different part of the brain yet still meshing together. For example, if I was to ask what you were looking at around noon, that's discretizing a continuous temporal & spatial sampling, assuming it's past noon and you've been looking at other things after noon. The cohesive structure of the brain allowing for two intensive phenomena to be meshed on demand is actually fascinating, and I find this to be more and more prevalent while studying physics, that the human brain & anatomy is a whole different beast in and of itself.

##### Anyways...
Basically: input $$\to$$ light, output $$\to$$ image. Intuitively thinking, we now have $$\mathbb{NxN}$$ photodiodes making up this photosensor. Each photodiode has incident photons which, through the doped p-n structure and holes, cause a net migration of electrons. Moving electrons = current. The electrodes measure the current, thus leading to a discretization of the induced voltage potential on the electrodes. 
