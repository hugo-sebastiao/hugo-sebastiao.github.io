---
layout: default
title: Musculoskeletal
---

## Autonomous Rehabilitation Robotics

**Role:** Scientific Software Engineer / Research Software Developer  
**Focus:** Musculoskeletal simulation, automated dataset generation, surrogate-model pipeline, rehabilitation robotics  
**Environment:** Robot-assisted lower-limb rehabilitation

**Problem**  
Robot-assisted rehabilitation requires patient-specific predictions of biomechanical response and robot–limb interaction forces. Full musculoskeletal simulations can provide these outputs, but they are too computationally expensive for real-time use in a robot control loop. In addition, training surrogate models requires large datasets across many parameter combinations, and generating this data manually through repeated optimization runs is slow, labor-intensive, and difficult to scale.

**Built**  
I developed a musculoskeletal simulation and data-generation workflow for rehabilitation motions, including lower-limb model selection, prescribed motion generation, 6-DOF attachment wrench estimation, and a software package that automates optimizer sweeps across varying parameters for surrogate-model dataset generation.

**Outcome**  
Established the simulation backend for rehabilitation wrench estimation and surrogate-model training, while increasing automated data-generation throughput from approximately **10 to 20 simulation points per hour** and removing the need for continuous manual supervision during optimizer sweeps.

**Stack**  
OpenSim, OpenSimCreator, Python, musculoskeletal modeling, optimization workflows, automated parameter sweeps, surrogate-model pipeline design, rehabilitation robotics

### Overview

Safe robot-assisted rehabilitation requires estimates of biomechanical response and robot–limb interaction forces, but full musculoskeletal simulations are too computationally expensive for real-time control. At the same time, training surrogate models for faster prediction requires large datasets that are tedious to generate manually.

I developed a musculoskeletal simulation and automation workflow for this problem, including prescribed rehabilitation motion generation, 6-DOF tibia attachment wrench estimation, and an automated sweep pipeline for optimizer-based dataset generation.

The result was a reusable simulation backend for rehabilitation robotics and a faster, more scalable data-generation process, increasing throughput from approximately **10 to 20 simulation points per hour** without continuous user supervision.
---

### Problem

Rehabilitation for intensive care and paraplegic patients is physically demanding and time-intensive, while therapy capacity is constrained relative to rehabilitation need. Robotic support can help offload repetitive work, but safe control requires estimates of quantities such as robot–limb interaction wrench and internal biomechanical response.

Full musculoskeletal simulations can provide these outputs, but they are too slow for direct real-time deployment in a control loop. At the same time, surrogate models offer a path toward real-time prediction, but they require large training datasets spanning different motions, scales, ROM values, and passive parameters.

Generating that data manually would require repeatedly changing parameters, launching optimization workflows, and collecting outputs by hand. Each data point takes a long time, making the process slow, repetitive, and difficult to scale.

To support this project, the software workflow needed to:

- represent patient-specific variability such as scale, ROM, and passive parameters
- estimate therapy-relevant outputs for safe robot control
- support comparison of alternative wrench-estimation formulations
- generate consistent training data for future surrogate models
- automate parameter sweeps and optimizer runs
- prepare the workflow for validation against measured robot–limb forces

---

### Solution

I developed the musculoskeletal simulation backend around **OpenSim**, selected for flexibility, available model ecosystem, and suitability for simulation and optimization workflows under the project constraints. I then adapted the workflow for rehabilitation use by selecting a lower-limb model with extended ROM, generating prescribed rehab-like motions, and implementing initial 6-DOF attachment wrench estimation workflows for the tibia attachment interface.

In parallel, I developed an automation package that runs optimizer-based simulation sweeps autonomously while varying parameters across defined ranges. This package removes the need to manually edit inputs and launch each run by hand, making surrogate-model data generation faster and far less labor-intensive.

The result is a computational foundation that supports prescribed-motion simulation, estimation of passive response and attachment wrench, benchmarking of alternative estimation methods, and scalable automated dataset generation for surrogate-model training.

---

### Musculoskeletal Backend Selection

For the simulation backend, **OpenSim** was selected because it is open-source, widely used in the research community, and offers strong model availability and workflow flexibility for simulation and optimization.

For the lower-limb model, I selected **Catelli-high-hip-flexion V4.0**, derived from the Rajagopal model family and using the **Millard2012EquilibriumMuscle** formulation. This model was suitable because it supports larger rehabilitation-relevant ROM while preserving Hill-type muscle and tendon mechanics needed for passive-force analysis.

---

### Rehabilitation Motion Definition

As a proof of concept, the workflow focuses on **supine hip flexion with knee flexion**, a clinically relevant lower-limb mobilization exercise suitable for passive rehabilitation scenarios. Motion files are generated by prescribing hip and knee angle trajectories over time, providing consistent input motions for simulation and later parameter sweeps.

This establishes a controlled simulation input for evaluating how passive tissue response and attachment wrench vary with rehabilitation motion.

---

### Initial 6-DOF Attachment Wrench Estimation

A central goal of the project is to estimate the **6-DOF attachment wrench** at the robot–limb interface — three forces and three moments at the tibia attachment — during prescribed motion. This quantity includes the effects of gravity, inertia, and passive internal forces, making it directly relevant for safe robot support and control.

