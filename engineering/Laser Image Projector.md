# Laser Image Projector


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

