# dementia-haptic-guidance
<div align="justify">
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

### The Cognitive Roots of Wandering
Dementia is an escalating global health priority, with the World Health Organization estimating 78 million cases by 2030 [[1]](https://pmc.ncbi.nlm.nih.gov/articles/PMC8869749/). One of the most dangerous symptoms is wandering behaviour, affecting approximately 60% of people with Alzheimer’s Disease (AD) [[2]](https://pmc.ncbi.nlm.nih.gov/articles/PMC6234917/). Wandering is often an intentional effort to reach a destination, but because of cognitive decline, patients frequently lose the ability to retrace their steps. This leads to "critical wandering": if a patient is not found within 24 hours, half of them suffer serious injury or death due to accidents, dehydration, or exposure [[2]](https://pmc.ncbi.nlm.nih.gov/articles/PMC6234917/).

The primary cause of this disorientation is the degeneration of the hippocampus-entorhinal cortex (HP-EC) network [[3]](https://www.mdpi.com/2077-0383/14/2/579). This network manages the transition between two navigation frames: allocentric (mental maps based on landmarks) and egocentric (self-referential cues like "left" and "right"). Early-stage AD patients lose their allocentric capacity first, becoming "anchored" to their immediate body-centered view [[3]](https://www.mdpi.com/2077-0383/14/2/579). Consequently, they lose the spatial flexibility required to navigate even familiar environments once they are out of direct sight of their home.

### Why Tracking Is Not Enough
Existing GPS navigation and tracking technologies already provide partial support for people with dementia by helping caregivers monitor a person’s location and improving safety during outdoor activities. Research has shown that GPS-based tracking systems can increase confidence in going outside independently and reduce caregiver stress and anxiety [[4]](https://pmc.ncbi.nlm.nih.gov/articles/PMC10852717/). However, these technologies primarily focus on passive monitoring rather than active assistance. While GPS trackers help locate a person after they become lost, they do not prevent wandering behavior or actively help users navigate independently in real time [[5]](https://www.ltcnews.com/articles/gps-trackers-for-dementia-safety-best-options-to-consider-in-2026). As a result, people with dementia often remain dependent on continuous caregiver supervision despite the presence of tracking technology. Furthermore, passive monitoring systems may raise ethical concerns regarding privacy and autonomy [[6]](https://www.intpsychogeriatrics.org/article/S1041-6102(24)02073-8/fulltext).

Due to shortages in professional healthcare workers, a growing share of dementia care responsibilities falls on informal caregivers, particularly family members. Caring for a person with dementia often requires continuous supervision and assistance with daily activities, which can place a significant emotional, physical, and financial burden on caregivers. Family caregivers frequently experience stress, anxiety, isolation, and burnout as they try to balance caregiving with their personal and professional lives [[7]](https://www.mdpi.com/2227-9032/13/20/2633). At the same time, many people with dementia remain physically capable of activities such as walking independently, but cannot safely do so without supervision because of cognitive impairment and risks such as disorientation or wandering. This loss of independence can reduce the quality of life of both patients and their families, as patients experience increased restrictions while caregivers face continuous responsibility and limited personal freedom [[8]](https://www.nccdp.org/the-impact-of-dementia-on-caregivers-and-family-members/).

### Haptic Feedback as a Solution
Haptic technology offers a unique advantage by providing directional cues through the sense of touch, bypassing the overstimulated visual and auditory channels. Research suggests that haptic feedback can reduce cognitive demand compared to purely auditory navigation cues, particularly in tasks that require continuous environmental awareness and spatial orientation [[9]](https://www.nature.com/articles/s41598-024-79845-7).

Previous research on haptic navigation systems has shown that tactile guidance can support independent navigation while maintaining environmental awareness and minimizing distraction. Because users do not need to continuously look at a screen or process spoken instructions, haptic systems encourage a more natural “heads-up” navigation style [[10]](https://www.researchgate.net/publication/235005436_Guiding_Blind_People_with_Haptic_Feedback). Real-world implementations such as HapticWorks [[11]](https://haptic.works/) further demonstrate how wearable haptic navigation can successfully guide visually impaired users through intuitive directional tactile feedback.

### Project Objective and System Mechanics
This project proposes a wearable haptic navigation system designed to help people with early-stage dementia safely return to a predefined safe location, such as their home or care facility. Instead of relying on complex turn-by-turn navigation instructions, which can be cognitively demanding for individuals with dementia, the system provides simple and intuitive directional feedback through touch.

The system continuously compares the user’s current heading with the bearing toward the safe location. When the user moves outside a predefined safe radius, the device activates and provides directional haptic guidance: vibrations on the left indicate that the user should adjust toward the left, while vibrations on the right indicate a correction toward the right. The intensity of the vibration increases proportionally to the angular deviation from the correct direction, making larger navigation errors more noticeable. When the user is moving in the correct direction toward the safe location, the system emits a calm confirmation pulse. If the user continues moving away from the target location or in a strongly incorrect direction, the device switches to a more urgent warning pattern to alert the user.

To ensure reliable perception for elderly users with reduced tactile sensitivity, the system uses Drake Haptic Actuators (TacHammers), which generate strong, sharp, and highly perceivable tactile feedback through solid-state magnetic suspension technology. By replacing cognitively demanding visual or auditory navigation with intuitive haptic cues, the system aims to support safer independent mobility while reducing caregiver stress and supervision demands.


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
This section describes the technical approach and system integration required to build the haptic guidance prototype. The system architecture is divided into four main layers: sensing, processing, decision, and haptic output.

### System Overview
The prototype is built around an Arduino Micro and combines GPS positioning, orientation sensing, and haptic feedback to guide a user back to a predefined safe location.The system continuously compares:

- the bearing → the direction toward the safe location
- the heading → the direction the user is currently facing

Based on the difference between these two values, the system activates haptic feedback on the left or right side of the wearable.

### Step 1: Core Components
The following components form the basis of the prototype:

- Arduino Micro → central controller
- GY-NEO6MV2 GPS module → location tracking
- LIS3MDL magnetometer → heading detection
- MPU6050 IMU → tilt and roll compensation
- 2x Drake TacHammer actuators → haptic feedback
- 2x DRV2605L drivers → actuator control
- TCA9548A I2C multiplexer → allows both DRV2605L modules to work simultaneously

The Arduino processes all sensor data and controls the haptic guidance logic.

### Step 2: Determining Direction (Heading vs Bearing)
The navigation system works by comparing the user’s heading with the bearing toward the safe location. Initially, heading was calculated only using GPS coordinates. However, this approach proved too inaccurate and too slow at walking speed because GPS position updates are limited and contain small positional errors.

To solve this issue, an LIS3MDL magnetometer was added to function as a digital compass. This sensor continuously measures the Earth’s magnetic field to determine the direction the user is facing. The magnetometer initially produced incorrect readings because of magnetic interference and sensor offsets. To improve accuracy:

- hard-iron offsets were calibrated
- soft-iron distortion was compensated

After calibration, the compass achieved a directional accuracy of approximately ±10°, which was considered acceptable for this application.

### Step 3: Tilt and Roll Compensation
Because the device is worn on the body, the sensor will not always remain perfectly horizontal while the user is walking. This can distort the compass heading calculated from the magnetometer and result in incorrect left/right navigation feedback.

To improve heading stability, the system combines the 3-axis magnetic field data from the LIS3MDL with the 3-axis accelerometer data from the MPU6050. The accelerometer acts as a gravity reference, allowing the software to estimate the tilt of the device in real time.

Tilt compensation is performed using vector projection. First, the magnetic field vector is projected onto the gravity vector:
`
float dot = mx * ax + my * ay + mz * az;
`

The component aligned with gravity is then removed:
```cpp
float hx = mx - dot * ax;
float hy = my - dot * ay;
float hz = mz - dot * az;
```

This produces a horizontal magnetic vector that is less affected by tilt and roll. The final heading is then corrected for local magnetic declination and smoothed using an exponential filter to reduce sensor noise and prevent unstable haptic feedback

### Step 4: Haptic Feedback System
The Arduino continuously combines the GPS position, compass heading, and tilt-compensated orientation data to determine the direction of the predefined safe location. Using the TinyGPS library, the system calculates both the distance and the bearing toward the target location.

The navigation logic compares the user’s current heading with the target bearing and calculates the angular error between both directions. Based on this error, the system activates directional haptic feedback through the left and right TacHammer actuators. The feedback follows a threshold-based steering logic:

- Correct direction (≤ 25°) → gentle confirmation pulse on both actuators
- Small deviation (≤ 60°) → soft vibration on the side the user should turn toward
- Large deviation (≤ 120°) → stronger repeated vibration on the corresponding side
- Wrong direction / moving away → strong warning pattern on both actuators

This approach was chosen because directional haptic feedback provides a simpler and less cognitively demanding navigation method than spoken turn-by-turn instructions.

### Step 5: Driver Communication
The TacHammer actuators are controlled using DRV2605L haptic driver boards. Since both driver boards use the same fixed I2C address, a TCA9548A I2C multiplexer was integrated into the system design from the start. This allows the Arduino to communicate with each driver independently and control the left and right actuator separately.

### Step 6: Software integration
The Arduino software continuously:
1. reads GPS coordinates
2. calculates the bearing to the safe location
3. determines the current heading
4. compares heading and bearing
5. activates the correct haptic feedback pattern

Raw compass measurements can fluctuate slightly because of sensor noise and small body movements while walking. Without filtering, these fluctuations could cause the haptic feedback to rapidly switch between left and right directions.

To improve stability, exponential smoothing was applied to the heading data. Instead of instantly using every new heading measurement, the software gradually blends new values with previous ones:
``cpp
float diff = normalizeAngle(heading - smoothHeading);
smoothHeading = wrap360(smoothHeading + diff * HEADING_SMOOTH_FACTOR);
``




### Step 1: Core Components
The core of the system is the Arduino Micro, chosen for its compact size and comprehensive communication interfaces (I2C and Serial) suitable for wearable applications. The logic dictates that the system must continuously calculate two vectors: the bearing (the direct line from the current location to the preset home location) and the heading (the direction the user is currently facing or moving). To deliver clear, percussive tactile feedback without causing overstimulation, Drake TacHammer were selected as actuators.


### Step 2: Determining Direction (Heading vs Bearing)
Initially, the system was designed to rely solely on the GY-NEO6MV2 GPS module for both position and heading data. However, relying on successive GPS coordinates to determine heading proved too inaccurate and slow at pedestrian walking speeds. To resolve this, an LIS3MDL magnetometer was integrated to determine the absolute direction. To ensure data reliability, the magnetometer was calibrated to eliminate hard-iron and soft-iron offsets, achieving a reliable heading accuracy within an acceptable range of ~10°C. Furthermore, because the user wears the device around the waist, the sensor is rarely perfectly horizontal, which would normally distort compass readings. To solve this, an MPU-6050 IMU was incorporated to provide real-time tilt and roll compensation, ensuring stable orientation tracking regardless of arm positioning. Both auxiliary sensors communicate with the Arduino Micro via the shared I2C bus.

### Step 3: Haptic Output Subsystem Construction
Driving the Drake TacHammers requires precise waveform generation, which is handled by two Adafruit DRV2605L Haptic Drivers. A hardware constraint arose because both DRV2605L modules share the same hardcoded I2C address, preventing them from being used simultaneously on the standard Arduino I2C bus. To resolve this, an Adafruit TCA9548A I2C Multiplexer was integrated. The Arduino sends routing commands to the multiplexer, which then forwards the specific vibration profiles to either the left or the right actuator independently.

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
</div>
