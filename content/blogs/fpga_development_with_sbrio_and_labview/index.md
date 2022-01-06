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


# Developer with sbRIO
> CompactRIO board-level controllers, such as CompactRIO Single-Board Controllers (sbRIO), have the same architecture as packaged CompactRIO controllers, but come without rugged packaging, and have a smaller form factor. sbRIO and cRIO are basically the same thing. 

> Objectives:
> - Figure out how the information flows among three levels: PC(Host), Real-time processor, FPGA. 


## Architecture
- LabVIEW
- A processor running real-time operating system RTOs, excels at floating-point math and analysis. 
- A reconfigurable FPGA, excels at smaller tasks that require high-speed logic and precise timing
- Interchangeable industrial I/O modules. (Extra products, not on the sbRIO)


## Designing a CompactRIO Software Achitecture (Several common cRIO architectures)
- Host --Ethernet-- Real-time VI --PCI bus-- FPGA VI<br>
	optional: RIO scan interface -> I/O data placed into local memory on RT controller. 
> Can we generate data from RT controller to place in the local memory and let FPGA read from it?

- An example. [LabVIEW procedure: Make your first RT application](https://www.youtube.com/watch?v=I43pZm0SeCQ&t=1133s)
  - RT main.vi Running. 
  - PC main.vi connect RT main.vi through variables. Control and read. 

## Use FIFO (First-In-First-Out) to communicate between real time controller and FPGA
[Reference Video](https://www.youtube.com/watch?v=Nr8q5VW-mXI)
- FIFO can be made of registers (flip-flops) or BRAM (Block RAM). Registers mean small data since the flip-flops inside FPGA are precious. BRAM can operate a larger data. 
- FIFO has width and length. Think about output a video or stream media. 
- Golden rules: Never write to a full FIFO (overflow). Never read from an empty FIFO (underflow). 
- Shared clock makes things easier.
- Figure out how to write code using AR/AF/Empty/Full flags.
- Never rely on FIFO level count.
- FIFO can be created in three ways: Instantiation, inference (recommended), GUI tools. 
- First Word Fall Through is great. [ref](http://www.deathbylogic.com/2015/01/vhdl-first-word-fall-through-fifo/) "The main difference between standard FIFOs and FWFT FIFOs are that, as the name describes, the first byte written into the FIFO immediately appears on the output"
### FIFO in sbRIO
- Data communication in LabVIEW FPGA falls into two categories: interprocess and intertarget. Interprocess communication generally corresponds to sharing data between two or more loops on the FPGA target. 
> Intertarget is what we need here. 

To do that, there are two methods: front panel controls and indicators, or DMA FIFOs. Both require using the FPGA Interface functions on the host VI to interact with the FPGA.
#### Front Panel Controls and Indicators
If you only need to transfer the latest data to / from a host VI.

Read/Write nodes are good candidates for transferring multiple pieces of information between the FPGA and host processor given their relatively low overhead. 

### Debugging
- Error code 50400. Occured in invoke method "FIFO.write".
[reference](https://knowledge.ni.com/KnowledgeArticleDetails?id=kA00Z000000kG75SAE)<br>
  - It has something to do with the timeout configuration. When the timeout is set a positive integar, there is the error code 50400. It disappeared when set to -1, but the program would get stuck at iteration 69. 
  - The reason is that FIFO is overflowed. 

- I got confused about the size definition in FIFO. There are some different "depths" in FIFO. 
  - "Requested Number of Elements". As in the project interface -- FIFO (right-click) -- FIFO properties -- General
  - The array size that we write to FIFO
  - Evoke method. FIFO. write. There is a property "empty elements remaining". 
> In my first understanding, the empty elements remaining should be equal to requested number - the array size we write to FIFO. But in the program debugging, it's not. Why is that?<br>
> Answer here. 
  - When you create the FIFO, you need to specify the elements you are gonna transfer ("requested number of elements"). Sure the number has a limit based on the memory. In our case, the number upper limit is 524293. (Note that below this number, the actual number of elements would be a little higher than the requested. e.g. 1000 -> 1029). 
  - For the "empty elements remaining", it is what we thought it would be. In the question I said it's not because I changed the requested depth in the configuration. 
  - But do we need to configure its depth? And what's the difference of this "requested depth" and "requested number of elements" during creation? 
  - Now everything makes sense.    

## MIO and ADC 
[what is MIO Multifunction Input Output](https://www.ni.com/en-us/support/documentation/supplemental/16/specifications-explained--ni-multifunction-i-o--mio--daq.html)<br>
- I guess we could read the analog input directly. But something is wrong now. When I connect the AI0-11 to the output of modules, their values are changing wiredly. 

