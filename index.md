# Hugo Sebastião

## Scientific Software for Custom Instruments and Lab Automation

I help research labs and deep-tech teams build reliable software for custom instruments, automated experiments, and hardware-integrated research workflows.

My work covers instrument control, device integration, computer vision, data acquisition, automated workflows, AI-driven analysis, and real-time analysis. Especially where experiments are still too manual, systems are fragile, or multiple devices need to work together reliably.

I have built software for optical tweezers, multiphoton FLIM microscopy, physiological sensing, and rehabilitation robotics, including systems used in real laboratory environments.

**Available for freelance projects in scientific software, instrument automation, and custom acquisition systems.**

**Need help? <a href="#contact">Get in touch</a>.**

<p class="top-links">
  <a href="#projects">Projects</a>
  <span> | </span>
  <a href="#services">Services</a>
  <span> | </span>
  <a href="#who-i-work-with">Who I Work With</a>
  <span> | </span>
  <a href="#about">About</a>
  <span> | </span>
  <a href="#contact">Contact</a>
</p>

---

## Why teams hire me

**Do you have an experimental workflow that still depends on too many manual steps? I help research teams turn fragile, time-consuming procedures into reliable software-driven workflows.**

I work at the intersection of software engineering and experimental research. I help when instrument software needs to do more than function as a prototype: it needs to coordinate hardware reliably, support acquisition and analysis, remain maintainable, and be usable by scientists in day-to-day work.

I am particularly useful when teams are dealing with:

- software that only works when the original developer is there
- instruments that require too many manual steps
- fragile integrations between cameras, stages, detectors, lasers, and analysis code
- research prototypes that are hard to extend or trust
- custom workflows that need to become reliable internal tools
- multi-device systems that need to work together predictably
- research codebases that have become difficult to maintain

---

<h2 id="services">Services</h2>

I can help with:

- building or improving control software for custom laboratory instruments
- integrating cameras, stages, detectors, lasers, and third-party device APIs
- automating experimental workflows to reduce manual effort and improve throughput
- developing real-time data acquisition, monitoring, and analysis pipelines
- applying computer vision and machine learning to microscopy and lab automation tasks
- creating scientific Python applications and custom GUIs for internal research use
- refactoring research code into maintainable, testable software
- troubleshooting fragile instrument software and improving reliability

Typical projects include:

- connecting multiple hardware components into a single software workflow
- automating manual experimental procedures
- stabilizing and extending research software developed during prototyping

---

<h2 id="who-i-work-with">Who I Work With</h2>

I typically work with research and R&D teams building or operating custom scientific instruments, including research labs, core facilities, deep-tech startups, and automated experimental platforms.

---

<h2 id="projects">Selected Work</h2>

### Optical Tweezers Experiment Automation

Developed a Python-based automation platform for optical tweezers experiments, integrating computer vision, hardware control, and automated measurement workflows into a modular system capable of running experiments with minimal user intervention.

The software unified droplet detection, hardware coordination, experiment execution, and data generation in a single workflow-oriented platform designed for real experimental use.

**Highlights**

- YOLO-NAS droplet detection
- automated droplet capture
- modular workflow design
- integrated hardware control
- automated measurement execution
- computer vision-guided experiment logic

**Outcome**  

Reduced hands-on operator involvement and made optical tweezers measurements more repeatable through workflow automation.

<p align="center">
  <img src="assets/img/sed_time.png" alt="sedimentation data" width="30%">
  <img src="assets/img/fusion_time.png" alt="fusion data" width="30%">
  <img src="assets/img/hig_low_sed.png" alt="protein comparison data" width="30%">
</p>
<p align="center"><em>Figure 1. Example data automatically collected and processed by the optical tweezers automation platform, including sedimentation and fusion measurements.</em></p>

Developed in a research environment at Technical University of Dresden.

[Read more →](mds/optical_tweezers.html)

---

### Multiphoton FLIM Microscope Control Software

Developed control software for a multiphoton fluorescence lifetime imaging microscope, integrating device control, synchronized scanning, TCSPC acquisition, and real-time lifetime analysis into a unified software environment.