To explore robust estimation strategies, I implemented and evaluated several workflows, including constraint-based approaches, inverse-dynamics-style formulations, and optimization-based methods. The model was adapted in **OpenSimCreator** to support the frames, constraints, and actuators required for these alternatives.

---

### Constraint and Optimization Approaches

One class of tested methods used **constraint reactions**, where an external body attached at the limb interface mirrors the robot end-effector and allows reaction wrench estimation if the interface definition matches the physical interaction correctly. These approaches were feasible, but sensitive to frame definition, constraint setup, and interface modeling.

A second class of methods used **optimization-based estimation**, including **Computed Muscle Control (CMC)** and **MocoInverse**. In this formulation, a **SpatialActuator** is added at the attachment interface, and the optimizer solves for the time-varying 6-DOF wrench needed to track the prescribed motion while satisfying dynamics.

Among the tested approaches, this optimization-based strategy proved the most robust in practice. CMC was used as an initial feasibility workflow, while a MocoInverse-based pipeline is being developed for more principled full-motion consistency.

---

### Automated Dataset Generation for Surrogate Models

Training surrogate models requires large simulation datasets covering many combinations of motion and model parameters. Initially, this data-generation process depended on manually changing parameters, launching optimization runs, and collecting outputs, which made it both slow and time-consuming.

To address this, I developed a software package that automates the simulation sweep workflow: it modifies parameters, runs the optimizer autonomously, and gathers the resulting outputs into structured data for surrogate-model training.

This automation increased throughput from approximately **10 to 20 simulation points per hour**, while also removing the need for continuous manual supervision. In practice, this made dataset generation both faster and less labor-intensive, freeing time for analysis and further development.

---

### Passive Response and Training Data

The simulation workflow is also being used to identify outputs correlated with passive resistance, such as passive muscle stretch forces and other internal OpenSim quantities relevant to rehabilitation loading. This is important because passive internal loads are interconnected with the required 6-DOF attachment wrench.

Once the wrench-estimation workflow is validated, the same backend can generate consistent input–output data for surrogate-model training by sweeping across variables such as:

- motion profiles
- model scale
- ROM
- passive parameters
- attachment wrench outputs

This automated sweep pipeline is intended to provide the training data needed for real-time surrogate prediction in later phases of the project.

---

### Validation Workflow

A major next step is validation against experimental measurements. The planned protocol records measured 6-DOF wrench at the shin cuff together with kinematics, scales the model to the participant, aligns the attachment frame with the sensor, runs the optimizer on recorded motion, and compares predicted versus measured wrench in a common frame.

This validation step is essential before using the simulation outputs to train or rely on surrogate models for robot-assisted mobilization.

---

### Long-Term Objective

The long-term goal of the project is an autonomous rehabilitation robot that uses surrogate-model predictions inside the control loop to support safe, patient-specific mobilization in real time.

The simulation and automated data-generation workflow developed here provides the foundation for that next phase by supplying the training data and biomechanical outputs needed to build, validate, and integrate those surrogate models into the future control architecture.

---

### Project Status

**Delivered**
- OpenSim selected as the musculoskeletal simulation backend
- lower-limb model selected and adapted for rehabilitation ROM
- proof-of-concept rehabilitation motion generation implemented
- initial 6-DOF attachment wrench estimation workflow implemented for tibia attachment
- automated simulation sweep package developed for surrogate-model dataset generation

**In progress**
- passive-parameter estimation
- validation of 6-DOF wrench estimation
- benchmarking of alternative wrench-estimation formulations
- expansion of the automated sweep pipeline for larger dataset generation

**Next**
- automatic patient scaling workflow
- surrogate-model training and evaluation
- integration of surrogate predictions into the control loop
- robot integration and controlled validation demo

---

### Technologies

- OpenSim
- OpenSimCreator
- Python
- musculoskeletal modeling
- prescribed-motion simulation
- CMC
- MocoInverse
- SpatialActuator-based wrench estimation
- automated parameter sweeps
- surrogate-model data pipeline design

---

### Key Contributions

- selected and configured the musculoskeletal simulation backend for rehabilitation use
- identified a lower-limb model suitable for rehabilitation-relevant ROM and passive-force analysis
- generated prescribed rehabilitation motions for proof-of-concept simulation
- implemented initial workflows for estimating 6-DOF attachment wrench at the tibia interface
- adapted the model to support multiple wrench-estimation formulations
- developed a package for autonomous optimizer-based parameter sweeps
- doubled simulation data-generation throughput from approximately 10 to 20 points per hour
- established the simulation basis for validation and surrogate-model training

### Engineering Challenges

Key challenges included defining a physically meaningful robot–limb interface inside the model, estimating a reliable 6-DOF attachment wrench under prescribed motion, handling sensitivity to frame and constraint definitions, and scaling the workflow from individual simulations into automated dataset generation for surrogate-model training.

Another major challenge was reducing manual intervention in repeated optimization runs. I addressed this by automating parameter variation, simulation execution, and output collection, making the workflow faster, more reproducible, and less dependent on constant user supervision.
