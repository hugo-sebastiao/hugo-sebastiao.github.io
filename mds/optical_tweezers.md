# Projects
## Automation of Optical Tweezers Data Acquisition

**Python-based automation platform for optical tweezers experiments integrating computer vision, hardware control, device APIs, and automated measurement workflows.**

Optical tweezers use focused laser beams to manipulate microscopic particles and are widely used in experiments such as DNA or RNA stretching and protein droplet studies.

These experiments are often performed manually, requiring researchers to continuously control the instrument and extract data during each run.

I developed software to automate protein droplet experiments, allowing measurements to run autonomously based on predefined user parameters.

### Problem
Optical tweezers experiments required continuous manual control and data extraction, limiting experimental throughput and requiring researchers to remain at the instrument for long periods.

### Solution
Developed a software system capable of controlling the optical tweezers setup and automatically executing experiments based on user-defined parameters. Multiple automation workflows were implemented and integrated into a single application with a graphical user interface.

To improve maintainability and adaptability, the automated workflows were organized into modular software packages, making the system easier to modify, extend, and reuse.

A unified software layer was implemented to coordinate heterogeneous hardware devices through their vendor APIs, enabling centralized control of the experimental setup.

### Impact
Automated nearly the entire experimental workflow, significantly reducing the need for continuous user intervention and allowing researchers to perform other tasks while measurements were running.

During experimental use and testing, the system achieved an average throughput of approximately **20 data points per hour** across fusion, sedimentation, and rheology measurements, including droplet detection, capture, and preparation.

---

Some visual examples have been simplified or anonymized to respect institutional data policies. The focus of this project description is the software architecture and automation workflows.


### Droplet Detection
Reliable droplet detection was required for full automation. I developed and trained a **YOLO-NAS–based computer vision model** capable of detecting droplets in the camera feed and distinguishing them from debris or other artifacts.

An automation workflow was built around this model to:

- detect droplets automatically  
- extract their center pixel coordinates  
- convert image coordinates into motor positions  
- enable automated droplet pickup using the laser trap  

---

### Automated Droplet Capture
An automated routine was implemented to capture droplets detected in the visual field (Fig. 1). The algorithm determines whether a droplet is already trapped in the laser beam. If not, the system moves the motorized stage to the droplet position and captures it with the optical trap.

This process continues until all required laser paths contain droplets. The system also ensures that only droplets above a **user-defined minimum radius** are selected.


<p align="center">
  <img src="../assets/img/droplet_detection.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figur 1. AI model to detect and extract dropelt positions</em></p>

---

### Measurement Workflows
Several measurement routines were implemented and made selectable through the graphical user interface (Fig. 2). These included:

- fusion experiments  
- sedimentation measurements (Fig. 3), (Fig. 4)
- rheology measurements  

Each routine could be repeated a user-defined number of times for the same droplet before discarding it and repeating the process with a new droplet set.


<p align="center">
  <img src="../assets/img/general_diagram_ot.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 2. General Workflow Diagram</em></p>

<p align="center">
  <img src="../assets/img/sedimentation_workflow.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 3. Example of sedimentation workflow </em></p>

<p align="center">
  <img src="../assets/img/high_low_sed.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 4.  Example of data obtained from the workflow </em></p>

<p align="center">
  <img src="../assets/img/fusion_time.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 5.  Time performing a fusion with automation software for protein A </em></p>

<p align="center">
  <img src="../assets/img/sed_time.png" alt="Droplet detection" width="700">
</p>

<p align="center"><em>Figure 6.  Time performing a sedimentation with automation software for protein A </em></p>

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


