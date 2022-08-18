# Message Broker

# Message Broker - Motivation

### Synchronous Communication
```
    Sender Application --> Load Balancer --> Receiver Application
    
```
+ They actively connect each other and both are healthy and running in the same time
+ Drawbacks
    1. Both application instances have to remain healthy and maintain this connection to complete the transaction
        - It's easy to achieve this when two services exchange small messages that take short time to process and respond
        - It can get complex when a service takes a long time to complete its operation and provide a response
    2. No padding in the system to absorb a sudden increase in traffic or load
*** 

# Message Broker - Benefits and Capabilities
```
    A software architectural building block that uses the queue data structure to store messages between senders and receives. It is used inside our system and not exposed externally
```

### Capabilities
+ Basic capabilities:
    - Storing/temporarily buffering the messages(일시적인 메시지 버퍼링과 저장 기능)
    - Message routing
    - Transformation validation(변환 유효성 검사)
    - Load balancing

### Loose Coupling between Senders & Receivers
+ Entirely decouple senders from the receivers(수신자 발신자 분리)
+ The fundamental building block of asynchronous software architecture(비동기 소프트웨어 설계에 있어 기초적인 빌딩블록)

### Message Broker - Benefits
+ Most message broker implementations offer the publish/subscribe pattern where multiple services can(대부분의 메시지 브로커 구현은 배포/구독 패턴을 제공하는데):
    - Publish message to a particular channel(다중 서버가 특정 채널에 메시지를 배포할 수 있게하고)
    - Subscribe to that channel(그 채널을 구독하게 하고)
    - Get notified when a new event is published(새로운 이벤트가 배포되면 알림을 얻게한다)
***

# Quality Attributes

### Fault Tolerance
+ A messsage broker adds a lotof fault tolerance to our system(내결함성 추가)
+ It allows different services to communicate with each other while some of them may be unavailable temporarily(몇몇이 사용 불가능하더라도 다른 서버들 간에 통신이 가능하게 한다)
+ Message brokers prevent messages from being lost

### Availability and Scalability
+ The additional fault tolerance helps us provide high availability to our users(뛰어난 내결함으로 고객에게 높은 가용성을 제공한다.)
+ A message broker can queue up messages when there is a traffic spike(트래픽이 급증하면 메시지를 큐에 줄세울 수 있다)
+ It allows our system to scale to high traffic without any modification(시스템 수정없이 많은 트래픽을 감당하도록)

### Performance
+ We pay a little in performance when it comes to latency(약간의 성능지연)
+ A message broker adds significant indirection between two services(두 서비스간 간접적인 의사소통이 상당히 많다)
+ This performance penalty is not too significant for most systems(대부분 시스템이 성능 패널티에 크게 영향을 받지 않는다)
***

# Message Broker Solutions

### Open Source
+ Apache Kafka
+ RabbitMQ

### Cloud based
+ Amazon Simple Queue Service(SQS)
+ GCP Pub/Sub and Cloud Tasks
+ Microsoft Azure Service Bus

<link rel='stylesheet' href='styles.css'>