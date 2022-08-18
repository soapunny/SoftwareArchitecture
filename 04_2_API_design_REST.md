# REST API

# What is REST API
+ A new style that originated from a dissertation published by Roy Fielding in 2000(2000 논문에서 파생된 새로운 스타일)
+ REST stands for Representational State Transfer(표현 상태 전송)
+ Set of architectural constraints and best practices for defining APIs for the web(웹 API를 정의하는 설계적 제약사항과 모범 사례 모음이다.)
+ It is not a standard or a protocol
+ It is an architectural style for designing APIs that are easy for our clients to use and understand(클라이언트가 쉽게 이해하고 사용하는 API로 설계하는 방식이다)
+ It makes it easy for us to build a system with quality attributes such as:
    - Scalability
    - High availability
    - Performance

```
    An API that obeys the REST architectural constraints is called a RESTful API
```

### RPC vs REST API
+ The RPC API style:
    - Revolves around methods that are exposed to the client
    - Methods are organized in an interface/set of interfaces
    - Our system is abstracted away from the client through a set of methods the client can call
    - API expansion through adding more methods
    - The actions the client can take regardless of its state are statically defined ahead of time by IDL(오직 IDL,데이터분석에 사용되는 언어,에 의해 사전에 정적으로 정의된 작업만을 상태에 관계없이 가질 수 있다)

+ REST API style:
    - Takes a more resource-oriented approach(보다 더 리소드 지향적인 접근방식)
    - The main abstraction to the user is a named resource(사용자에게 보여지는 주된 추상화 도구는 리소스이다)
    - The resources encapsulate different entities in our system(리소스는 시스템의 다양한 엔티티를 캡슐화한다)
    - REST API allows the user to manipulate those resources through small number of methods(REST API는 유저가 소수의 메서드를 통해서만 그 자원들을 통제할 수 있게 한다.)
    - REST API is dynamic in nature(동적이다)
    - This interface is a lot more dynamic through Hypermedia as the Engine of the Application State(HATEOAS)
    - Achieved by accompanying a state representation response to the client with hypermedia links(하이퍼미디어 링크로 클라이언트에게 현재상태 response를 동반한다)


# REST API Quality Attributes

### Statelessness(무상태성)
    + The server is stateless
    + It does not maintain any session information about client(client의 세션정보를 유지하지 않는다)
    + Each message should be served in isolation without any information about previous requests(이전 요청들에 대한 어떠한 정보도 가지지 않고 각각의 메시지는 독립적으로 처리되야 한다)

### Cacheability(캐시 가능성)
+ The server has to either explicitly/implicity define each response as either:(서버는 각각의 response를 명료하게/함축적으로 정의해야한다.)
    - Cacheable(캐시 가능한지)
    - Non-cacheable(불가능한지)
+ We can get information from the Cache instead of our server.
+ It reduces the load on our system(시스템 부하 줄여줌)

# Named Resources
+ Each resource is named and addressed using a URI(Uniform Resource Identifier) - 각 리소스의 이름과 주소는 URI를 사용한다.
+ The resources are organized in a hierarchy(각 리소스는 계층 구조로 구성되며)
+ Each resource is either:
    - Simple resource(단일 리소스)
    - Collection resource

### Hierarchy of Resources
+ The hierarchy is represented using "/"
+ A simple resource:
    - Has a state(상태가 있고)
    - Can contain one/more sub-resources(하나 또는 그 이상의 하위 리소스를 포함할 수 있다.)
+ A collection resource
    - Contains a list of resources of the same type
    ```
        aaa.com/movies/movie38
        aaa.com/movies/movie27
        ...
    ```

### Representation of Resources
+ The representation of each resource state can be expressed in a variety of ways such as:(리소드 상태의 표현은 다양한 방식으로 이루어 질 수 있다)
    + An image
    + A link to a movie stream
    + An object
    + An HTML page
    + Binary blob
    + Executable code like javascript

# Resources - Best Practices
1. Naming our resources using nouns
    + It makes a clear distinction from the actions that we're going to take (메서드와의 구분)
    + We're going to use verbs for the actions on those resources(리소스 메서드에 대해 동사를 사용)
2. Making a distinction between collection resources and simple resources
    + Plural names for collections
    + Singular names for simple resources
3. Giving the resources clear and meaningful names
    + The users will find it very easy to use our API(우리 API를 사용하기 매우 쉽게)
    + It will help prevent incorrect usage and mistakes(오용이나 실수를 방지할 수 있다.)
    + Overly generic collection names
    should be avoided
        - elements
        - entities
        - items
        - instances
        - values
        - objects
4. The resource identifiers should be unique and URL friendly(리소스 식별자는 고유하고 URL 친화적이여야 한다.)
    + They can be used easily and safely on the web(쉽고 안전하게 사용될 수 있다)


# REST API Operations
+ Unlike RPCs, the REST API limits the number of methods we can perform on each resource
+ These predefined operations are:
    - Creating a new resource -> POST
    - Updating an existing resource -> PUT
    - Deleting an existing resource -> DELETE
    - Getting the current state of the resource(list of sub-resources in case of collection resource - 컬렉션 리소스에 경우 하위 리소스 목록으로) -> GET
+ In some situations, we define additional custom methods

### HTTP Methods - Guarantees
1. GET method is considered safe - applying it to a resource would not change its state(리소스에 적용해도 상태가 변하지 않는다)

2. GET, PUT, DELETE methods are idempotent - applying them multiple times would result in the same state change as applying them once(멱등성을 가짐)

3. GET requests are considered cacheable by default

4. Responses to POST requests can be made cacheable

### Sending Additional Information
+ To send additional information to our system as part of a POST or PUT command use:
    - JSON
    - XML


# Defining REST API Step by Step

1. Identifying Entities
    + ex) users, moview, reviews, actors

2. Mapping Entities to URIs
```
    #user
    /users
    /users/{user-id}

    #movie
    /movies
    /movies/{movie-id}

    #actor
    /actors
    /actors/{actor-id}

    #review
    /movies/{movie-id}/reviews
    /movies/{movie-id}/reviews/{review-id}
```

3. Defining Resources' Representations
```
    GET /movies
    {
        "movies":[
            {
                "name": "aaa",
                "id": "12jid3"
            },
            {
                "name": "bbb",
                "id": "34sew3"
            }
        ]
    }

    GET /movies/{movie-id}
    {
        "movie-info":{
            "name":"aaa",
            "id": "12jid3"
        },
        "links":{
            "movie-stream":".",
            "reviews": "/movies/12jid3/reviews",
            "actors": "/actors?movie-id=12jid3",
        }
    }
```

4. Assigning HTTP Methods To Operations on Resources

+ POST /user/join -> Create new user
+ GET /users/{user-id} -> Get user information
+ PUT /users/{user-id} -> Update user information
+ DELETE /users/{user-id} -> Delete Existing user

<link rel='stylesheet' href='styles.css'>