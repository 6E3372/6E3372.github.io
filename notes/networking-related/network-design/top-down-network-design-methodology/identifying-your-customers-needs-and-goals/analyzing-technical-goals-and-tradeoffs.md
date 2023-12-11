# Analyzing Technical Goals and Tradeoffs

## Technical Goals

* Scalability
* Availability
* Performance
* Security
* Manageability
* Usability
* Adaptability
* Affordability



### Scalability

* ability to grow

### Availability

* the amount of time a network is available to users
* availability can be expressed as a percent uptime per year, month, week, day, or hour, compared to the total time in that period
  * eg. 24/7, availability is 98.1%, 99.999% (five nines)
* Availability can also be expressed as a MTBF[^1] and MTTR[^2]
* Availability = MTBF / (MTBF + MTTR)

### Performance

Factor that can effect performance

* Bandwidth
* Throughput
* Bandwidth utilization
* Offered load
* Accuracy
* Efficiency
* Delay (latency) and delay variation
* Response time

### Security

* Identify network assets
  * Hardware
  * Software
  * Applications
  * Data
  * Intellectual property
  * Trade secrets
  * Company’s reputation
* Analyze security risks

### Manageability

* Performance management
  * Analyzing traffic and application behavior to optimize a network, meet service-level agreements, and plan for expansion
* Fault management
  * Detecting, isolating, and correcting problems; reporting problems to end users and managers; tracking trends related to problems
* Configuration management
  * Controlling, operating, identifying, and collecting data from managed devices
* Security management
  * Monitoring and testing security and protection policies, maintaining and distributing passwords and other authentication and authorization information, managing encryption keys, and auditing adherence to security policies
* Accounting management
  * Accounting of network usage to allocate costs to network users and/or plan for changes in capacity requirements

### Usability

* the ease of use with which network users can access the network and services

### Adaptability

* Avoid incorporating any design elements that would make it hard to implement new technologies in the future

### Affordability

* A network should carry the maximum amount of traffic possible for a given financial cost

[^1]: mean time between failure

[^2]: mean time to repair
