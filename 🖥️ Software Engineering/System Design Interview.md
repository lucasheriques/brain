System design is simple: all it asks is that you understand how the underlying system of various websites and technologies work; how does sharding work under its hood and why one policy might be better than other; why is a load balancer necessary, and what benefit or purpose does it serve; and so on.

An engineer needs to understand what parts of a tech stack could go right or wrong.

# Characteristics of Distributed Systems

## Scalability
For a system to be scalable, it must be able to adapt to growing demand whether that demand is number of users or an increase in network requests.

### Horizontal Scaling
Scaling a system horizontally means adding more servers to the pool of resources. Might be easier than vertical scaling as you can purchase a new server and have it up and running quickly.

**Cassandra** and **MongoDB** are examples of database management systems that use horizontal scaling.

### Vertical Scaling
Requires adding more power, such as CPU or RAM to existing servers. Is often more difficult to achieve as you're limited to a single server, so scaling past that server's capability often requires downtime and has an upper-bound limit.

**MySQL** is a example of vertically scaling database.

## Reliability / Fault Tolerance

Probability that a system will fail during a given period of time. A system is reliable if it continues functioning when its hardware or software fails. 

## Load Balancing

Process that determines how your servers receive requests. Load balancing not only distributes traffic to servers but also monitors the status of the servers while distributing traffic. If a server suddenly becomes unavailable to accept new requests, the load balancer will prevent new requests from reaching that server.

They sit between the client and the server, and use variouds algorithms to determine how traffic should be distributed to different servers. By distributing traffic, load balancers prevent any individual server from being inundated with requests.

### Load Balancing Algorithms
- **Least Connection Method**: distributes traffic to the server with least active connection.
- **Least Response Time Method**: distributes traffic to the server with the least amount of active connections and the quickest average response time.
- **Lowest Bandwidth Method**: distributes traffic to the server that is currently serving the least amount of traffic (measured in megabits per second, or Mbps).
- **Round Robin Method**: iterates through each server and sends each new request to the next server. When the last server in the cluster is reached, the load balancer starts over from the first server in the cluster.
- **Weighted Round Robin Method**: similar to the round robin, however it can account for servers with different processing capabilities. Each server in the cluster is assigned a weight that indicates its processing capability and servers with higher weights receive new connections before servers with lower weights.
- **IP Hash Method**: the IP hash method calculates the IP address of the requesting client and using this IP hash redirects the request to a server.

## Caching

Caching is the process of saving respones to be quickly served the next time that response is requested. Cache is limited and can be expensive but if managed properly can drastically improve the response time to your clients.

### Cache Invalidation
It's imperative to have an up-to-date-cache. When our data is updated, we must invalidate our cache. Let's take a look at three cache invalidation methods:

- **Write-Through Cache**: data is saved in cache as well as its corresponding database simultaneously, which allows for quick retrieval. Having cache and database parity ensures consistency, making the system more secure in the event of a power failure or system error. However, since each operation must be done twice (once in cache and once in DB) before it sends the response to the client, there is a higher latency.
- **Write-Around Cache**: write only to the DB and ignore the cache. Can prevent the cache from being inundated with write operations, however, the next time a read request is made, it'll cause a cache miss and the response must be read from permanent storage.
- **Write-Back Cache**: write solely to the cache before sending the response to the client. Provides the lowest latency, however it can lead to data-loss in the event of system failure as we only write data from cache to permanent storage at particular intervals.

### Cache Eviction Policies
How to determine which data should be removed from cache to reduce latency.

- **First-In-First-Out**: the first-accessed block is evicted regardless of how often it is accessed.
- **Last-In-First-Out**: most recently 
- **Least Frequently Used**
- **Most Frequently Used**
- **Least Recently Used**
- **Most Recently Used**
- **Random Replacement**

## Data Partitioning

Method by which a large database is segmented. Optimizing data partitioning can have a massive impact on the speed of your system.

- **Horizontal Partitioning**: also know as range-based partitioning and data sharding, different rows are placed into different tables.
- **Vertical Partitioning**: data is separated by schema. For example, in a school system, vertical data partitioning would allow to place all student information in one server, all class information on another server, and all teacher information on a third server. 



1 . General Requirements (core functionality)
2. Functional Requirements (technical details - cache size, how can we configure it)
3. Component Architecture
	1. high-level mock up
	2. dependency graph
4. Data Entities (won't have on frontend focused)
5. API Design (widget should be used in different places in the app)
6. Store Design (what state is the widget going to have?)
7. Optimization ()
8. Accessibility


## Tips for System Design for Front-End Devs

- Ask clarifying questions
- List functional and non-functional requirements
	- If designing Twitter, a functional requirement would be that users should be able to follow other users and post new tweets. A non-functional requirement may be that the system must be highly available; our system might want to prioritize replication of data.
- Unsure where to start, ask
- Unsure about something say "I am not sure how to proceed with this, I know it's not correct, but I will come back to this if I have time at the and and will move on to X"


# Heuristics and Shortcuts
## 1. Cap Theorem
---
![[cap-theorem.png]]
Most of the time, when designing distributed systems, we'll have support Partition Tolerance, because we want our system to work well even if network interruptions happen.
This leaves us with the choise of Consistency or Availability as our top priority.

## 2. Know what's likely to break
---
More or less the same question as: asking what the inefficiencies or the pain point of the system is. 

## 3. Don't commit yourself to a specific tech
---
Until you know for sure that it fits our needs.

