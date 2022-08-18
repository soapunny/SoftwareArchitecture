# API Design

### What is an API?
+ After capturing all functional requirements, we can think of our system as a black box
+ The black box has:
    - Behavior
    - Well-defined interface
+ The interface is contract between:
    - Engineers who implement the system(시스템을 구현하는 엔지니어와)
    - Client applications who use the system(시스템을 사용하는 클라이언트 어플리케이션)
+ Since this interface is called by other applications, it is referred to as an Application Programming Interface(API)
+ In a large-scale system, API is called by other applications remotely through the network
+ The applications calling our API may be:
    - Front-end clients like mobile applications/web browsers
    - Back-end systems that belong to other companies
    - Internal systems within our organization
+ Each component of our system will have its own API
+ The component API's will be called by other applications within our system
***

# API categories
+ APIs are classified into three groups:
    - Public APIs
    - Private/Internal APIs
    - Partner APIs

### Public APIs
+ Exposed to the general public
+ Any developer can use/call them from their application
+ Requiring the users to register with us before allowing to send requests and use the system
+ This allows:
    - Control over who uses the system externally
    - Control over how they use the system
    - Better security
    - To blacklist users breaking rules

### Private APIs
+ Exposed only internally within the company
+ They allow other teams/parts of the organization to:
    - Take advantage of the system
    - Provide bigger value for the company
    - Not expose the system directly outside the organization

### Partner APIs
+ Similar to Public APIs
+ Exposed only to companies/users having business relationship with us
+ The business relationship is in the form of:
    - Customer Agreement after buying our product
    - Subscribing to our service

***

# Benefits of a well designed API
1. Client who uses it can immediately and easily enhance their business by using our system
2. They need not know anything about our system's internal design/implementation
3. Once we define and expose our API, clients can integrate with us without waiting for full implementation of our system
4. API makes it easier to design and architect the internal structure of our system
    - It defines the endpoints to the different routes that the user can take to use our system(사용자가 우리 시스템을 사용하기 위해 취할 수 있는 다양한 경로에 대한 엔트포인트("요청-응답이 있는 서비스"를 사용할 수 있는 지점)을 정의한다.)

***

# API best practices and patterns

### Complete Encapsulation
+ Complete Encapsulation of the internal design and implementation
+ Abstracting it away from a developer wanting to use our system(우리 시스템을 사용하는 개발자와 API가 관계가 없도록 분리)
+ If client wanting to use our API:
    - Requires any information about how it is implemented internally
    - Needs to know our business logic to use it
+ Then, the whole purpose of the API is defeated
+ API should be completely decoupled from our internal design and implementation
+ We can change the design later without breaking the contract with our clients

### Easy to Use
+ Easy to use
+ Easy to understand
+ Impossible to misuse
+ The ways to make an API simple can be:
    - Only one way to get certain data/perform a task
    - Descriptive names for actions and resources
    - Exposing only the information and actions that users need
    - Keeping things consistent all across our API(모든 항목을 일관되게 유지하는것)

### Keeping the Operations Idempotent(멱등성, 여러번 수행하더라도 결과가 달라지지 않는,을 유지)
```
    "An operation doesn't have any additional effect on the result if it is performed more than once"
```
+ Idempotent Operations
    - Updateing the user's address to a new address is an Idempotent Operation
    - The result is the same regardless of performing it any number of times
+ Non-Idempotent Operations
    - Incrementing a user's balance by a hundred dollars is not an Idempotent Operation
    - The result will be different depending on the number of times we perform it
+ Idempotent Operations are preferred for our API as they are going to be used through the network
+ If the client application sends us a message:
    - The message can be lost
    - The response to that message may be lost
    - The message wasn't received as a critical component in our system went down
+ Because of network decoupling, the client application has no idea which scenario actually happened
+ If our operation is idempotent, they can simply resend the same message again without any consequences

### API Pagination
+ Important when a response from our system to the client request contains a very large payload or dataset
+ Without pagination most client applications will:
    - Not be able to handle big responses
    - Result in a poor user experience
    - Examples
        * After opening your email account, you see all the emails you ever received instead of the latest emails
    - The client application/web browser is unlikely to handle so much data
    - It would take an unreasonable time to show all those results
+ Pagination allows the client
    - To request only a small segment of the response
    - Specify the maximum size of each response from our system
    - Specify an offset within the overall dataset
+ To receive the next segment we increment the offset

### Asynchronous Operations
+ Some operations need one big result at the end
+ Nothing meaningful can be provided before the entire operation finishes
+ Examples of such operations can be:
    - Running a big report requiring our system to talk to many databases
    - Big data analysis that scans a lot of records/log files
    - Compression of large video files
+ If the operation takes a long time, the client application has to wait for the result
+ The pattern used for these situations is an Asynchronous API
+ A client application receives a response immediately without having to wait for the final result
+ That response includes some kind of identifier that allows:
    - To Track the progress and status of the operation
    - Receive the final result


### Versioning our API(버전 사용)
+ Best API design allows us to make changes to the internal design and implementation without changing the API
+ In practice, we may need to make non-backward compatible API changes(실무에서, 이전 버전과 호환되지 않게 API 수정을 해야할 지도 모른다)
+ If we explicitly version the APIs we can:
    - Maintain two versions of the API at the same time
    - Deprecate the older one gradually

### Defining our API
+ We can define our API in any way as long as we adhere to these best practices
+ A few types of APIs have become more standard in the industry

<link rel='stylesheet' href='styles.css'>