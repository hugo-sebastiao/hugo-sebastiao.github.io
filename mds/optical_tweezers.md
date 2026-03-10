---
layout: default
title: Optical Tweezers Experiment Automation
---

## Optical Tweezers Experiment Automation

**Role:** Software Developer / Automation Engineer  
**Focus:** Computer vision, hardware integration, workflow automation  
**Environment:** Optical tweezers experimental platform

**Problem**  
Optical tweezers experiments required continuous manual control, droplet selection, and manual data extraction, limiting throughput and requiring constant researcher supervision.

**Built**  
I developed a modular automation platform integrating droplet detection, hardware control, automated droplet capture, experiment workflows, structured data generation, and graphical user interaction.

**Outcome**  
Automated nearly the full experimental workflow and achieved approximately **20 data points per hour** across fusion, sedimentation, and rheology measurements.

**Stack**  
Python, computer vision, YOLO-NAS, hardware APIs, socket communication, GUI development, automation workflows

### Overview

At the **Technical University of Dresden**, I developed a Python-based automation platform for optical tweezers experiments, integrating computer vision, device control, experiment orchestration, and automated measurement workflows.

The system unified droplet detection, hardware coordination, automated capture, experiment execution, and data generation in a modular software platform capable of running measurements with minimal user intervention.

Optical tweezers use highly focused laser beams to manipulate microscopic particles. In this setup, experiments were typically performed manually, requiring researchers to continuously monitor the sample, operate the instrument, and extract data during each run. The goal of this project was to replace that manual workflow with a reliable and extensible automation system.

---

### Problem

The experimental workflow depended on continuous manual control and manual data extraction, which reduced throughput and required researchers to remain at the instrument for long periods.

To automate the setup reliably, the software needed to:

- detect droplets reliably in live camera images
- distinguish valid droplets from debris and artifacts
- convert detections into stage movements
- coordinate multiple hardware devices through different vendor APIs
- execute measurement workflows automatically
- allow researchers to configure experiments through an accessible interface
- generate structured output data with minimal manual intervention

---

### Solution

I designed and implemented the automation software platform for the optical tweezers setup, integrating computer vision, device control, experiment orchestration, automated measurement routines, and graphical user interaction into a single system.

I organized the workflows into modular software packages so the platform could be maintained more easily and adapted to new hardware, measurement types, and experimental procedures.

A unified software layer coordinated heterogeneous hardware devices through their vendor APIs, enabling centralized control of the full setup.

---

### Impact

The platform automated nearly the entire workflow, replacing continuous manual operation with autonomous droplet detection, capture, and measurement execution while researchers could focus on other tasks.

During experimental use and testing, the system achieved an average throughput of approximately **20 data points per hour** across fusion, sedimentation, and rheology measurements, including droplet detection, capture, and preparation.

This reduced hands-on instrument time, increased experimental throughput, and made routine automated data generation more practical.

---

Some visual examples have been simplified or anonymized to respect institutional data policies. The focus of this project description is the software architecture and automation logic.

### Droplet Detection

Reliable droplet detection was a core requirement for full automation. I developed and trained a **YOLO-NAS-based computer vision model** capable of detecting droplets in the live camera feed and distinguishing them from debris and other artifacts.

An automation workflow was built around this model to:

- detect droplets automatically
- extract center pixel coordinates
- convert image coordinates into motor positions
- enable automated droplet pickup using the laser trap

<p align="center">
  <img src="../assets/img/droplet_detection.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 1. Droplet detection using the trained YOLO-NAS model. Detected droplets were used to extract positions for automated pickup.</em></p>

---

### Automated Droplet Capture

I implemented an automated routine to capture droplets detected in the visual field. The algorithm determines whether a droplet is already trapped in the laser beam. If not, the system moves the motorized stage to the droplet position and captures it with the optical trap.

This process continues until all required laser paths contain droplets. The software also ensures that only droplets above a **user-defined minimum radius** are selected.

This routine formed a core control loop of the platform, linking computer vision output directly to automated motor positioning and trap loading.

---

### Measurement Workflows

I implemented measurement routines for:

- fusion experiments
- sedimentation measurements
- rheology measurements

Each routine could be repeated a user-defined number of times for the same droplet before discarding it and repeating the process with a new droplet set.

I built a shared workflow framework that supported all three measurement types, allowing the same software architecture to be reused across multiple experimental protocols.

The overall automation workflow for droplet capture and measurements is shown below.

<p align="center">
  <img src="../assets/img/general_diagram_ot.png" alt="General optical tweezers workflow" width="700">
</p>

<p align="center"><em>Figure 2. High-level automation workflow for droplet capture and measurement routines.</em></p>

An example of the sedimentation-specific workflow is shown below.

<p align="center">
  <img src="../assets/img/sedimentation_workflow.png" alt="Sedimentation workflow" width="700">
</p>

<p align="center"><em>Figure 3. Automation workflow used for sedimentation measurements.</em></p>

The software also generated structured output data for downstream analysis.

<p align="center">
  <img src="../assets/img/hig_low_sed.png" alt="Example sedimentation output" width="700">
</p>

<p align="center"><em>Figure 4. Example output generated by the automated sedimentation workflow.</em></p>

The timing plots below illustrate the execution time of automated measurements for protein A.

<p align="center">
  <img src="../assets/img/fusion_time.png" alt="Fusion timing results" width="700">
</p>

<p align="center"><em>Figure 5. Time required to perform automated fusion measurements for protein A.</em></p>

<p align="center">
  <img src="../assets/img/sed_time.png" alt="Sedimentation timing results" width="700">
</p>

<p align="center"><em>Figure 6. Time required to perform automated sedimentation measurements for protein A.</em></p>

---

### Platform Engineering

To support reliable day-to-day operation, I also implemented several platform-level features:

- **logging and traceability** for experiment records and output paths
- **safety constraints** to keep automated movements within a safe operating region
- **microfluidics integration** through a syringe pump to maintain measurement conditions automatically
- **device integration** for motors, cameras, pumps, and other hardware components

Communication and control were implemented through available **device APIs and hardware libraries**, while a **socket-based server architecture** was used to initialize, connect, and manage devices within a unified control environment.

---

### Technologies

- Python
- GUI development
- computer vision
- YOLO-NAS
- hardware control
- device APIs and libraries
- socket communication
- scientific data processing
- automation workflows
- modular software design

---

### Key Contributions

- designed and developed the main automation software for optical tweezers experiments
- developed a unified software layer to coordinate heterogeneous hardware devices through their vendor APIs
- structured automation workflows into modular software packages for easier maintenance and adaptation
- trained and integrated a YOLO-NAS model for droplet detection
- implemented automated droplet capture and measurement workflows
- integrated multiple hardware devices into a unified control system
- implemented logging, safety constraints, and microfluidics support

### Engineering Challenges

Key challenges included reliable droplet detection in live microscopy images, translating image coordinates into physical stage movements, coordinating heterogeneous hardware through different vendor interfaces, and maintaining safe automated operation during repeated measurement cycles.
