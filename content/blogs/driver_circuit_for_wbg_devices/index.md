---
title: Power Electronics
summary: Trying to understand and figure out good designs for driving GaN HEMT / SiC MOSFET.
date: 2021-03-22
math: true
diagram: true
tags:
- EE
image:
  placement: 3
---
> "Reviewers ridiculed it and consumers spurned it. Nevertheless, as is often with Microsoft products, persistence eventually made Windows better and dominant."
# PCB Technique
Discussion about the PCB design and EMC (Electro-Magnetic Compatibility) never stopped. The thing we need to do seems quite simple, find the three elements of the interference: Source, Propagation path, and Load. And then break them down. Though, the principles are important. You don't want to create a monster with some rigid rules. "The devil is in the detail."

Here, this blog would record some essential information to illustrate the nature of a good design of PCB. Besides, some resources from *Youtube* or some forums may help. 

Meanwhile, since the blogger majored in Power Eletronics, this blog might have a closer relationship to it than the others. Surely, we would also try our best to explain the high-frequency electronics well.

## Overview
In this section, we would give an overview of respectively EMC, PCB and the bond between. 

### Electromagnetic Compatibility (EMC)
- When we talk about EMC...<br>
  - Regulations: not only on **Emissions** but also **Susceptibility (Immunity)**
  - RFI (Radio Frequency Interference)
  - ESD (ElectroStatic Discharge) *Under the immunity requirement.*
  - Power Disturbances. Analog and digital devices respond differently. Digital circuits are affected by spikes on the power system (EFT and lightning), as well as failure due to excessively high or low voltage levels. Analog devices generally operate on voltage levels, which may be degraded by a disturbance changing the reference level of the system's power source.
  - Self-Compatibility.   
- Element - Propagation Path
  - Direct radiation from source to receptor
  - Direct RF energy radiated from the source transferred to AC mains cables or signal/control cables of the receptor
  - RF energy radiated by AC mains, signal, or control cables from source to receptor
  - RF energy conducted by common electrical power supply lines or by common signal/control cables 
- Coupling Mechanism (for each propagation path)
  - Conductive (Low-Frequency More likely)
  - Electromagnetic (High-Frequency more likely)
- When we talk about interference
  - Frequency. Frequency domain <-> time domain. 
  - Amplitude.
  - Time. Periodic, or only certainly cycles?
  - Impedance. Source, receptor, and transmission. 
  - Dimensions. 
- Causes of system-level EMI
  - Improper use of containment measures. (Metal vs. plastic)
  - Poor design, implementation and grounding of cables or connectors.
  - Incorrect PCB layout. 
    - clocks and periodic signal trace routing
    - stackup arrangement of the PCB and signal routing layer allocation
    - selection of components with high spectral RF energy distribution
    - common-mode and differential-mode filtering
    - ground loops
    - insufficient bypassing and decoupling

### Printed Circuit Board
- Structure of the board
- available development softwares
- process of production

### EMC inside PCB
> EMI is often the result of **exceptions** to the normal rules of passive component behavior. "When is a capacitor not a capacitor?"
<img src = "img/2021-03-26-10-11-58.png">  

## Special Topics
- Cross talk
- Impedance and signal reflection

# Semiconductor switching and Driving Issues
> When talking about ~MHz applications of GaN, we are always using soft-switching techniques. <br>

> Is this true? Why is that? What happens if we want to use hard-switching in MHz occasion?

We will start from the technical support of GaN Systems Inc.

## (GaN Systems Inc.) Official Application Notes
- Zero reverse recovery of GaN HEMT leads to lower switching loss and less EMI noise. (page 9 in GN001)
- Smaller output capacitance results in lower switching loss and easier ZVS. 
> They assume us adopting or wanting to adopt ZVS. 

### Other options

### monolithic integration (Navitas Inc.)
> and not a multi-chip combination of a silicon driver and a gallium nitride power device.  


> This idea is super cool. It's a pity that Navitas doesn't have a 100-V product line, otherwise I would really want to give it a try. 

## GaN HEMT Driver Design Comparison: Optocoupler vs. SI8274
### ACPL-P346-000E
> 2.5-Amp Output Current Power, GaN and SiC MOSFET Gate Drive Optocoupler with Rail-to-Rail Output <br>

