---
title: The Physics Behind Photosensors
tags: [Physics Behind, Photography, Optics/Photonics]
style: fill
color: secondary
comments: true
description: A dive into modern CMOS Imaging architecture used in most consumer cameras
mathjax: true
---
<br>
### Prelude
I took a class on scientific imaging where we examined imaging systems ranging from atomic scale imaging to astral imaging, as well as using _Mathematica_ for image processing & analysis. This class was an amalgamation of my hobby and academic interest, so I'm going to share one of the coolest bits of knowledge I've gained from the course (credit to Dr. deHarak, and the textbook _Principles of Digital Image Processing by Burger & Burge_). While CMOS architectures are broad, I'm focusing on the CMOS image sensor here, specifically the Active-Pixel Sensor (known as APS-C).
<br>
### Brief Introduction to Photodiodes
The building block of most imaging systems, at 2 to 30 $$\mu$$m, this is the foundational pillar of consumer cameras. From mobile cameras to 15,000 dollar  professional cameras to 80,000 dollar cinema cameras, this is the reason it all works. The core issue at hand here is finding a way to convert light to either an applied voltage or a current, depending on the specific operation. At the p-n junction (these are the two types of semiconductor materials, doped accordingly to produce holes for electrons to pass through the junction) an incoming photon exceeding a threshold of energy hits the diode and excites an electron $$\to$$ causing it to move $$\to$$ which fills the hole $$\to$$ thus allowing for the flow of current through the junction to the cathode. Interestingly, the absorption of light is a quantum phenomena where electrons are excited to higher energy levels, leading them to be more mobile.
$$\frac{hc}{\lambda}$$ where $$h$$ is the Planck constant, $$c$$ is the speed of light, and $$\lambda$$ is the wavelengh, is what each photosensor picks up. An array of these super tiny diodes make up the photosensor.
<br>

Based on this, intuitively we know that absorption of light depends entirely on the _exposure time_ of the diodes to the light source. That leads to the signal (the image, in this case). However, it also leads to noise(extraneous unwanted stuff that can distort the true values & bury them), so there is a signal to noise ratio (SNR - bigger is better) involved:

$$SNR = \frac{PQ_et}{\sqrt{PQ_et+Dt+N_r^2}}$$

where $$P$$ is the photon flux (rate of change of photons per pixel per second), $$Q_e$$ is the quantum efficiency, $$t$$ is time, $$D$$ is the dark current, $$N_r$$ is the readout noise (usually 2-20 electrons per pixel)

##### Tangent On Discretization...
A reason this phenomena is so interesting is more biological/neurological than anything else. Our eyes(rather, occipital lobe, but you get the idea) are in a state of continuous spatial sampling while temporal sampling is handled by an entirely different part of the brain (which in this case would be working memory handled by the right side of the prefrontal cortex) yet still meshing together on demand. For example, if I was to ask what you were looking at around noon, that's discretizing a continuous temporal & spatial sampling, assuming it's past noon and you've been looking at other things after noon. The cohesive structure of the brain allowing for two intensive phenomena to be meshed on demand is actually fascinating, and I find this to be more and more prevalent while studying physics, that the human brain & anatomy is a whole different beast in and of itself. I digress...

##### Anyways...
Basically: input $$\to$$ light, output $$\to$$ image. Intuitively thinking, we now have $$\mathbb{NxN}$$ photodiodes making up this photosensor. Each photodiode has incident photons which, through the doped p-n structure and holes, cause a net migration of electrons. Moving electrons = current. That current is measured at the electrodes as an induced voltage potential which is the heart of this discussion. That's the key bit of information as that is how what is seen is captured electronically. That's the first step to the analog to digital conversion...

### Analog To Digital Conversion
To capture RGB (color) light, a Bayer filter is placed over the photodiodes. A consumer camera pixel is simply 3 photodiodes measuring the intensity of one of the colors hitting it: R, G, and B.
{% include elements/figure.html image="http://www.siliconimaging.com/Images/Microlenses.gif" caption="Bayer Filter | Only photons of specific color wavelength pass through onto the diode" %}  
These make up the most basic pixels. Keep in mind that the camera is essentially capturing a 3-dimensional world onto a 2-dimensional time dependent continuous distribution of varying photon energies onto an $$\mathbb{NxN}$$ array of pixels (or $$\mathbb{NxM}$$; the geometry is manufacturer specific).
The individual pixel is also manufacturer specific, some containing 4 transistors, functioning as different gates. The actual analog to digital conversion is done by one of the transistors in the photodiode which measures the charge and sends the measurement through to a digitizer which converts it to a numerical value which gets processed. The summation of voltages across the entire photosensor gets passed through the digitizer which gives it a numerical value, which gets formed into the $$\mathbb{NxN}$$ matrix, thus forming a picture as we know it.

### Some Important Selection Criteria
- Number of pixels: Often used to judge the spatial resolution (i.e. how fine are the details being captured) of the sensor
    - It's not that simple. The size of the pixel is also very important and the biggest factor are actually the optics in front of the sensor.
- Pixel size: How big is the individual pixel? Smaller pixels $$\to$$ more per given area
    - However, keep in mind smaller pixels store less charge and the range of light values measured is reduced
    - smaller pixels can sometimes result in more noise in low light levels
- Sensor size: bigger is better usually. Both factors above should be harmonious with one another. Nikon, Sony, Canon and Leica have done a great job with this.
- Dynamic range: How many different light levels can be detected? Usually expressed in bits. A 10 bit dynamic range = $$2^10 = 1024$$ different levels can be resolved.
    - Small pixels cannot have a large dynamic range because they cannot hold enough electrons.
- Fill factor: How much of the sensors surface is used to gather light  
    - more surface $$\to$$ shorter exposure time
    - Full frame CCD (charge coupled device architecture) uses almost the entire sensor
    - CMOS architecture usually uses less of the surface. The transistors used for transferring the charge take up space.
- Quantum efficiency (QE): what is the chance that a single photon striking the photodiode will generate a single electron to be liberated?
    - A minimum energy threshold must be crossed (1.1eV, usually)
    - Front illuminated CCD's absorb short wavelength photons, waste the resolution effort
    - Back illuminated CCD's have a higher QE. Light incident on the back eliminates losses from the gates.
    - Historically, CMOS has had less QE than CCD's, but are near if not better nowadays
- Shutters: important b/c it determines when the camera 'detects' an image
    - Mechanical shutters are slow and physically placed in front of the sensor, usually in full frame CCD's.
    - Global shutters: entire active area of the sensor is detecting an image at the same time, meaning, the entire image is captured along the sensor simultaneously rather than being resolved as the shutter opens.
    - Rolling shutters: image is transferred pixel by pixel so the exposure values are different. Essentially the image is being exposed row by row. Why would anyone want this?
- Sensitivity: the lowest light level that can be detected. Usually this is the level at which a signal will be produced, typically at the same amplitude as noise signal.
- Aspect ratios: ratio of length to width.
