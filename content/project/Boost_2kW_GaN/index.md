---
title: 2kW Full-GaN Boost Converter
summary: Generic Compact Daughter Board.
tags:
- Power Electronics
date: "2020-07-27T00:00:00Z"

# Optional external URL for project (replaces project detail page).
external_link: ""

image:
  caption: Picture by Jimmy on Altium Designer
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
# Background
To power the computer room, we were asked to design a 2kW boost converter prototype. The table below specifies the parameters.

| Parameter | Value |
| -- | -- |
| Input Voltage | 200~350V |
| Output Voltage | 400V |
| Output Ripple | 2% | 
| Power Rating | 2kW |
| Other requirement | Full-GaN |

At this time, [our company](https://shop34012880.taobao.com/?spm=a230r.7195193.1997079397.2.36a35baao0FdHc) (I am the manager, nominated by my senior) was planning for a novel plug-in GaN daughter board. So, "Let's do it."

We developed a daughter board that integrated the power semiconductors and driving circuits. And this project was the first try. 



# Daughter Board
The daughter board consists of two parts, the driving board, which transform the digital pulses into the driving signals for GaN HEMTs, and the power board, which is actually a half-bridge topology and receives the driving signals to commutes the HEMTs. 

The figure below gives information of the **power board**.
<img src = "GaN_Power_Board.png ">  

The figure below gives information of the **driving board**.
<img src = "GaN_Daughter_Board.png">

Ultimately, we plug the power board onto the driving board, the integrated daughter board forms, as follows.
<img src = "P00628-103139.jpg ">
<img src = "P00628-103149.jpg ">

# Converter
We equiped a mother board for the packaged daughter board. And the ultimate solution is shown in photos below.
<img src = "Aside.jpg ">
<img src = "B_side.jpg ">
<img src = "C_side.jpg ">
The controller realises the functions including dual-loop feedback regulation, over-current protection, soft start, etc.  

# Testing Results
The test is performed with **YOKOGAWA·WT1804E precision power analyzer**.
## Efficiency
<img src = "efficiency.png">
The efficiency stays over 98.48% in full voltage range. 
## Adjustment due to Load
<img src = "load adjust.png">
Varying with the load, the output voltage changes within 396~401V. 
## Waveforms
<img src = "waveform.png">
The waveforms are given as below. (purple-current; green-voltage)

# Other
I am proud of myself, not because of the converter, but because of the box I made for it, so amateurly professional.
<img src = "case.png">
