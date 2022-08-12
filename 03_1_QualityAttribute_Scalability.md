# Scalability(확장성)

### Motivation
+ Traffic Patterns
    - The load/traffic on our system never stays the same. It can follow different patterns
        * Cruise business's webpage
        * traffic between week days and weekends

### Scalability Definition
+ The measure of a systems ability to handle a growing amount of work, in an easy and cost effective way, by adding resources to the system




### Vertical Scalability
+ Adding resources or upgrading the existing resources on a single computer, to allow our system to handle higher traffic or load
+ Scale up(성능 증가) -> upgrade hardwares
+ Pros:
    - Any application can benefit from it
    - No code changes are required
    - The migration between different machines is very easy(traffic low -> use cheaper resources, traffic high -> use upgraded resources)
+ Cons:
    - The scope of upgrade is limited
    - We are locked to a centralized system which cannot provide "High availability" and "Fault tolerance"

### Horizontal Scalability
+ Adding more resources in a form of new instances running on different machines, to allow our system to handle higher traffic or load
+ Scale up(성능 증가) -> add more unit of resources(ex. use multiple computers)
+ Pros:
    - No limit on scalability
    - It's easy to add/remove machines
    - If designed correctly we get "High availability" and "Fault tolerance"
+ Cons:
    - Initial code changes may be required
    - Increased complexity, coordination overhead

### Team/Organizational Scalability
+ The measure of a systems ability to handle a growing amount of work(features, testing, fixing bugs, releases), in an easy and cost effective way, by adding resources(engineers) to the system
+ Software Architecture impacts engineering velocity(team productivity, 생산성 증가)

### Too much engineer in same code base can cause
* Many crowded meetings
* Code merge conflict
* Business Complexity - Longer ramp up time(인력 고용 후 실전 배치까지)
* Testing is harder and slower
* Releases become very risky
    
### How to increase Team Scalability
+ Make each team to work on seperate, independant modules/library - But still each modules are tightly coupled each other
+ Seperate our codes into different services. Each service has its own codebase, stack, releasing date - loosely coupled each other, but it costs

<link rel='stylesheet' href='styles.css'>