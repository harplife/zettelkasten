# Laser Image Projector

"I built a projector" :
- Design and implementation of an FPGA-controlled RGB laser projection system with closed-loop galvanometer control and automatic geometric calibration.


## References
- [How a laser show projector works - FesixGermany](https://www.youtube.com/watch?v=57RMK1En_yc)
- [DLP & LCD & Laser PROJECTOR - How They Work + TEARDOWN - Electronoobs](https://www.youtube.com/watch?v=U-HXgM9wdpY)
- [ESP32 Laser Projector with stepper motors | StanleyProjects.com - StanleyProjects](https://www.youtube.com/watch?v=w1O48Ysdiiw)
- [$2 vs $200,000 Projector - Linus Tech Tips](https://www.youtube.com/watch?v=JAPMSoM6U7w)
- [DIY Laser Show with ESP32 Laser DAC | StanleyProjects.com - StanleyProjects](https://www.youtube.com/watch?v=9YASnlB_t_U)
- [DIY Laser Image Projector (100ft+ Range!) - Ben Makes Everything](https://www.youtube.com/watch?v=fEPicBSYeNQ)
- [DIY Laser Projector - Built from an old hard drive - Ben Makes Everything](https://www.youtube.com/watch?v=u9TpJ-_hBR8)
- [How laser projectors work - X-Laser USA](https://www.youtube.com/watch?v=jscpGsmAEmE)


## System Diagram

![[Laser Projector - System Diagram.png]]

![[Pasted image 20260731091949.png]]

## Related Engineering Topics

|Area|Examples|
|---|---|
|Electronics|Laser diode drivers, power regulation|
|Analog Circuits|Current control, feedback loops|
|Embedded Systems|MCU or FPGA control|
|Digital Design|Image generation, timing|
|Signals|Raster/vector scanning waveforms|
|Control Systems|Mirror positioning feedback|
|Electromagnetics|Laser propagation, optics|
|Optics|Beam shaping, lenses, focusing|
|Programming|Image processing and rendering|


## Levels of Build

### Level 1 : Basic
- RGB laser modules
- Galvanometer mirrors
- STM32 or ESP32
- Simple vector graphics


### Level 2 : Intermediate
- grayscale control
- image interpolation
- animation
- automatic calibration
- brightness compensation
- geometric correction


### Level 3 : Advanced
- MEMS mirror scanning
- FPGA video pipeline
- HDMI input
- laser modulation
- real-time image scaling
- optical correction
- color balancing


## Subsystems

Laser Projector
│
├── Power Electronics
├── Laser Drivers
├── Optical System
├── Beam Combining
├── Beam Steering
├── Motor/MEMS Control
├── FPGA or MCU
├── Image Processing
├── Signal Generation
├── Feedback Control
├── Mechanical Design
├── Thermal Management
└── Safety System

### Laser Source
- Red diode
- Green diode
- Blue diode

With independent current drivers.

### Driver Electronics
Constant-current drivers with:
- temperature protection
- modulation input
- over-current protection


### Beam Combining
Use dichroic mirrors to combine
- red
- green
- blue
into one beam.


### Beam Steering

#### Galvanometers


#### MEMS mirrors


### Controller
Tasks include
- image storage
- mirror control
- PWM
- laser modulation

Examples:
- STM32
- RP2040
- FPGA
- TI C2000

### Software
Desktop software could
- load images
- convert to scan paths
- stream data
- adjust brightness


## Possible Extensions


| Extension                 | Description                                                                                                                   |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Automatic Focus           | Automatically adjust focus by measuring projection distance                                                                   |
| Keystone Correction       | Correct for angled projection                                                                                                 |
| Color Calibration         | Automatically balance RGB intensity by measuring color  output using a sensor                                                 |
| Closed-Loop Galvo Control | Instead of open-loop mirror movement, measure mirror position and use PID control (whatever that means)                       |
| Speckle Reduction         | Laser projectors suffer from speckle. Research methods include : vibrating diffusers, wavelength diversity, and polarization. |


## FPGA Video Pipeline

1. Receive HDMI
2. Frame Buffer
3. Raster Generation
4. Mirror Control
5. Laser Modulation


## Challenges

- Synchronizing mirror movement with laser intensity
- Preventing image distortion
- Maintaining linear scan speed
- Thermal management
- Eye safety
- Precision alignment


## Cost Estimate

- Basic : $300~600
- Intermediate : $700~1200
- Advanced : $1500+


## Laser Safety

Because visible lasers can pose eye hazards, incorporate safety features such as:
- using low-power laser modules where practical,
- enclosed beam paths during alignment,
- beam stops and interlocks,
- emergency shutdown circuitry,
- compliance with your university's laboratory safety policies.


## Required Skills/Knowledge

**Measurement**
- Digital multimeter
- Oscilloscope
- Bench power supply
- Function generator

**Electronics**
- Breadboard
- Soldering station
- Logic analyzer

**Software**
- KiCad
- LTspice
- MATLAB or Python
- C/C++
- Git

**Mechanical**
- CAD (Fusion 360 or SolidWorks)
- 3D printing

**Optics**
- Optical mounts
- Mirrors
- Lenses
- Alignment targets


### Knowledge-by-Course

| Course                                            | Major knowledge gained                                                 | Projector subsystem(s)                               | Example applications                                                   |
| ------------------------------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------- | ---------------------------------------------------------------------- |
| **ECE 211 - Circuit Analysis II**                 | AC analysis, transients, filters, resonance                            | Power distribution, analog signal conditioning       | RC filters, regulator stability, resonance analysis                    |
| **ECE 282 - Digital Systems Design**              | Logic design, FSMs, FPGA fundamentals, memory                          | Digital controller, image timing, frame buffer       | Scan controller, timing generator, FPGA implementation                 |
| **MATH 355 - Engineering Mathematics**            | Differential equations, Laplace transforms, Fourier analysis, matrices | System modeling, signal analysis, calibration        | PID analysis, mirror dynamics, geometric correction                    |
| **ECE 326 - Electronic Circuits I**               | Transistors, op-amps, analog feedback, current regulation              | Laser drivers, analog interfaces, sensor electronics | Constant-current laser driver, photodiode amplifier                    |
| **ECE 340 - Electromagnetics**                    | Maxwell's equations, EM waves, reflection, refraction                  | Optical system                                       | Laser propagation, lenses, mirrors, polarization                       |
| **ECE 351 - Signals and Systems**                 | Sampling, convolution, Fourier transforms, LTI systems                 | Image generation, waveform synthesis                 | Scan waveforms, anti-alias filtering, signal processing                |
| **ECE 352 - Probability & Statistics**            | Noise analysis, estimation, statistical inference                      | Calibration, testing, quality assurance              | Brightness calibration, measurement uncertainty                        |
| **ECE 365 - Control Systems**                     | Feedback, PID, stability, frequency response                           | Mirror control, autofocus, thermal regulation        | Closed-loop galvanometer control, laser power regulation               |
| **ECE 341 - Electromechanical Energy Conversion** | Motors, magnetic actuators, electromechanical systems                  | Beam steering hardware                               | Galvanometers, voice-coil or electromagnetic MEMS actuators            |
| **ECE 375 - Introduction to Communications**      | Digital communications, interfaces, error detection                    | Video input and external communications              | HDMI/USB interfaces, wireless control, firmware updates                |
| **IE 106 - Engineering Problem Solving**          | Engineering design process, requirements, optimization                 | Entire project lifecycle                             | Requirements definition, trade studies, project planning               |
| **IE 345 - Engineering Economics Analysis**       | Manufacturing, quality, cost, production planning                      | Product realization                                  | PCB assembly planning, optical alignment procedures, manufacturability |
| **ECE 436 - Digital Signal Processing**           | Advanced digital hardware concepts                                     | High-speed digital processing                        | FPGA architecture, memory pipelines, real-time processing              |
| **ECE 476 - Electronic Circuits II**              | Advanced signal processing/communications                              | Image and signal processing                          | Digital filtering, spectral analysis, efficient data transfer          |
| **ECE 482 - Microprocessor System**               | Embedded computing and system integration                              | Embedded controller                                  | RTOS, DMA, peripheral control, firmware architecture                   |
| **ECE 484 - Digital VLSI Design**                 | Advanced electronic system design                                      | System integration and optimization                  | Hardware integration, debugging, reliability engineering               |


### Knowledge-by-Self
- Engineering tools
- Electronics tools
- Programming
- Optics
- Mechanical design
- Project management

#### Electronics CAD
need to learn:
- Schematic capture
- PCB layout
- Component footprints
- Design rules
- Ground planes
- Differential routing
- Power routing

Recommended software:
- **KiCad** (free)
- Autodesk Fusion Electronics (formerly Eagle)

Example progression:
```
LED flasher
↓
Arduino shield
↓
Laser driver PCB
↓
Galvo controller PCB
↓
Complete projector motherboard
```


#### Mechanical CAD
Laser projectors require
- mounting lasers
- mounting mirrors
- lens holders
- enclosures
- cooling
- alignment fixtures

Learn:
- sketches
- constraints
- assemblies
- tolerances
- sheet metal basics

Software
- Autodesk Fusion
- SolidWorks
- Onshape


#### PCB Manufacturing
Learn
- Gerber files
- assembly drawings
- BOMs
- pick-and-place files
- solder stencil generation


#### Soldering & Assembly
Learn
- through-hole soldering
- SMD soldering
- hot air rework
- microscope inspection
- connector crimping


#### Embedded Programming
Learn
- STM32
- ESP32
- RP2040

Topics
- timers
- DMA
- interrupts
- ADC
- DAC
- PWM


#### FPGA Development
Learn
- Verilog/SystemVerilog or VHDL
- Vivado or Quartus
- simulation
- timing analysis

Project examples
```
LED blinking
↓
VGA controller
↓
Frame buffer
↓
Laser scan generator
```


#### Python
Use it for
- automation
- calibration
- plotting
- testing
- image processing

Libraries
- NumPy
- SciPy
- OpenCV
- Matplotlib


#### MATLAB (or GNU Octave)
Learn
- plotting
- FFT
- filters
- simulations
- control systems


#### LTspice
Circuit Simulation

Examples
- op-amps
- MOSFETs
- filters
- regulators
- laser drivers


#### Image Processing
Learn
- grayscale
- RGB
- interpolation
- edge detection
- raster scanning
- vector graphics


#### Computer Vision
Possible additions
- autofocus
- automatic calibration
- keystone correction
- screen detection


#### Precision Mechanics
Learn
- tolerance stack-up
- alignment
- vibration isolation
- thermal expansion
- fasteners
- bearings


#### 3D Printing
Print
- brackets
- lens mounts
- laser holders
- electronics enclosures

Fusion → STL → print?


#### Version Control
Version control (Using Git)
- firmware
- PCB files
- CAD
- documentation


#### Technical Documentation
Learn to create
- block diagrams
- wiring diagrams
- schematics
- assembly drawings
- test plans
- design reports
- requirements documents


#### Project Management
Learn
- requirements decomposition
- milestones
- risk assessment
- issue tracking
- design reviews
- change control



#### Optical Design Software
Learn basic ray tracing with
- OpticStudio (Zemax) if your university provides access
- OpticsRayTracer (good for learning concepts)
- OSLO EDU (educational edition)

Topics
- ray tracing
- focal length
- beam expansion
- aberrations


#### Laser Safety
Understand
- laser classes
- eye hazards
- diffuse vs. specular reflections
- beam stops
- optical density (OD) of safety eyewear
- alignment procedures



#### Optics

Study
- lenses
- mirrors
- focal length
- numerical aperture
- diffraction
- Gaussian beams
- beam expanders

##### Geometric Optics
- lenses
- mirrors
- focal length
- magnification

##### Wave Optics
- interference
- diffraction
- polarization

##### Lasers
- stimulated emission
- coherence
- beam divergence
- Gaussian beams


##### Electro-Optics
- modulators
- laser diodes
- photodiodes
- beam steering


## Incremental Subprojects

|Stage|Project|Skills learned|
|---|---|---|
|1|LED flasher|Basic circuits|
|2|PWM LED brightness|Timers, microcontrollers|
|3|Constant-current driver|Analog electronics|
|4|Laser diode driver (low-power)|Current regulation, safety|
|5|Servo-controlled mirror|Motor control|
|6|Galvanometer driver|Control systems|
|7|XY laser drawing system|Embedded programming|
|8|Vector graphics projector|Timing, synchronization|
|9|RGB projector|Color mixing|
|10|Image projector|Full capstone|

