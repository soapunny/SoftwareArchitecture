# Intuition and motivation for Software Architecture

### The software architecture impacts

+ Performance and scale of the product
+ Ease of adding new features
+ Response to failure or security attack.
+ Cost of the money and time of the project.

### Definition of Software Architecture

    The software architecture of a system is a *high-level description of the system's structure, its different components, and how those *components communicate wiht each other to fulfill the systems' *requirements and constraints.

+ high-level description: An abstraction that shows us the important components while hiding the implementation details.
+ Technologies or programming languages are not a part of the software architecture but a part of the implementation.
+ Design about the implementation should be delayed to the very end of the design.
+ The components here are "black box" elements defined by their behavior and APIs.
+ Components come together to do what the system must do, which are cour requirements.
+ The system does not do what it shouldn't do, which are the constraints.

### Levels of Abstraction
+ Classes/structs -> Lowest level
+ Modules/packages/libraries -> Middel level
+ Services (processes/groups of processes) -> High level

### Advantages of Distributed, multiple service approach
+ Handle large amounts of requests.
+ Process and store very large amounts of data
+ Serve many users every day

### Examples of large scale systems
+ Ride-sharing
+ Video-on-demand
+ Social media
+ Online video games
+ Investment Services
+ Banks

### Software Development Cycle

    Design -> Implementation -> Testing -> Deployment

+ The cycle repeats but the first cycle is the most important one.
+ Software Architecture is the output of the Design and the input of the Implementation.

### Challenges of Software Architecture
+ We cannot prove Software Architecture to be either correct or optimal.
+ The way to guarantee success is
    - to have Methodical Design Process
    - to use Proven Architectural Patterns
    - to refer the Best Practices(모범 사례 참조)

<link rel='stylesheet' href='styles.css'>