## Multiphoton FLIM Microscope Control and Real-Time Analysis

### Overview

During my Master's thesis at the **International Iberian Nanotechnology Laboratory (INL)**, I developed the complete software control and data-analysis system for a nonlinear multiphoton fluorescence lifetime imaging microscope (MP-FLIM).

The system integrates hardware control, image acquisition, and real-time fluorescence lifetime analysis to enable high-resolution imaging of biological samples labelled with multiple fluorophores.

The project was developed within the **ExtreMED research project**, which focuses on ultrafast laser technologies for biomedical imaging.

---

### Problem

Multiphoton microscopy systems integrate several specialized devices that must operate in precise synchronization:

- femtosecond laser sources  
- galvanometric scanning mirrors  
- motorized microscope stages  
- photon detectors  
- time-correlated photon counting electronics  

Commercial microscope control software often lacks flexibility and cannot support custom experimental workflows or advanced real-time analysis.

The project required a **custom software platform** capable of:

- controlling multiple hardware devices
- performing synchronized scanning
- acquiring photon arrival data
- computing fluorescence lifetimes in real time
- providing an intuitive interface for researchers

---

### Solution

I designed and implemented a **modular software platform** for device control and real-time fluorescence lifetime analysis.

The system integrates:

- device communication and control
- scanning orchestration
- photon data acquisition
- fluorescence lifetime computation
- visualization and analysis tools

All automated workflows were implemented as **independent software packages**, allowing the system to remain modular and easily adaptable to new devices or experimental procedures.

---

### System Architecture

The software coordinates communication between the control computer and several microscope components.

Controlled hardware includes:

- laser shutter
- galvanometric scanning mirrors
- motorized XY scanning stage
- piezo Z-stage for depth scanning
- photon detectors
- TCSPC photon counting electronics

These components are synchronized to perform controlled scanning and real-time data acquisition.

**Architecture diagram**

<p align="center">
<img src="../assets/img/thesis_diagram.png" width="700">
</p>
<p align="center"><em>Figure 7. Software diagram </em></p>

---

### Device Control

Dedicated control modules were implemented for each microscope component.

These modules interact with the hardware using **manufacturer APIs and device libraries**, enabling:

- laser shutter control
- galvanometric mirror scanning
- stage positioning
- z-axis scanning for 3D imaging
- detector triggering
- synchronization with photon counting electronics

This demonstrates proficiency in integrating external hardware libraries into a unified software environment.

---

### Scanning and Image Acquisition

Image acquisition is performed through controlled scanning of the sample.

The software generates scanning trajectories and coordinates device motion during acquisition.

Implemented capabilities include:

- beam scanning using galvanometric mirrors  
- sample scanning using a motorized XY stage  
- configurable pixel dwell time  
- synchronized photon detection  
- automated scanning grid generation  

These scanning modes enable flexible imaging configurations depending on experimental needs.

---

### Real-Time Fluorescence Lifetime Analysis

Fluorescence Lifetime Imaging Microscopy (FLIM) measures the decay time of fluorescence emitted by molecules after laser excitation.

Photon arrival times are recorded using **Time-Correlated Single Photon Counting (TCSPC)** electronics.

The software processes these signals in real time by:

- building photon arrival histograms for each pixel
- fitting exponential decay curves
- extracting fluorescence lifetime parameters
- generating FLIM images during acquisition

This enables researchers to monitor fluorescence lifetime contrast while the experiment is running.

---

### Real-Time Visualization

The system provides several live visualizations during data acquisition:

- fluorescence intensity images  
- fluorescence lifetime maps  
- photon arrival histograms  
- lifetime distribution plots  

These visualizations provide immediate feedback and allow rapid evaluation of experimental results.

**Graphical user interface**

<p align="center">
<img src="../assets/img/thesis_gui.png" width="700">
</p>
<p align="center"><em>Figure 8. Graphical User Interface developed for the project </em></p>
---

### Data Processing

Several analysis tools were implemented within the software:

- exponential fitting of fluorescence decay curves
- lifetime histogram extraction
- lifetime component separation
- threshold filtering of low-count pixels
- generation of intensity and lifetime images

These tools allow the identification and separation of fluorophores based on fluorescence lifetime differences.

---

### Results

The system was successfully tested in laboratory experiments using multi-colour labelled cellular samples.

The developed platform enabled:

- automated microscope control
- synchronized image acquisition
- real-time fluorescence lifetime visualization
- differentiation of multiple fluorophores using a single detector

This demonstrates the effectiveness of integrating device control, real-time data analysis, and visualization within a single software platform.


<p align="center">
<img src="../assets/img/thesis_data.png" width="700">
</p>
<p align="center"><em>Figure 9. Example of data extracted using the software </em></p>

---

### Technologies

- Python  
- Scientific computing and signal processing  
- Hardware API integration  
- Photon counting data analysis  
- Real-time data processing  
- Graphical user interface development  
- Scientific instrumentation control  

---

### Key Contributions

- Designed and implemented the **complete software control platform** for a multiphoton FLIM microscope.
- Integrated multiple microscope devices through their **manufacturer APIs**.
- Developed **real-time fluorescence lifetime analysis algorithms**.
- Implemented synchronized **scanning and photon acquisition workflows**.
- Built a **modular software architecture** enabling easy adaptation to new hardware and experiments.
- Developed a **graphical interface** for microscope control and live data visualization.
