# SLA, SLO, SLI

### SLA - Service Level Agreement
+ It is a legal contract that represents our quality service such as
    - Availability
    - Performance
    - Data durability
    - Time to respond to system failures
+ It states the penalties and financial consequences, if we breach the contract(계약을 위반했을때, 패널티와 금전적 보상)
    - Full/Partial refunds
    - Subscription/License extensions
    - Service credits(서비스 수준 확인서)
+ It exist for
    - External paying users(always)
    - Free external users(sometimes)
        * It makes sense if our system has major issues during a free trial of our service
        * We compensate users with a trial extension or credits for future
        * Company providing entirely free services don't publish SLA
    - Internal users within our company(occasionally)  
        * It doesn't include any penalties


### SLOs - Service Level Objectives
+ Individual goals set for our system
+ Each SLO represents a target value/range that our service needs to meet
    - Availability Service Level Objective of 3 nines
    - Response Time SLO of less than 100 milliseconds at the 90th percentile
    - Issue Resolution Time Objective of between 24 and 48 hours
+ SLOs include
    - Quality attributes from the beginning of the design process
    - Other objectives of our system
+ Systems that don't have SLA still must have SLOs
+ If we don't set SLOs, our users won't know what to expect from our system


### SLIs - Service Level Indicators
+ Quantitative measure of our compliance with a service-level objective(서비스 수준 목표 준수에 대한 양적 측정)
+ It is the actual numbers:
    - Measured using a monitoring service
    - Calculated from our logs
+ It can be later compared to our SLOs
+ Examples
    - Percentage of user requests receiving a successful response can be used as a SLI for availability
    - Later it can be compared to the availability SLO of three nines that we set
    - The average/percentile distribution of the response time experienced by users can be calculated(유저 경험에 의한 응답시간 평균/백분율 분포를 계산할 수 있다.)
    - Later it can be compared to the end-to-end latency SLO of 100 milliseconds at the 90th percentile that we set(나중에 이 수치는 종단간(user-server) 지연 서비스 수준 목표인 "90th 백분위에서 100밀리초"와 비교할 수 있다.)

### SLI, SLO and SLA
+ SLO represent the target values for the important quality attributes
+ Quality attributes need to be testable and measurable
+ If they weren't measurable, we wouldn't find any SLIs to validate that we meet our SLOs
+ If we can't prove that we meet the SLOs, we can't say that we meet our SLA
+ SLAs are crafted by the business and the legal team
+ SLOs and SLIs are defined and set by the software engineers and architects


### Important Considerations
1. We shouldn't take every SLI that we can measure in our system and define an objective associated with it
    - Instead, we need to think about the metrics that users care about the most
    - Define the SLOs around those metrics 
    - From that, right SLIs to track those SLOs can be found
2. Promising fewer SLOs is better
    - With many SLOs, it's hard to priorize all of them equally
    - With fewer SLOs, It's easier to focus the entire software architecture around them
3. Set a realistic goals with a budget for error(오류에 대한 예산을 포함한 현실적 목표 설정)
    - We shouldn't commit to five-nines of availability even if we can provide that
    - We should commit to a much lower availability than we can provide(제공 가능한것 보다 더 낮은 가용성을 보장하기 위해 집중해야 한다.)
    - This saves costs and incorporates unexpected issues(이는 비용을 절약하고 예상치 못한 문제를 대비할 수 있다.)
    - This is true when our SLOs are represented in an external SLA
    - Companies define separate external SLOs which are looser than internal SLOs(내부 서비스 수준 목표 보다 더 느슨한 외부 서비스 수준 목표을 따로 설정한다.)
    - Externally we can commit to 99.9% of availability but internally we commit to 99.99% availability(외부적으로 3 nines 수준의 가용성을 설정하지만 내부적으로 4 nines 수준의 가용성을 위해 노력할 수 있다.)
    - We can strive for better quality internally while committing less to clients
    (클라이언트에 신경을 덜 쓰면서 내부적으로 더 나은 품질을 위해 노력할 수 있다)
    - This would avoid financial penalties
4. Create a recovery plan for when the SLIs show that we are not meeting our SLOs
    - we need to think when 
        * the system goes down for long time
        * the performance degrades
        * we have reports about issues/bugs in the system
    - The plan should include
        * Automatic alerts to engineers/DevOps
        * Automatic failovers/restarts/rollbacks/auto-scaling policies
        * Predefined handbooks on what to do in certain situations



<link rel='stylesheet' href='styles.css'>