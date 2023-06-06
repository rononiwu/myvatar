# E2E Avatar system

## High level design
### Functional Requirements
### Personas
1. User 1
2. User 2
### Scenario
#### Output
1. As User 1, I want to view an avatar belonging to User 2 in its basic form(Without sensory input).
2. As User 1, I want to view an avatar belonging to User 2 along with sensory information.
3. As User 2 I want to hear Audio from User 1
4. As User 2 I want to hear Audio from User 1 translated to my default language.
![Alt avatar-system-architecture-diagram](./images/architecture.svg)

### Input / Output
The input / output component should have all or some of the following capabilities.
1. **Sensors:** Capture real-time sensory data from the user. 
2. **Displays:** Rendering of avatar(s).
3. **Audio systems:** Capture and play back audio in various formats.
4. **Haptics**: Play back of sensory data.
4. **Encoder / Decoder:** Encode data coming from the sensors and audio systems. Decode data coming back into the system into formats that can be rendered by the display and played back by the audio system. In the case of haptic enabled systems, this should also encode and decode haptic data. 
5. **Real-time Transport (RTP):** A real-time transport protocol that powers communication between the input/output systems and external services. 

### Services
**Front-end Services:** This service provides user management and security.
**Rendering Services:** 
**Audio:** This service manages audio data and language translation. It should also contain an AI engine that utilizes voice signatures for each user to generate transalted audio. This will help provide an enriched user experience.
**Telemetry:** Management of telemetry data coming from devices and services. This services should be capable of ingesting data streams and performing real-time analytics.

### Data
**Mapping Tool:** Enable simplified data storage and retrieval. 
**Blob Store:** Storage of binary data from sensors.
**File storage:** Storage of audio and image data. Telemetry data can also be stored here. 
**Relational Database:** Storage of relational data such as user information and links to data in file and blob storage. 

### Choice of tech stack
    - Programming for Real-time applications
## Telemetry service
## Language Translation service / 3p tool?
## Rendering Service ?
    - https://github.com/google/filament

## Deep dive & non-functional requirements
## Challenges

## Unknowns

## Risks 
## Extended design
**Admin service:** This service should provide operational capabilities to monitor and manage the entire set of capabilities.
**Avatar Marketplace:** Provide capabilities for Users to design avatars and monetizer their designs.
**Develper tools:** Provides tools for developers to build on and extend the capabilities of the current system. These tools should include
    * External API's to manage and customize avatars. 
    * Open source libraries with which Avatars can be exported and utilized in other systems with similar capabilities.
    * SDK's that enable utilization
## Conclusion

