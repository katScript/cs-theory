# Reliability

### Definition

```
Design for reliability is a collection of techniques 
    that are used to modify the initial design of 
    a system to improve its reliability.
    
Mean the system should continue to work correctly even in the face of 
    adversity (hardware or software faults, and even human error)
```

**Common metric:** `availability = uptime / (uptime + downtime)`

Usually expressed in terms of the number of "nines" we would like to provide: 99.9%, 99.99%, or 99.999% availability.

**Ex:** 99.99% (four “9”) available system means 1 year, your system can be down at most 52.56 minutes (~1 min per week).

**Aggregate availability:** `availability = successful request / total request`

**Ex:** A system that serves **2.5M requests** in a day with a daily availability target of 99.99% can serve up to **250 errors** and still hit its target for that given day.

<hr>

#### Techniques

**To achieve High Availability:**
 - Monitoring: health check, count real traffic success rate. (prometheus, grafana …)
 - Fault tolerance:
   - remove Single point of failure.
     - server has to be **stateless**
     - prefer smaller servers
     - **make sure each server can handle extra load**
     - N+2 rule: if your system need N servers
       make it N+2 => 1 extra for upgrade or testing
       and 1 for failure.
 


