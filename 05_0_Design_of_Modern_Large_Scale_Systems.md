# DNS, Load Balancing, GSLB

### Load Balancer - Introduction
```
    Balance load among a group of servers - 시스템의 여러 서버에 트래픽 부하를 나누는 것
```
+ Automatically balance the load to a group of servers
+ It makes the servers seem like a single server

### Quality Attributes
1. Scalability
    + In a cloud environment, we can use auto-scaling policies to intelligently add/remove servers based on
        - Requests per second
        - Network bandwidth
2. High Availability
    + Using monitoring service, It balance the load except a server with problem
3. Performance(Throughput)
    + When it comes to performance, load balancers may add a little latency(약간의 지연이 있을 수 있다)
    + It is an acceptable price to pay for increased performance in terms of throughput(하지만 처리량에 있어서는 높은 성능을 띄므로 충분히 감내할 수 있다)
4. Maintainability
    + We can maintain a server one by one without shutting down the whole servers

### Types of Load Balancers
1. DNS load balancing
2. Hardware load balancing
3. Software load balancing
4. Global Server Load Balancing

### DNS - Domain Name System
+ DNS is part of the internet infrastructure that maps human-friendly URLs to IP addresses
+ They can be used by network routers to route requests to individual computers on the web
+ DNS is the "phone book of the internet"

### DNS Load Balancing - Advantages
+ Simple
+ Cheap(Comes for free by purchasing a domain name)

### DNS Load Balancing - Drawbacks
1. DNS doesn't monitor the health of our servers(It doesn't know whether the server is down or good)
    - The list of IP addresses changes based on the TTL(Time to live) configured for that particular DNS record(특정 DNS 레코드에 대해 구성된 TTL에 따라 IP 주소 목록이 변경됨)
    - This list of addresses can be cached in different locations such as the client's computer(클라이언트의 컴퓨터 같은 장소에 주소목록이 캐시될 수 있다) - The time between the server shuts down and the point it request something to server instead of cache will be longer

2. The balancing strategy is always just a simple round-robin
    - Some of our application instances may be running on more powerful servers than others(균등한 분배X)
    - One of our servers may be more overloaded than the other

3. The client application gets the direct IP addresses of all our servers(클라이언트 어플이 우리 서버의 모든 직접적 아이피 주소를 얻는다)
    - This exposes some implementation details of our system(시스템의 구현 세부사항을 노출시킴)
    - It makes our system less secure(보안 문제 야기)
    - A malicious client application can pick one IP address and send requests only to that particular server(악의적인 클라이언트가 IP주소 하나를 정해 트레픽 과부하를 일으킬 수 있다)

### Hardware Load Balancers
+ Run on dedicated devices designed and optimized specifically for load balancing(로드 밸런싱에 특화 설계된 전용 장치에만 실행 가능)


### Software Load Balancers
+ Programs that can run on a general-purpose computer and perform a load balancing function(일반 컴퓨터에서도 작동)


### Software/Hardware Load Balancing Strategies
+ They can check the health of our server
+ They can balance the load intelligently taking into account(알아서 다음을 판단):
    - Different types of hardware(하드웨어 유형)
    - Current load on each server(각 서버의 현재 부하량)
    - Number of open connections(활성화된 연결)
+ They can be used inside our system
+ They can create an abstraction between different services(서비스 사이의 추상화, 독립성을 가지고 확장가능)

### Load balancers - DNS Resolution
+ Load balancers on their own do not solve the DNS resolution
+ We would still need some kind of DNS solution to map a human-readable domain name to an IP address(여전히 DNS 솔루션이 필요)

### Global Server Load Balancing(GSLB)
+ hybrid solution
    - DNS service
    - Hardware/Software Load Balancer
+ response client with most nearby IP addresses of Load balancer
+ Most GSLB can be configured to route traffice based on a variety of strategies and not just by physical location (물리적 위치만이 아닌 다양한 전략에 의해 트래픽을 라우팅함)
+ Since they are in constant communication with our data centers, they can be configured to route users based on current traffic, CPU load in each data center, Best-estimated response time or Bandwidth between user and the data center(데이터 센터와 지속적으로 통신하므로, 현재 트래픽이나 CPU 부하량, 최적의 응답 시간 또는 유저와 데이터 센터 사이의 대역폭을 기반으로 라우팅)
***

# Load Balancing Solution
+ Open source
    - HAProxy
    - NGNIX
+ Based on Cloud
    - Application(Layer 7)Load Balancer
    - Network(Layer 4) Load Balancer
    - Gateway Load Balancer
    - Classic Load Balancer
+ GCP - Cloud Load Balancing
    - External HTTP(S) Load Balancer
    - Internal HTTP(S) Load Balancer
    - External TCP/UDP Network Load Balancer
+ Microsoft Azure Load Balancer
    - Standard Load Balancer
    - Gateway Load Balancer
    - Basic Load Balancer
+ GSLB Solutions
    - Amazon Route 53
    - Google Cloud Platform Load Balancer & Cloud DNS
    - Azure Traffic Manager


<link rel='stylesheet' href='styles.css'>