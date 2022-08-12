# Quality Attributes

### Quality Attributes Motivation and Definition
+ System are frequently redesigned NOT because of functional requirements But because the system as it stands:
    - Isn't fast enough
    - Doesn't scale
    - Slow to develop
    - Hard to maintain
    - Not secure enough
+ Quality attributes are non functional requirements
+ They describe the qualities of the functional requirements and the overall properties of the system
+ Provide a quality measure on how well our system performs on a particular dimension
+ They have direct correlation with the architecture of our system

### Quality Attributes Example
```
    "(1) When a user clicks on a search button after they type in a particular search keywords, the user will be provided with a lif of products that closely match the search keyword (2) within at most a 100 milliseconds. (3) The online store must be available to user a requests at least 99.9% of time. (4) Development team can deploy a new version of the online store at least twice a week"
```
+ (1) : Functional Requirement
+ (2) : Performance Quality Attribute
+ (3) : Availability Quality Attribute
+ (4) : Deployability Quality Attribute

### Quality Attributes Considerations
+ Testability and Measurability
    - Quality attributes need to be:
        * Measurable
        * Testable
    - If we can't prove that our system satisfied the required quality attribute we don't know if our system performs well or poor
+ Tradeoffs(절충안 제시)
    - No single software architecture can provide all the quality attributes.
    - Certain quality attributes contradict one another
    - Some combinations of quality attributes are very hard or impossible to achieve
    - Software Architects need to make the right tradeoff
+ Feasibility(실현 가능성)
    - We need to make sure that the system is capable of delivering with the client asking for
    - The client may ask for something that is either
        * Technically impossible
        * Prohibitively expensive to implement
    

### An example of Unmeasurable Quality Attribute

```
    "When a user clicks on the buy button, the purchase confirmation must be displayed quickly to the user"
```
+ Needs to be changed into specific measurable value(=> within 200 milis/s)

### An example of Trade Off of Quality Attribute

```
    1. Performance: Login Time < 1s
    2. Security: Check Username, Password, SSL > 1s
```
+ Needs to talk about which one has priority and adjust them well

### An example of Feasibility of Quality Attribute

```
    (1)The data center is too far from the client's company and it takes at least 150 miliseconds to get response. But they want it within 100 miliseconds.

    (2)"Plase make the system never fail for Maintenance, Upgrade."

    (3)Full protection against hackers. 

    (4) High resolution video streaming in limited bandwidth areas

    (5) Very high storage growth
```
+ The architects have to catch that it is impossible in advance and let them know
+ You should talk it with Domain experts in advance.
+ There is no 100% perfect system.



<link rel='stylesheet' href='styles.css'>