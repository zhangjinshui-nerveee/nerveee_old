---
title: Development of Totem-Pole PFC Rectifier
summary: 98.1% peak efficiency & unity power factor.
tags:
- Power Electronics
date: "2020-07-27T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

links:
- icon: twitter
  icon_pack: fab
  name: Bilibili
  url: https://space.bilibili.com/321991714
url_code: ""
url_pdf: ""
url_slides: ""
url_video: ""

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example
---

![Topology of Totem-Pole Rectifier](TTPL_topology.png)

# Background
  Popular electrical appliances need rectifiers to transfer ac power to dc. The market has gradually eliminated traditional diode full-bridge recitifier due to its high current harmonics and low power factor. By contrast, the Totem-Pole bridgeless rectifier arouses wide concerns. The low device cost promises this converter a bright prospect.
# Challenges
   When working in Continuous Conduction Mode (CCM), the Totem-Pole rectifier suffers the current distortion at the zero-crossing area. 
   Traditional dual-loop control tries to make a tradeoff between the grid-frequency reference tracking effect and disturbance suppression. In this way, we might be able to reduce the zero-crossing distortion but likely to introduce high-frequency harmonics. 
## Waveforms Description
  ![Distorted Current](Original.png)<br>
  
  
  
# Methodology


# Experiments
  Results
  
# Small Tricks
  Simulation


What have we done.

What results have been obtained.

What we will do in the future.
