# System Constraints

### Introduction

+ Once we define what our system must do, we have freedom on how to structure our system
+ While defining the final architecture, we have to make a lot of decisions
+ For quality attributes, we are expected to make trade-offs

### Definition
```
    "A system constraint is essentially a decision that was already either fully or partially made for us, restricting our degrees of freedom."
```
+ Instead of looking at a constraint as a choice that was taken away, we look at it as a decision that was already made.
+ System Constraints are referred as pillars for software architecture
    - They provide us with a solid starting point
    - The rest of the system need to be designed around them(나머지 시스템은 이것을 중심으로 설계되야 한다.)


### Types of System Constraints
+ Technical constraints
+ Business constraints
+ Regulatory/legal constraints

### Technical constraints
+ Technical constraints may seem like they belong to implementation and not to software architecture
+ In practice, they affect the decisions we make in the design phase and put restrictions on our architecture


### Examples of technical constraints
+ Being locked to a particular hardware/cloud vendor
+ Having to use a particular programming language
+ Having to use a particular database or technology
+ Having to support certain platforms, browsers, or OS
+ If our company makes a decision to run on-premise data centers(자체 보유 데이터 센터)
    - All the cloud architectures and paradigms(patterns) like Auto Scaling, which adjusts the size of the server automatically, will become unavailable to us
    - We would have to implement a lot of non-trivial(중요한) infrastructure
+ If we have to support some older browsers or low-end mobile devices
    - We have to adapt our architecture to support those platforms and their APIs
    - Keep providing a different, more high-end experience for newer browsers or higher-end devices

### Business Constraints
+ As engineers, we make the right decisions and architectural choices from a technical perspective
+ This forces us to make sacrifices in Architecture and Implementation

### Examples of Business Constraints
+ Limited budget or a strict deadline will make us have very different choices than if we had an unlimited budget and unlimited time
+ Different software architectural patterns are based on suitability between small startups or bigger organizations
+ Usage of third-party services with their own APIs and architectual paradigms(patterns) as apart of our architecture
    - Using third-party shipping/billing providers for an online store
    - Integration of different banks/brokers/security/fraud detection services for an investing platform

### Regulatory/Legal constraints(규제/법적 제한)
+ It can be global or specific to a region


### Examples of Regulatory/Legal Constraints
+ In the US, HIPAA(Health Insurance Portability and Accountability Act) places constraints on accessing patients' data
+ In the EU, GDPR(General Data Protection Regulation) sets limitations on collecting, storing and sharing users' data


### System constraints Considerations
+ We shouldn't take any given constraint lightly
    - There should be a distinction between Real constraints and Self-imposed constraints
+ Use loosely coupled architecture


### Examples of Accepting Constraints lightly
+ External rules and regulations may not have room to negotiate
+ Internal constraints can be negotiated
+ If locked to using a particular hardware/cloud vendor/technologies may be an opportunity to explore other options

### Examples of Loosely Coupled Architecture
+ If limited to a database/third-party service, we need to make sure our system is not tightly coupled to that technology or APIs
+ Usage of different technology/service in future should need minimal changes
+ Different parts of the system can be decoupled to be easily replaced or updated independently
+ 



<link rel='stylesheet' href='styles.css'>