The system was built to coordinate multiple hardware and acquisition components while providing live visualization and analysis during operation.

**Highlights**

- device API integration
- synchronized scanning
- TCSPC data acquisition
- real-time fluorescence lifetime visualization
- hardware-coordinated acquisition workflow
- scientific GUI development

**Outcome**  

Enabled synchronized measurement and live lifetime analysis in a single software environment used in day-to-day microscope operation.

<p align="center">
  <img src="assets/img/thesis_data.png" alt="FLIM data example">
</p>
<p align="center"><em>Figure 2. Example output generated during automated FLIM acquisition and analysis.</em></p>

Developed for real laboratory use at INL – International Iberian Nanotechnology Laboratory.  
Base software remains in use.

[Read more →](mds/FLIM.html)

---

### Autonomous Rehabilitation Robotics (Ongoing)

Developing a research pipeline for autonomous lower-limb rehabilitation based on AI-driven surrogate models of musculoskeletal dynamics and robotics-integrated control.

The project combines biomechanical modeling, predictive software workflows, and robotic control logic to support future rehabilitation systems for passive mobilization scenarios.

**Highlights**

- musculoskeletal modeling
- surrogate model development
- biomechanical simulation workflows
- robotics-integrated control logic
- model-based prediction pipeline
- scientific software for rehabilitation systems

**Outcome**  

The long-term objective is a software-guided robotic system capable of supporting autonomous lower-limb mobilization through model-based control.

Developed in a research collaboration between Clausthal University of Technology and HAWK Göttingen.

[Read more →](mds/musculoskeletal.html)

---

## Additional Projects

### Custom Pulse Measurement System

Developed a custom pulse measurement system from scratch using an Arduino and an optical finger sensor.

The project focused on extracting heart rate from the red-light sensor signal alone, requiring signal acquisition, software processing, and heartbeat detection logic.

**Highlights**

- Arduino-based sensor integration
- physiological signal acquisition
- heartbeat extraction from optical sensor data
- signal processing for noisy real-world measurements
- custom software for pulse detection and analysis

**Outcome**  

Built a working end-to-end prototype that strengthened my experience in instrumentation, signal processing, and real-time physiological data analysis.

---

## Technical Stack

**Core stack:** Python • NumPy/SciPy • OpenCV • PyQt/PySide • hardware APIs • serial/socket communication • scientific GUIs • real-time analysis • automation workflows

Additional experience with C/C++, MATLAB, JavaScript, signal and image processing, synchronized acquisition, multiprocessing, modular architecture, logging, testing, and reproducible scientific software development.

---

<h2 id="about">About</h2>

I have a background in biomedical engineering and scientific software, with experience building software at the interface of instrumentation, automation, and scientific data analysis.

My work has included software for microscopy, optical tweezers, rehabilitation robotics, and hardware-integrated experimental systems where reliability, usability, and maintainability matter in daily operation.

I am particularly interested in projects involving:

- custom instruments
- microscopy and imaging systems
- automated experiments
- device coordination and acquisition
- research software that has grown complex or difficult to maintain

I bring both software engineering and research context to these projects: integrating hardware, handling real-time constraints, building maintainable systems, and creating tools scientists can rely on.

[Read more →](mds/AboutMe.html)

---

<h2 id="contact">Contact</h2>

If you need help with instrument control, device integration, workflow automation, or research software that has become difficult to maintain, send me a short description of your setup and the problem you are trying to solve.

Helpful starting points include:

- what instrument or system you are working with
- which hardware or devices are involved
- what the current bottleneck or software problem is
- whether you need troubleshooting, improvement of an existing system, or a new tool built

I take on short consulting engagements, targeted software improvements, and end-to-end development of custom research tools.

LinkedIn: [linkedin.com/in/hugo-mvs-sebastiao](https://www.linkedin.com/in/hugo-mvs-sebastiao)

Email: [hugo.sebastiao.work@gmail.com](mailto:hugo.sebastiao.work@gmail.com)
