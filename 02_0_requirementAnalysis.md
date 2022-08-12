# Requirement Analysis

### What is System Requirements
+ Format description of what we need to build

### High level of Ambiguity
+ Large scale system requirements are different than the usual requirements we typically get for implementing(Big scope and high level of abstraction)
+ The person providing the requirements is often not an engineer and may even be not very technical.
+ The client doesn't always know what they need
+ The client generally knows only what problem they need solved.

### How to clarify the ambiguious requirements?
        "Allow people to join drivers on a route, who are willing to take passengers for a free." - very ambiguious requirement.
+ Real Time vs Advance Reservation
+ User Experience: Mobile vs Desktop vs both
+ Payment through us vs direct payment

### What happen if we neglect gathering requirements?
+ Large scale systems are big projects that cannot be easily changed
+ Many engineers are involved
+ Many months of engineering work
+ Hardware and Software costs
+ Contracts include financial obligations.
+ May damage your reputation and brand


### Types of Requirements(Architectural Drivers)
+ Features of the System(시스템 기능)
    - Functional requirements
+ Quality Attributes(품질 속성)
    - Non-Functional requirements
+ System Constraints(시스템 제약)
    - Limitations and boundaries

### Features of the System
+ Describe the system behavior, "What system must do"
+ Easily tied to the objective of our system
+ Functional requirements do not determine its architecture
+ Generally, any architecture can achieve any feature(모든 설계는 모든 기능을 수행할 수 있다.)

    ```
    "When a rider logs into the service mobile app (->input), 
    the system must display a map with nearby drivers within 5 miles radius (->output)"

    "When a rider is completed(->input),
    the system will charge the rider's credit card and credit the driver, minus service fees(->output)"
    ```

### Quality Attributes
+ System properties, "the system must have"
    - Scalability
    - Availability
    - Reliability
    - Security
    - Performance 
    - ...
+ The quality attributes dictate the software architecture of our system

### System Constraints
+ Time Constraints - Strict deadlines
+ Financial Constraints - Limited budget
+ Staffing Constraints - Small number of available engineers

***

<link rel='stylesheet' href='styles.css'>