---
title: 2kW Full-GaN Boost Converter
summary: Generic Compact Daughter Board.
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
# Background
To power the computer room, we were asked to design a 2kW boost converter prototype. The table below specifies the parameters.

| Parameter | Value |
| Input Voltage | 200~300V |
| Output Voltage | 400V |
| Output Ripple | 2% | 
| Power Rating | 2kW |
| Other requirement | Full-GaN |

At this time, [our company](https://shop34012880.taobao.com/?spm=a230r.7195193.1997079397.2.36a35baao0FdHc) (I am the manager, nominated by my senior) was planning for a novel plug-in GaN daughter board. So, "Let's do it."

We developed a daughter board that integrated the power semiconductors and driving circuits. And this project was the first try. 



# Daughter Board
It consists of a power board, as below,
<img src = "GaN_Power_Board.png ">  
as well as a driving board, as bleow. 
<img src = "GaN_Daughter_Board.png">
The photo of the daughter board is given as below. 
<img src = "daughter_board.jpg">

# Converter
We equiped a mother board for the packaged daughter board. And the ultimate solution is shown in photos below.
<img src = "Aside.jpg ">
<img src = "B_side.jpg ">
<img src = "C_side.jpg ">
<img src = "E_side.jpg ">
The controller realises the functions including dual-loop feedback regulation, over-current protection, soft start, etc.  
