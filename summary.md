# Myvatar - An end-to-end Avatar system
## Challenges
* Latency & Bandwidth: Overall latency & bandwidth are still limited to the slowest point in the communication chain. In most cases, this is the users' network. Functionality should be designed to account for low/intermittent bandwidth scenarios.
* Translation Service: Building a real-time Speech translation service is outside the scope of this design. Various third-party options exist and selection criteria should account for reliable SLAs and pricing. A good example is [Microsoft's Speech translation service](https://azure.microsoft.com/en-us/products/cognitive-services/speech-translation/)

## Unknowns
* **Input/output stack:**
Further research needs to be conducted to validate the design. Most devices on the market today already possess the capabilities to capture and transmit sensory input as data. An in-depth evaluation of the various existing options is required to arrive at a solution that meets the requirements of speed, security and reliability. 


## Risks
* Cost: The current architecture can become quite expensive over time. There needs to be a plan in place to  enable revenue generation to offset the cost of running the system
## Extended design
This architecture could benefit from a variety of improvements. These improvements should improve reliability & performance. They should also improve the customer experience and enable monetization. 

**Admin service:** This service should provide operational capabilities to monitor and manage the entire set of capabilities.
**Avatar Marketplace:** Provide capabilities for Users to design avatars and monetize their designs.
**Developer tools:** Provides tools for developers to build on and extend the capabilities of the current system. These tools should include
    * External APIs to manage and customize avatars. 
    * Open-source libraries with which Avatars can be exported and utilized in other systems with similar capabilities.
    * SDKs that enable the utilization

## Conclusion