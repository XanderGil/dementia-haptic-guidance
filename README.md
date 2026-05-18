# dementia-haptic-guidance

This project, developed by students at KU Leuven, focuses on the development of a wearable haptic navigation system for people with early-stage dementia who experience spatial disorientation and wandering behaviour. The prototype is activated when a person moves beyond a predefined radius from a safe location, such as their home or a care centre. Once activated, the system provides intuitive haptic guidance to help the user return safely, reducing the need for continuous supervision and allowing people with dementia to maintain a greater level of independence

## Team Members
- Matts Lanting
- Xander Gilbert

## Repository Structure

- docs/ → project documentation
- code/ → Arduino code
- hardware/ → schematics and CAD
- media/ → images and videos
- references/ → references


## Introduction

### The Global Burden of Dementia and Wandering
Dementia is an escalating global health priority, with the World Health Organization estimating 78 million cases by 2030 [[1]](https://pmc.ncbi.nlm.nih.gov/articles/PMC8869749/). One of the most dangerous symptoms is wandering behaviour, affecting approximately 60% of people with Alzheimer’s Disease (AD) [[2]](docs/references/). Wandering is often an intentional effort to reach a destination, but because of cognitive decline, patients frequently lose the ability to retrace their steps [[3]](docs/references/). This leads to "critical wandering": if a patient is not found within 24 hours, half of them suffer serious injury or death due to accidents, dehydration, or exposure [[2]](docs/references/).

### Neurobiological Basis of Spatial Disorientation
The primary cause of this disorientation is the degeneration of the hippocampus-entorhinal cortex (HP-EC) network [[4]](docs/references/). This network manages the transition between two navigation frames: allocentric (mental maps based on landmarks) and egocentric (self-referential cues like "left" and "right") [[5]](docs/references/). Early-stage AD patients lose their allocentric capacity first, becoming "anchored" to their immediate body-centered view [[4]](docs/references/). Consequently, they lose the spatial flexibility required to navigate even familiar environments once they are out of direct sight of their home.

Limitations of Current Care and TechnologyCurrent medical solutions and GPS technologies focus primarily on monitoring rather than active assistance. While active GPS trackers help locate a person after they become lost, they do not prevent wandering or help the user navigate independently [[6]](docs/references/). Furthermore, passive monitoring often raises ethical concerns regarding privacy and autonomy [[7]](docs/references/).

This lack of active support places an immense burden on informal caregivers. Globally, the median prevalence of caregiver burden is nearly 50%, leading to high levels of emotional distress, anxiety, and social isolation [[8]](docs/references/). Due to healthcare worker shortages, many physically capable patients are restricted to their homes to ensure safety, which significantly decreases their quality of life [[9]](docs/references/).

### Haptic Feedback as a Solution
Haptic technology offers a unique advantage by providing directional cues through the sense of touch, bypassing the overstimulated visual and auditory channels [[10]](docs/references/). Research indicates that for individuals with cognitive impairments, auditory instructions can result in a 22 times higher cognitive load than haptic pulses [[11]](docs/references/). Furthermore, haptic navigation has been shown to:
-Enhance Environmental Awareness: Users maintain a "heads-up" posture, focusing on their surroundings rather than a screen [[12]](docs/references/).
-Improve Spatial Memory: Route recall is often superior when using haptic cues compared to visual landmarks [[13]](docs/references/).

### Project Objective and System Mechanics
This project proposes a wearable haptic system that uses a bearing-based "hot/cold" principle to guide users back to a predefined safe location [[14]](docs/references/). Unlike turn-by-turn systems that require complex instruction-following, our system continuously compares the user’s heading (current direction) with the bearing (target direction) [[15]](docs/references/).

When the user moves toward the home point, the device provides a calm pulse; as they deviate, vibration intensity increases proportionally to the angular offset [[16]](docs/references/). To ensure effective perception in elderly users with diminished tactile sensitivity, the system utilizes Drake Haptic Actuators (TacHammers), which employ a solid-state magnetic suspension for sharp, percussive feedback [[17]](docs/references/). By restoring the ability to navigate safely and autonomously, the system aims to reduce caregiver anxiety and preserve the independence of people living with early-stage dementia.


## Supplies

| Component                                | Quantity | Description                                                       | Example Product                                                                                                                                                                                                            | Estimated Cost |
| ---------------------------------------- | -------: | ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------: |
| Microcontroller                          |        1 | Main controller handling sensor fusion, GPS, and haptic logic     | Arduino Micro  [https://store.arduino.cc/products/arduino-micro](https://store.arduino.cc/products/arduino-micro)                                                                                                         |         €24.10 |
| Haptic Driver (DRV2605L)                 |        2 | Drives the vibration actuators using I2C                          | Adafruit DRV2605L  [https://www.adafruit.com/product/2305](https://www.adafruit.com/product/2305)                                                                                                                         |     €6.81 each |
| Haptic Motor (Drake TacHammer)           |        2 | Vibrotactile feedback motors used for directional navigation cues | Titan Haptics TacHammer   [https://titanhaptics.com/product-category/tachammer/](https://titanhaptics.com/product-category/tachammer/)                                                                                     |       €45 each |
| I2C Multiplexer                          |        1 | Allows multiple I2C devices with identical addresses on one bus   | Adafruit TCA9548A  [https://www.adafruit.com/product/2717](https://www.adafruit.com/product/2717)                                                                                                                         |          €5.95 |
| GPS Module                               |        1 | Provides real-time geographic position and navigation data        | GY-NEO6MV2 GPS Module  [https://www.ebay.com/itm/403641520095](https://www.ebay.com/itm/403641520095)                                                                                                                     |          €5.68 |
| Accelerometer/Gyroscope (MPU-6050 6-DoF) |        1 | Measures acceleration and tilt for orientation estimation         | Adafruit MPU6050  [https://www.adafruit.com/product/3886](https://www.adafruit.com/product/3886)                                                                                                                          |         €11.09 |
| Magnetometer                             |        1 | Measures Earth’s magnetic field for heading estimation            | Adafruit LIS3MDL  [https://www.adafruit.com/product/4479](https://www.adafruit.com/product/4479)                                                                                                                          |          €8.52 |
| Breadboard                               |        1 | Rapid prototyping platform for temporary circuit assembly         | Mini Breadboard  [https://www.amazon.nl/AZDelivery-Mini-Breadboard-compatibel-Inclusief/dp/B07KKJSFM1](https://www.amazon.nl/AZDelivery-Mini-Breadboard-compatibel-Inclusief/dp/B07KKJSFM1)                               |          €4.44 |
| Jumper Wires                             |      ~40 | Electrical connections between modules                            | Male-to-male jumper wires   [https://www.amazon.nl/Jenalinng-breadboard-steekbruecken-draadbrueken-mannelijk/dp/B0GZ2XGRK6](https://www.amazon.nl/Jenalinng-breadboard-steekbruecken-draadbrueken-mannelijk/dp/B0GZ2XGRK6) |          €2.95 |
| USB Cable                                |        1 | Programming and powering the Arduino                              | USB cable                  [https://www.amazon.nl/DIGITUS-USB-2-0-kabel-USB-verbindingskabel/dp/B07CWTTX65](https://www.amazon.nl/DIGITUS-USB-2-0-kabel-USB-verbindingskabel/dp/B07CWTTX65)                                               |          €0.94 |
| Portable Power Supply                    |        1 | Mobile power source for wearable operation                        | USB power bank (5V output)                                                                                                                                                                                                 |         €10–20 |
| **Total Estimated Cost**                 |          |                                                                   |                                                                                                                                                                                                                            |  **~€170–180** |



## Methods

In this section, we describe the technical approach and system integration required to build the haptic guidance prototype. The system architecture is divided into four main layers: sensing, processing, decision, and haptic output.

### Step 1: System Architecture and Component Selection
The core of the system is the Arduino Micro, chosen for its compact size and comprehensive communication interfaces (I2C and Serial) suitable for wearable applications. The logic dictates that the system must continuously calculate two vectors: the bearing (the direct line from the current location to the preset home location) and the heading (the direction the user is currently facing or moving). To deliver clear, percussive tactile feedback without causing overstimulation, we selected Drake TacHammer actuators.

### Step 2: Sensor Integration (Localization and Orientation)
Initially, the system was designed to rely solely on the GY-NEO6MV2 GPS module for both position and heading data. However, relying on successive GPS coordinates to determine heading proved too inaccurate and slow at pedestrian walking speeds. To resolve this, an LIS3MDL magnetometer was integrated to determine the absolute direction. To ensure data reliability, the magnetometer was calibrated to eliminate hard-iron and soft-iron offsets, achieving a reliable heading accuracy within an acceptable range of ~10°C. Furthermore, because the user wears the device around the waist, the sensor is rarely perfectly horizontal, which would normally distort compass readings. To solve this, an MPU-6050 IMU was incorporated to provide real-time tilt and roll compensation, ensuring stable orientation tracking regardless of arm positioning. Both auxiliary sensors communicate with the Arduino Micro via the shared I2C bus.

### Step 3: Haptic Output Subsystem Construction
Driving the Drake TacHammers requires precise waveform generation, which is handled by two Adafruit DRV2605L Haptic Drivers. A hardware constraint arose because both DRV2605L modules share the same hardcoded I2C address, preventing them from being used simultaneously on the standard Arduino I2C bus. To resolve this, we integrated an Adafruit TCA9548A I2C Multiplexer. The Arduino sends routing commands to the multiplexer, which then forwards the specific vibration profiles to either the left or the right actuator independently.

### Step 4: Software Implementation and Decision Logic
The software architecture on the Arduino Micro is designed to continuously fuse sensor data, compute navigation vectors, and execute an intelligent haptic steering algorithm. The logic is divided into three primary subroutines.

#### Sensor Fusion & Tilt Compensation:
A magnetic compass is highly sensitive to tilt. To ensure accurate heading data while the user is walking, the software reads the raw 3-axis magnetic field from the LIS3MDL and the 3-axis acceleration from the MPU6050. Using vector projection, the accelerometer data acts as a gravity reference to mathematically compensate for the magnetometer's tilt. The resulting heading is then corrected for local magnetic declination and passed through an exponential smoothing filter to reduce sensor noise and prevent erratic haptic triggers.

#### Navigation Vectoring:
The TinyGPS library parses the incoming Serial NMEA sentences to extract the current latitude and longitude. The system continuously calculates the distance and the absolute bearing to the predefined safe zone (home radius).

#### Discrete Haptic Steering Algorithm:
Instead of a purely linear scaling of vibration, the decision layer calculates the angular error between the user's current heading and the target bearing. It then applies a threshold-based steering logic targeting the left or right actuator via the I2C multiplexer:
-> Forward/On-Track (Error <= 25°): A gentle, synchronous confirmation pulse on both actuators (doGentleConfirmation).
-> Slight Deviation (Error <= 60°): A light directional pulse on either the left or right actuator, prompting the user to correct their course.
-> Strong Deviation (Error <= 120°): A stronger, repeated pulse on the specific side the user needs to turn toward.
-> Wrong Direction / Moving Away: The system tracks consecutive errors and distance trends (movingAwayCounter, wrongDirectionCounter). If the user is walking away from the target or is completely turned around (Error > 120°), both actuators fire a strong, repeated warning pattern (doVeryWrongDirection).


## Discussion

### Addressing the Medical Challenge
The primary objective of this project was to develop an active, non-intrusive haptic guidance system to mitigate the risks of spatial disorientation and wandering in early-stage dementia patients. Overall, the prototype successfully demonstrated that a wearable device can actively steer a user back to a safe "home radius" without relying on complex visual or auditory instructions. By transitioning from passive GPS tracking to active tactile navigation, the system provides a strong proof-of-concept for preserving patient autonomy while reducing caregiver burden.

### Sensor Performance and Limitations
During testing, the sensor fusion approach proved critical, yet it highlighted specific hardware constraints. A notable limitation was the NEO-6M GPS module, which occasionally struggled to establish a reliable satellite connection quickly, especially in environments with obstructed views of the sky. Additionally, as noted during development, relying solely on the GPS to determine the user's heading was highly inaccurate at slow walking speeds. While integrating the LIS3MDL magnetometer and MPU6050 (for tilt compensation) successfully stabilized the orientation data, the system remains dependent on the initial GPS satellite lock to calculate the target bearing.

### Navigation Constraints ("Bird's-Eye" Limitation)
An unexpected conceptual limitation observed during testing is the system's reliance on direct line-of-sight mathematics. The current algorithm calculates the bearing "as the crow flies" (a straight bird's-eye line to the home coordinates). While mathematically accurate, this approach does not account for physical obstacles such as buildings, fences or complex street layouts. Consequently, the device might occasionally attempt to guide the user straight through impassable barriers. This highlights the necessity of implementing a street-level map API for future iterations.

### Haptic Interaction and Prototype Constraints
The iterative shift from a purely continuous "hot/cold" vibration mapping to a discrete, threshold-based steering algorithm (differentiating between slight and strong left/right deviations) significantly improved the interpretability of the feedback. The Drake TacHammers delivered sharp, distinct pulses that were easy to differentiate. However, from a hardware perspective, the current prototype faces physical limitations typical of breadboard assemblies. Bulky wiring and the risk of loose connections emphasize that significant ergonomic miniaturization, such as integration into a smartwatch form factor, is required before the system can be comfortably and reliably worn by elderly patients.


## Conclusion and Future Work

### Conclusion
The "Haptic Home Guidance for Dementia" prototype successfully demonstrates the viability of using active, tactile navigation to assist individuals experiencing spatial disorientation. By fusing standard GPS localization with tilt-compensated magnetometer readings, the system effectively overcomes the inaccuracies typical of low-speed pedestrian GPS tracking. The implementation of a discrete, threshold-based left/right haptic steering algorithm proved highly effective, providing intuitive directional cues without overwhelming the user's visual or auditory channels. Ultimately, this prototype validates the concept of transitioning from passive monitoring to active, autonomous guidance.

### Lessons Learned
For others building upon this work, several key technical and conceptual lessons emerged during development:

-> Sensor Fusion is Essential: Relying solely on GPS for heading calculation is inadequate for slow-moving pedestrians. Integrating a calibrated magnetometer and an IMU for real-time tilt compensation is strictly necessary, especially for a waist-worn device that is rarely perfectly horizontal.

-> Discrete vs. Continuous Feedback: We initially hypothesized that a continuous "hot/cold" proportional vibration would be intuitive. However, practical testing revealed that discrete, distinct patterned pulses (e.g., slight left vs. strong left) are significantly easier for a user to interpret while walking.

-> The "Bird's-Eye" Limitation: Calculating the bearing via direct line-of-sight mathematics is highly efficient for the microcontroller but ignores physical real-world obstacles like buildings or fences, highlighting the limits of coordinate-only navigation.

### Future Work
To evolve this prototype into a production-ready medical device, future development should focus on the following areas:

-> Smart Routing Integration: Upgrading the navigation logic from direct line-of-sight coordinates to an integrated map network API. This would allow the system to guide users safely via actual streets, sidewalks and intersections.

-> Ergonomic Miniaturization: The current breadboard setup must be compressed into an unobtrusive, fashionable smartwatch form factor. To improve bilateral feedback without physical discomfort, a dual-band system could be developed, utilizing a primary processing watch on one arm and a secondary Bluetooth-connected actuator band on the other.

-> Broader Non-Medical Applications: The core haptic directional technology developed in this project can be expanded to other fields. Potential applications include haptic GPS navigation integrated into car steering wheels (to reduce visual distraction for drivers) and advanced, discreet wayfinding tools for the visually impaired.
