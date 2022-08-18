# RPC
```
    RPC(Remote Procedure Call) is a function of client application that execute subroutine in a remote server
```

### Unique Features of RPC
+ The remote method invocation looks like calling a normal local method in terms of the developer code(원격 메서드 호출은 개발자 코드에서 로컬 메서드를 호출하는것 처럼 보인다.)
+ This is referred to as location transparency(위치 투명성)
+ To the developer of the client application a method executed locally or remotely looks the same(클라이언트 개발자에게 로컬, 원격 메서드는 비슷해보인다.)
+ RPC frameworks support multiple programming languages
+ Applications written in different programming languages can talk to each other using RPC(서로 다른 언어로 쓰여진 어플들이 RPC를 통해 통신할 수 있다.)


# How RPC works
+ This concept of implementing an API using an RPC has been around for decades
+ The only thing that changes over time are:
    - The frameworks
    - The details of their implementation
    - Their efficiency
+ Our job as API developers is:
    - To pick an appropriate framework
    - Define the API an the relevant data types using IDL
    - Publish that description


***

# Benefits of RPC
+ Convenience to the developers of the client applications
+ They can communicate with our system easily by calling methods on objects similar to calling normal, local methods
+ The details of communication establishment or data transfer between client to server are abstracted away from the developers(클라이언트에서 서버로의 통신 설정, 데이터 전송의 세부 사항은 개발자로부터 추상화된다)
+ Failure in communication with server result in an error or exception depending on the programming language

***

# Drawbacks of RPC(단점)
+ Unlike local methods executed on the client-side, remote methods are slower and less reliable
+ Slowness
    - The client never knows how long those remote method invocations can take
    - Slowness can be addressed by introducing asynchronous versions for slow methods(느린 메서드를 위한 비동기 버전을 도입하면서 해결할 수 있다.)
+ Unreliability
    - The client remotely running on a computer and is using the network to communicate with our system
    - Carelessness in designing the API can introduce confusing situations for the client application developers
        * In online shopping it can charge customer twice
    - There is no real way for the client to know whether:
        * The server received the message and the acknowledment message got lost in the network
        * The server crushed and never received the message
    - To solve the unreliability problem, we can stick to the best practice of making our operations idempotent when possible(멱등성 부여)

***

# When to use RPC
+ RPC are used in communication between two backend systems
+ Frameworks that support RPC from frontend clients are less common
+ RPC is a perfect choice for:
    - API provided to a different company instead of an end user app/web page
    - Communication between different components within a large system
    - Abstracting away the network communication and focusing only on the actions the client wants to perform
+ RPC approach would not be a good fit:
    - Where we don't want to abstract the network communication away
    - When we want to take direct advantage of HTTP cookies or headers

### Importance of RPC
+ RPC revolves more around actions and less around data/resources
+ In RPC, every action is a new method with a different name and signature
+ We can define many methods/actions without limitation


### When we need other styles of API
+ Designing an API that is more data-centric
+ All the operations needed are simple CRUD(Create, Read, Update, Delete) operations



<link rel='stylesheet' href='styles.css'>