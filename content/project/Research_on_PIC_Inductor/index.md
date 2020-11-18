---
title: Critical Design of PIC Inductor
summary: Smaller, smaller, smaller.
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
> Actually, this research happened during the development of Totem-Pole PFC converter. However, I found that this idea could be applied to any circuit, and it would be especially useful for those with powdered iron cores. Therefore, I decided it an independent project.

# Background
As the electrical vehicle (EV) being increasingly popular, onboard chargers (OBC) have aroused great research and commercial interest worldwide. The state-of-the-art OBCs usually use Wide-Bandgap devices -- mainly GaN HEMTs and SiC MOSFETs -- because of their low loss and high switching frequency. 
This significantly shrinks the space occupied by heat sink. Meanwhile, the passive components account for the predominant volume of the converter.

Different from traditionally popular ferrite cores, powdered iron cores have a special saturation process. 
<img src = "Comparison_between_PICandFC.png" width = "50%">

# Saturation Influencing Harmonics

## Methodology

## Verification

# Variable Switching Frequency Scheme

# Summary
