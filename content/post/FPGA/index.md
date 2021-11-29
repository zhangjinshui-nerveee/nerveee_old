---
title: FPGA Learning Notes
date: 2021-03-25
math: true
diagram: true
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

- Now we use LabVIEW as the starter. It sucks, you are gonna love it.

- "timing error" during compiling
> "The FPGA compiler returns a timing error if the propagation delay between any two registers exceeds the FPGA clock rate." I solved this error by replacing for loop with exhaustive comparison. But, what is a register in LabVIEW? And propagation delay? See the link below.
> [Understanding Timing Considerations for FPGA VIs (FPGA Module)](https://zone.ni.com/reference/en-XX/help/371599P-01/lvfpgaconcepts/registers/)
> Propagation delay is the time it takes a signal to travel from one register to the next. Because registers update every clock cycle, the propagation delay must not exceed the clock cycle.
