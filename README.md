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

###The Global Burden of Dementia and Wandering
Dementia is an escalating global health priority, with the World Health Organization estimating 78 million cases by 2030 [[1]](docs/references/). One of the most dangerous symptoms is wandering behaviour, affecting approximately 60% of people with Alzheimer’s Disease (AD) [[2]](docs/references/). Wandering is often an intentional effort to reach a destination, but because of cognitive decline, patients frequently lose the ability to retrace their steps [[3]](docs/references/). This leads to "critical wandering": if a patient is not found within 24 hours, half of them suffer serious injury or death due to accidents, dehydration, or exposure [[2]](docs/references/).

###Neurobiological Basis of Spatial Disorientation
The primary cause of this disorientation is the degeneration of the hippocampus-entorhinal cortex (HP-EC) network [[4]](docs/references/). This network manages the transition between two navigation frames: allocentric (mental maps based on landmarks) and egocentric (self-referential cues like "left" and "right") [[5]](docs/references/). Early-stage AD patients lose their allocentric capacity first, becoming "anchored" to their immediate body-centered view [[4]](docs/references/). Consequently, they lose the spatial flexibility required to navigate even familiar environments once they are out of direct sight of their home.

Limitations of Current Care and TechnologyCurrent medical solutions and GPS technologies focus primarily on monitoring rather than active assistance. While active GPS trackers help locate a person after they become lost, they do not prevent wandering or help the user navigate independently [[6]](docs/references/). Furthermore, passive monitoring often raises ethical concerns regarding privacy and autonomy [[7]](docs/references/).

This lack of active support places an immense burden on informal caregivers. Globally, the median prevalence of caregiver burden is nearly 50%, leading to high levels of emotional distress, anxiety, and social isolation [[8]](docs/references/). Due to healthcare worker shortages, many physically capable patients are restricted to their homes to ensure safety, which significantly decreases their quality of life [[9]](docs/references/).

###Haptic Feedback as a Solution
Haptic technology offers a unique advantage by providing directional cues through the sense of touch, bypassing the overstimulated visual and auditory channels [[10]](docs/references/). Research indicates that for individuals with cognitive impairments, auditory instructions can result in a 22 times higher cognitive load than haptic pulses [[11]](docs/references/). Furthermore, haptic navigation has been shown to:
-Enhance Environmental Awareness: Users maintain a "heads-up" posture, focusing on their surroundings rather than a screen [[12]](docs/references/).
-Improve Spatial Memory: Route recall is often superior when using haptic cues compared to visual landmarks [[13]](docs/references/).

###Project Objective and System Mechanics
This project proposes a wearable haptic system that uses a bearing-based "hot/cold" principle to guide users back to a predefined safe location [[14]](docs/references/). Unlike turn-by-turn systems that require complex instruction-following, our system continuously compares the user’s heading (current direction) with the bearing (target direction) [[15]](docs/references/).

When the user moves toward the home point, the device provides a calm pulse; as they deviate, vibration intensity increases proportionally to the angular offset [[16]](docs/references/). To ensure effective perception in elderly users with diminished tactile sensitivity, the system utilizes Drake Haptic Actuators (TacHammers), which employ a solid-state magnetic suspension for sharp, percussive feedback [[17]](docs/references/). By restoring the ability to navigate safely and autonomously, the system aims to reduce caregiver anxiety and preserve the independence of people living with early-stage dementia.
