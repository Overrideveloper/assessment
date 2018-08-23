# Performance Optimization
This is the fine tuning and improvement of a systems performance. The reason for such improvement could be either real or anticipated. Most systems will respond to increased load with some degree of decreasing performance. The act of modifying a system to handle a higher load is synonymous to performance tuning.

**Benefits of measuring performance and scalability**
------------------
- Improve efficiency of performance tuning by identifying bottle necks.
- Accurate data on infrastructure requirements and costs to meet application performance and scalability goals.
- Assurance that current infrastructure will meet anticipated user demand.
- Reassurance to developers as regards having the knowledge whether pushing updates to software will affect the scalabilty and performance of the system.

**Kinds of test**
------------
- Performance Test: determine or validate speed of the application.
- Load Test: Determines how an application's performance varies as load increases.
- Stress Test: its a kind of load test, that determines application behaviour when pushed beyond normal or peak load conditions.

#  Common performance metrics

**What to measure (Performance Metrics)**
-------
- Time To First Byte(TTFB): refers to how quickly the server sends back the first byte of a response to a given page request.
- Time To Last Byte(TTLB): refers to the time required to get all dependent requests including images, css and script files.

**What to measure (Load Characteristics)**
--------
- User Load: how many users are being simulated in accessing the system at a given time.
- Request per second.
- Errors per second.

**What to measure (Resource Utilization per server)**
---------
- CPU
- Memory
- Disk/Network