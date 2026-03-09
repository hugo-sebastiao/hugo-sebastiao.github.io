## Automation of Optical Tweezers Data Acquisition

**Role:** Software Developer / Automation Engineer  
**Focus:** Computer vision, hardware integration, workflow automation  
**Environment:** Optical tweezers experimental platform

**Python-based automation platform for optical tweezers experiments integrating computer vision, hardware control, device APIs, and automated measurement workflows.**

**The platform unified droplet detection, hardware coordination, experiment execution, and data generation into a modular system capable of running optical tweezers measurements with minimal user intervention.**

Optical tweezers use focused laser beams to manipulate microscopic particles and are widely used in experiments such as DNA or RNA stretching and protein droplet studies.

These experiments are often performed manually, requiring researchers to continuously control the instrument and extract data during each run.

At the University of Dresden, I developed software to automate protein droplet experiments, allowing measurements to run autonomously based on predefined user parameters.

### Problem
Optical tweezers experiments required continuous manual control and data extraction, limiting experimental throughput and requiring researchers to remain at the instrument for long periods.

### Solution
I designed and implemented the complete automation software platform for the optical tweezers setup, integrating computer vision, device control, experiment orchestration, automated measurement routines, and graphical user interaction into a single system.

To improve maintainability and adaptability, the workflows were organized into modular software packages, making the system easier to modify, extend, and reuse.

A unified software layer was implemented to coordinate heterogeneous hardware devices through their vendor APIs, enabling centralized control of the experimental setup.

### Impact
The platform automated nearly the entire experimental workflow, replacing continuous manual operation with autonomous droplet detection, capture, and measurement execution while researchers could focus on other tasks.

During experimental use and testing, the platform achieved an average throughput of approximately **20 data points per hour** across fusion, sedimentation, and rheology measurements, including droplet detection, capture, and preparation.

---

Some visual examples have been simplified or anonymized to respect institutional data policies. The focus of this project description is the software architecture and automation workflows.

### Droplet Detection
Reliable droplet detection was required for full automation. I developed and trained a **YOLO-NAS–based computer vision model** capable of detecting droplets in the camera feed and distinguishing them from debris or other artifacts.

An automation workflow was built around this model to:

- detect droplets automatically  
- extract their center pixel coordinates  
- convert image coordinates into motor positions  
- enable automated droplet pickup using the laser trap  

<p align="center">
  <img src="../assets/img/droplet_detection.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 1. Droplet detection using the trained YOLO-NAS model. Detected droplets were used to extract positions for automated pickup.</em></p>

---

### Automated Droplet Capture
An automated routine was implemented to capture droplets detected in the visual field. The algorithm determines whether a droplet is already trapped in the laser beam. If not, the system moves the motorized stage to the droplet position and captures it with the optical trap.

This process continues until all required laser paths contain droplets. The system also ensures that only droplets above a **user-defined minimum radius** are selected.

This routine formed the core experimental control loop of the platform, linking computer vision output to automated motor positioning and trap loading.

---

### Measurement Workflows
Several measurement routines were implemented and made selectable through the graphical user interface. These included:

- fusion experiments  
- sedimentation measurements  
- rheology measurements  

Each routine could be repeated a user-defined number of times for the same droplet before discarding it and repeating the process with a new droplet set.

Similar workflow patterns were implemented across fusion, sedimentation, and rheology routines, allowing the same software framework to support multiple experimental protocols.

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
  <img src="../assets/img/high_low_sed.png" alt="Example sedimentation output" width="700">
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

### Logging and Traceability
The software allowed the user to define where experimental data should be stored during acquisition. In addition to measurement results, relevant system and experiment information was recorded in log files to ensure traceability and reproducibility.

---

### Safety Constraints
To prevent device collisions, a safe operating region was implemented within the control software. This ensured that automated movements remained within safe boundaries and prevented hardware damage caused by incorrect positioning.

---

### Microfluidics Integration
For reliable measurements, water must remain between the optical tweezers objectives and the sample. This process was automated by integrating a **syringe pump**, which managed water removal and eliminated the need for manual intervention.

---

### Device Integration
The software automatically connected to the devices that compose the optical tweezers setup, including motors, cameras, syringe pumps, and other hardware components.

Communication and control were implemented using the available **device APIs and hardware libraries**, allowing the system to coordinate all components programmatically from the main software interface.

A **socket-based server architecture** was used to initialize, connect, and manage the devices within a unified control environment.

---

### Technologies

- Python  
- GUI development  
- Computer vision  
- YOLO-NAS  
- Hardware control  
- Device APIs and libraries  
- Socket communication  
- Scientific data processing  
- Automation workflows  
- Modular software design  

---

### Key Contributions

- Designed and developed the main automation software for optical tweezers experiments  
- Developed a unified software layer to coordinate heterogeneous hardware devices through their vendor APIs  
- Structured automation workflows into modular software packages for easier maintenance and adaptation  
- Trained and integrated a YOLO-NAS model for droplet detection  
- Implemented automated droplet capture and measurement workflows  
- Integrated multiple hardware devices into a unified control system  
- Implemented logging, safety constraints, and microfluidics support  

This project combined computer vision, hardware API integration, modular software design, and automated experimental workflows into a unified research software platform.
