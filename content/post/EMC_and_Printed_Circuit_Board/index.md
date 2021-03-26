---
title: Printed Circuit Board Tech. - Blog
date: 2021-03-22
math: true
diagram: true
image:
  placement: 3
  # caption: 'Image credit: [**John Moeses Bauan**](https://unsplash.com/photos/OGZtQF8iC0g)'
---
> "Reviewers ridiculed it and consumers spurned it. Nevertheless, as is often with Microsoft products, persistence eventually made Windows better and dominant."

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

## References
[1] Montrose, M.I., 2004. EMC and the printed circuit board: design, theory, and layout made simple (Vol. 6). John Wiley & Sons.