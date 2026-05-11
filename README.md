# dementia-haptic-guidance

This project is developed by students of KU Leuven and develops a wearable haptic navigation system for people with young dementia who experience spatial disorientation and wandering behaviour. The prototype is activated when a person moves beyond a certain radius from a pre-set point; this point could be the person’s home or a care centre. 

## Team Members
- Matts Lanting
- Xander Gilbert

## Repository Structure

- docs/ → project documentation
- code/ → Arduino code
- hardware/ → schematics and CAD
- media/ → images and videos

## Documentation

- [Introduction](docs/introduction.md)
- [Supplies](docs/supplies.md)
- [Methods](docs/methods.md)
- [Discussion](docs/discussion.md)
- [Conclusion](docs/conclusion.md)
- [References](docs/references.md)

# Introduction

Dementia is a growing medical and social challenge, especially as the ageing population increases. One common and dangerous symptom is spatial disorientation, which can lead to wandering behaviour. People with dementia may leave their home or care facility and become unable to find their way back. This can result in dangerous situations, anxiety for the person with dementia, and increased stress for family members and caregivers. The Alzheimer’s Association states that six in ten people living with dementia will wander at least once, and many do so repeatedly. :contentReference[oaicite:0]{index=0}

Existing solutions mainly focus on monitoring rather than active guidance. GPS trackers and location-sharing devices can help caregivers find a person after they have become lost, but they do not necessarily support the person in returning independently. Research on GPS tracking for dementia care also shows practical limitations, such as battery life, localisation problems, technical difficulties, privacy concerns, and barriers to adoption by users and caregivers. :contentReference[oaicite:1]{index=1} :contentReference[oaicite:2]{index=2}

This project addresses this gap by developing a wearable haptic guidance system. Instead of giving complex visual or spoken instructions, the device uses vibration feedback to guide the user back to a pre-set home location. Haptic feedback can provide a unique advantage because it is subtle, non-visual, and does not block environmental sounds. This makes it suitable for navigation support in situations where visual or auditory feedback may be distracting, confusing, or overstimulating. Previous research on wearable haptic navigation systems shows that vibration-based feedback can be used to communicate directional or spatial information in an intuitive way. :contentReference[oaicite:3]{index=3} :contentReference[oaicite:4]{index=4}

The proposed system uses GPS data to compare the user’s current movement direction with the direction toward the home location. Based on the difference between these directions, the system provides haptic feedback through vibration motors. The goal is not to give explicit instructions such as “turn left” or “turn right”, but to create a simple “hot/cold” feedback principle. When the user moves in the correct direction, the feedback becomes calmer; when the user moves away from the correct direction, the vibration becomes stronger.

The main knowledge gap addressed by this project is the lack of simple, low-cost and user-friendly systems that actively guide people with dementia rather than only tracking them. By combining GPS-based navigation with wearable haptic feedback, this prototype aims to explore whether subtle tactile cues can support safer and more independent movement for people who experience spatial disorientation.
