# Myvatar - An end-to-end Avatar system
## Deep-dive
Table of Contents
1. [Non-functional requirements](#non-functional-requirements)
    * [Security](#security)
    * [Reliability](#reliability)
    * [Input / Output stack](#inputoutput-stack)

### Non-functional requirements
#### **Security** 
Sensory data should be captured and transmitted in a secure manner. This data should also be encrypted at rest and should be anonimized so as to prevent any personally identifiable (PII) data being used to track back to the human behind the avatar. 

#### **Reliability**
 Data should be transmitted, processed and received at a reasonably fast speed. Below are assumed benchmarks that enable an MVP.

#### **Assumed benchmarks**


| Benchmark | Value |
|-----------|-------|
| Latency| 5Mbps (one way)|
| Throughput| 2000 RPS @ 5Mbps|

* _Latency:_ 5Mbps Transmission rate - this system should be capable of transmitting 5 Mbps in a one way call. This benchmark will enable HD 1080p quality video to be streamed.
> Using [Youtube's live stream guidelines](https://support.google.com/youtube/answer/78358?hl=en)  as a benchmark.
         
 
* _Throughput:_ The architecture should handle 2000 simultaneous connections (from multiple devices) at 5Mbps.
The services should at a minimum be capable of handling 10GBps bandwith to support the minimum required connections. 
>   [AWS General purpose M* class EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/general-purpose-instances.html#general-purpose-network-performance) instances are a good example of hardware to provision for this. 

* _Compute:_
    
    **Client Side:** 
    Client side devices should be capable of handling high fidelity input and enginer agnostic rendering. Some examples include

    *  Modern IOS & Android devices that have [ARKit](https://developer.apple.com/augmented-reality/arkit/) and [ARCore](https://developers.google.com/ar/) capabilities.
    * AR / VR headsets like the [Microsoft HoloLens](https://www.microsoft.com/en-us/hololens), [Meta Quest](https://www.meta.com/quest/) and the new [Apple Vision Pro](https://www.apple.com/apple-vision-pro/) have these capabilities.
    * Devices that only posess browser capabilities should be capable of rendering avatars. However, do may not have the capabilities to capture sensory input.  

    **Server Side:** 
    Server side compute should enable high fidelity rendering and streaming, audio rendering and also real-time voice generation to power the translation capabilities. 
    > [AWS GPU class Instances](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs-gpu.html) are a good example of hardware that can powere server side rendering.

 
#### Input / Output stack
Below is a proposal of the sequence  of operations within the instantiation device. This proposal has not been validated and there could be devices on the market that implement this today.
```mermaid
    sequenceDiagram
    participant sensors
    participant audio
    participant display
    participant haptics
        sensors ->> encoder/decoder: Send sensory data for endocding
        audio ->> encoder/decoder: Send audio data for encoding
        encoder/decoder -->> haptics: Send decoded sensory data
        encoder/decoder -->>  display: Send decoded sensory data to power avatar
        encoder/decoder -->> audio: Send decoded & translated audio data

        loop 
            encoder/decoder ->> real-time protocol:  send encoded data (sensory, audio) to be transmitted
            real-time protocol -->> encoder/decoder: Decode data (sensory, audio)received from transport layer
        end
        loop 
            real-time protocol ->> upstream services:  Transmit data to upstream services
            upstream services -->> real-time protocol: Receive data to be sent to the decoder
        end

 ```