> Rail-to-rail” implies that the signal swings all the way to supply voltage levels on both the positive and negative rails.<br>
> In this case, it means the on-voltage is VCC and off-voltage is VEE.

#### Specifications
- Propagation Delay Time to High Output Level Typ. 55 ns 
- Propagation Delay Time to Low Output Level Typ. 55 ns 
- Pulse width distortion Max. 50 ns 
- Propagation Delay Difference between any two pairs -50 ~ 50 ns 
> Should we set up a deadtime at least 50 ns to avoid this difference?  

- Rise Time Typ. 8 ns (Max. 30 ns)
- Fall Time Typ. 8 ns (Max. 30 ns)



### SI8274
 
#### Specifications
- propagation delay time 30 - 45 ns 
- Pulse width distortion (SI8274 with low jitter) 14-19 ns 
- Programmed dead time 20 ns
- Rise time 10.5 ns 
- Fall time 13.3 ns 

### Comparison
- Those two drivers all mentioned that they are ideal for GaN. So pick any of them would work for normal GaN operation. 
- ACPL-P346-000E has a slightly better rising/falling time performance. However, Si8274 has a more accurate and steady dynamic. (The ranges are s are narrow.)
- Surprisingly, they all have a significant propagation delay (or it is common in power semiconductor drivers.) We might be able to ignore this phenomenon at low frequency, however, it would become a pain in the ass when we pushing the frequency high. 
- ACPL has a on-resistance of 0.3 $\omega$, and according to its max current output ability, the minimum of external gate resistor can be calculated:$R_{g, min} = (V_{CC} - V_{EE}) / I_{OUT} - R_{DSON} = 3.7\omega$



## Driver Circuit Structure: Should we put driving circuit and power circuit on the same board?
- "Extremely costly and large interference if put driver and power stage on the same PCB." --- Dr. Li experienced. 
- Designing them on the same board would give us a theoretically smaller tray inductance (1~10 nH). No other difference any more. However, it would be really hard to obtain this aim (tons of work on layout design.) 
- **Conclusion:** Even though this is the main stream in industries (after all the number of boards would affect significantly the final cost.), it won't hurt if we design the driver circuit as a daughter board.

### Gate Drive Consideration[5]
- capacitance of gate drive interface should be kept low.
- gate drive power supply should be rated for at least 50 V/ns 






## References
[1] Montrose, M.I., 2004. EMC and the printed circuit board: design, theory, and layout made simple (Vol. 6). John Wiley & Sons.<br>
[2] H. W. Ott, ‘Electromagnetic Compatibility Engineering’, p. 871.<br>
[3] [application notes of GaN Systems Inc.](https://gansystems.com/design-center/application-notes/)<br>
[4] [Breaking Speed Limits with GaN Power ICs](https://navitassemi.com/breaking-speed-limits-with-gan-power-ics/)<br>
[5] [Design Recommendations for SiC MOSFETs](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=2ahUKEwjB7K_spMT0AhXej3IEHW09AzYQFnoECAIQAQ&url=https%3A%2F%2Fwww.microsemi.com%2Fdocument-portal%2Fdoc_download%2F136647-micronote-1826-microsemi-sic-mosfets-design-recommendations&usg=AOvVaw277z80u34b3XLi0y6IAzu5)<br>
[6] [TI review of GaN related questions](https://training.ti.com/gan-demystified-frequently-asked-questions)

# Craftsmanship
## Handle components with ease
### Naming of chips
> Knowing how the chips are named is much more important than we thought. It could save us much time searching for chips. <br>
Products from popular companies are listed here. 
#### Texas Instrument
- Operational Amplifiers<br>
OPA[number of channels][Mode]xx
  - number of channels: skip when there is only one channel. Therefore, 3 digits mean one channel OPA. 4 digits means more than 1 chnannel. 
  - Mode: 1xx-FET, 2xx-


# When writing a paper
- In the paper, you are not telling reader what you did exactly, you are selling them what's worth publishing. For example, you made a big machine to test your idea. Even though you may have spent a lot of money and energy on this machine, but finally what's the most important thing in this paper is how you organize and implement your idea. People don't need and don't want to know how you built this machine. 
- When writing, ask yourself, constantly: 
  - What am I trying to say? 
  - Have I said it?
  - Is it clear to someone encountering the subject for the first time?
-

