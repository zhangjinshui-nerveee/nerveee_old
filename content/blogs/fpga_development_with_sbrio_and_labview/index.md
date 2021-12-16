---
title: FPGA Development with sbRIO and LabVIEW
summary: Use LabVIEW as a starter of FPGA development. It sucks, you are gonna love it. 
date: 2021-03-25
math: true
diagram: true
tags:
- EE
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---

> Now we use LabVIEW as the starter. <br>
> It sucks, you are gonna love it.

- "timing error" during compiling
> "The FPGA compiler returns a timing error if the propagation delay between any two registers exceeds the FPGA clock rate." I solved this error by replacing for loop with exhaustive comparison. But, what is a register in LabVIEW? And propagation delay? See the link below.<br>
> [Understanding Timing Considerations for FPGA VIs (FPGA Module)](https://zone.ni.com/reference/en-XX/help/371599P-01/lvfpgaconcepts/registers/)<br>
> Propagation delay is the time it takes a signal to travel from one register to the next. Because registers update every clock cycle, the propagation delay must not exceed the clock cycle.

# Things we should know 
> I have just started using FPGA for one or two weeks. 

## Market
- Comparison

## Development Environment

## Running python script in labview
- Notice: FPGA is only support by 32-bit LabVIEW. Therefore the python should be also 32-bit.
- Error code: 1667. "Python node in xx.vi."
> cause: the modules imported in .py is not installed. 

For more error codes, check here.<br>
[General LabVIEW Error Codes](https://zone.ni.com/reference/en-XX/help/371361R-01/lverror/misc_lv_error_codes/)<br>
[Labview Error Code Family](https://labviewwiki.org/wiki/LabVIEW_Error_Code_Family)
note: general, not all !!!

## Manipulate Arrays in FPGA (with LabVIEW)
- The size of array must be fixed. (The FPGA needs to reserve some resource for this array) And the size can not be changed during the program, thus functions like "delete from array" can not be used. Also, the computing ability would put some limits on the size of array. 
- We usually use one-click loop structure, where some functions would be disabled, such as "rotate array". 
- 
