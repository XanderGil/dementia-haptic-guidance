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

Dementia is a growing medical challenge worldwide, especially due to the ageing population. One of the most dangerous symptoms associated with dementia and Alzheimer’s disease is wandering behaviour. Research from the Alzheimer’s Association shows that six out of ten people with Alzheimer’s disease will wander at least once during the progression of the disease [[1]](docs/references/). Many people incorrectly assume that wandering only occurs in the later stages of dementia, while in reality it can occur during any stage of the illness. Wandering behaviour has a broader definition than simply “running away”. It can include behaviours such as returning later than usual from a regular walk, forgetting how to get to familiar places, attempting to fulfil former obligations such as going to work, repeatedly trying to “go home” even while already being at home, or displaying restless pacing and repetitive movements [[1]](docs/references/). These situations can lead to dangerous outcomes, stress for caregivers, and loss of independence for the patient.

Current medical solutions mainly focus on monitoring rather than actively helping the person navigate independently. GPS trackers are commonly used to locate patients after they become lost. Although these systems improve safety, they still place a large responsibility on caregivers or family members, who must continuously monitor the patient’s location and intervene when necessary [[2]](docs/references/). This creates psychological stress and increases the burden on caregivers. Furthermore, healthcare systems are increasingly facing shortages of healthcare workers and caretakers. As a result, many people with early-stage dementia who are still physically capable of walking and living at home are often no longer allowed to walk independently outdoors. Although these individuals are still capable of carrying out many daily activities, occasional spatial disorientation makes unsupervised walking too risky. Consequently, they are frequently forced to remain indoors or can only go for walks under supervision.

In practice, this supervision is not always available. Family members are often unable to provide constant guidance due to work or other responsibilities, while professional caretakers and begeleiders are already in short supply. Because of this shortage, many people with dementia lose an important part of their independence and social freedom, despite still being physically active and benefiting greatly from regular walks and outdoor activity. This can negatively affect both their mental wellbeing and overall quality of life. This project aims to address these limitations by developing a wearable haptic guidance system that can actively guide the user back to a predefined safe location. The objective is to increase the autonomy of people with dementia while simultaneously reducing stress for caregivers and relatives. The system is specifically intended for people with Alzheimer’s disease or early-stage dementia who are still capable of living at home and walking independently, but who are no longer fully able to safely navigate outdoor environments on their own. By enabling safer autonomous walking, the system aims to help these individuals preserve their independence and daily routines for a longer period of time.

Haptic technology offers several advantages in this medical context. Traditional navigation systems often rely on visual maps, spoken instructions, or complex smartphone interfaces. However, people with dementia may struggle to process complex visual or auditory information, especially in stressful or unfamiliar situations. Haptic feedback provides directional guidance through the sense of touch using vibration motors. Research shows that tactile feedback can provide intuitive navigation support without requiring continuous visual attention [[3]](docs/references/). An important advantage of haptic feedback is that it does not block environmental sounds or overload the visual system, which is especially important for vulnerable users. Studies on haptic navigation systems have demonstrated that users can successfully navigate using only vibration-based directional cues and that haptic systems can improve spatial awareness and memory recall compared to conventional visual navigation methods.

The proposed system uses a “hot/cold” navigation principle. The device continuously compares two directions: the bearing toward the home location and the heading of the user based on GPS measurements. When the user moves in the correct direction, the vibrations become calmer. When the user deviates from the correct direction, the vibrations increase in intensity. This allows the user to receive simple and intuitive guidance without explicit verbal commands such as “turn left” or “turn right”, thereby reducing confusion and overstimulation.

Several studies have already investigated haptic navigation aids for visually impaired users and pedestrian navigation applications [[3]](docs/references/),[[4]](docs/references/). However, relatively little research has focused specifically on wearable haptic guidance systems for people with dementia. Existing dementia-related technologies mainly focus on tracking and monitoring rather than restoring independent navigation abilities. This project aims to contribute to this research gap by exploring whether simple wearable haptic feedback can provide a low-cost, intuitive, and non-invasive solution for safe autonomous navigation in people with dementia.



| Component                        | Quantity | Description                                                       | Example Product                                                    | Estimated Cost |
| -------------------------------- | -------: | ----------------------------------------------------------------- | ------------------------------------------------------------------ | -------------: |
| Microcontroller                  |        1 | Main controller handling sensor fusion, GPS, and haptic logic     | [Arduino Micro Arduino a000053]()                                  |           ~€24 |
| Haptic Driver                    |        2 | Drives the vibration actuators using I2C                          | [SparkFun Haptic Motor Driver - DRV2605L]()                        |      ~€10 each |
| Haptic Actuator (“Drake haptic”) |        2 | Vibrotactile feedback motors used for directional navigation cues | ERM/LRA haptic motors compatible with DRV2605L                     |    ~€5–10 each |
| I2C Multiplexer                  |        1 | Allows multiple I2C devices with identical addresses on one bus   | [Adafruit Multiplexer I2C TCA9548A]()                              |            ~€8 |
| GPS Module                       |        1 | Provides real-time geographic position and navigation data        | [Adafruit Ultimate GPS Breakout with GLONASS + GPS]()              |           ~€50 |
| Accelerometer/Gyroscope          |        1 | Measures acceleration and tilt for orientation estimation         | [GY-521 MPU-6050 3-assige gyroscoop en versnellingsmeter Set]()    |           ~€10 |
| Magnetometer                     |        1 | Measures Earth’s magnetic field for heading estimation            | [Adafruit Drieassige magneetmeter]()                               |           ~€10 |
| Breadboard                       |        1 | Rapid prototyping platform for temporary circuit assembly         | Standard half-size breadboard                                      |            ~€5 |
| Jumper wires                     |      ~40 | Electrical connections between modules                            | [Dupont Jumper Kabels 40 Stuks (Male-Male) 20cm Voor Breadboard]() |            ~€2 |
| USB Cable                        |        1 | Programming and powering the Arduino                              | Micro-USB cable                                                    |            ~€3 |
| Portable Power Supply            |        1 | Mobile power source for wearable operation                        | USB power bank (5V output)                                         |        ~€10–20 |
| Plastic Enclosure                |        1 | Housing for wearable electronics                                  | Generic plastic project box                                        |         ~€5–10 |

