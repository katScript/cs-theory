# Scalability

### Definition

```
A scalable system is one that can handle rapid changes to workloads and user demands. 
Scalability is the measure of how well that system responds to changes by 
    adding or removing resources to meet demands.
    
Is the ability of a system to continue to work as user load and data grow.
```

**Common metric:**
- **throughput:** the number of queries or requests processed in a given period. **qps** (query per second) , **rps** (request per second).
- **latency:** `response time = network delay + latency`

<hr>

#### Latency
**1.Mean**
```
Mean: average of all request’s latency
    - request 1, request 2, ..., request 9: 100ms
    - request 10: 3s
    => mean latency = 390ms
```
**2.Percentile**
```
Percentile: the response time threshold at which x% of request are faster than 
    that particular threshold.
    - p95 = 100ms => 95 out of 100 requests take less than 100ms, 5 requests take > 100ms.
```

_**High** latency can cause **Low** throughput_

**Cause of high latency:**
- Complex computation (O(n^2) vs O(n))
- Storage delay (RAM vs hard disk)
- Distance (use CDN (static: html, css, image) <=> cache that is near users)
- Protocol 
  - gPRC : http 2 
  - REST API: http 1.x

**How to reduce latency:**

<hr>

#### Throughput

**To increase throughput:**
- **Vertical scaling:** use more powerful machine.
- **Horizontal scaling:** distribute load access multiple smaller machines.
- Reduce latency




