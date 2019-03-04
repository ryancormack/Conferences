# Resiliency and Availability Design Patterns - Steven Bryen

## Designing for availability

Design for the known unknowns, and design for the unknown unknowns.

### Multi AZ for Maximum Availability
Typically less than 2ms latency between AZ's and less than 0.5ms between data centers in the same AZ

Using 3 AZ's, and 150% of peak load allows for instant recovery for an AZ loss.

### Decoupling and async
Using queues or streams allow for easy decoupling.

SQS can have high and low priority queues

### Retries and timeouts
Timeouts allow you to fail fast on slow failures. Timeouts are key and important to ensure flooding services doesn't happen

Retries and exponential backoff allow backends or other services to try and recover.

Exponential backoff is good, but adding a jitter improves performance even more.

### Database Federation
Usig different database across the whole stack allows you to easily pick the best storage solution for the application, and stops everything failing at once due to a single bad query etc

Database sharding with read replicas also improves database reliability. Read and write separation imrpoves this even more. Ensuring reads are still available even if writes are not

#### Shuffle Sharding

Aims to stop a cascading failure. When one service takes out a node, it would usually failover to the next node, and then taking that out.

Overlapping nodes that services can use massively reduces the blast radius

This is used to balance Lambda/Firecracker across underlying instances

### Load Shedding
Don't be overly optemise and take on more than you can. KISS for features

Avoid false positives

Prioitize pings. Don't reject pings on load balancers etc. They need to respond to health checks

### Chaos
Creating resilience through destruction

Test things for worst case failures. Be prepared for the unexpected.

[Chaos engineering](https://principlesofchaos.org)

Start with testing chaos at a small level. Start at application failure, then work up to host/instance, then resources like cpu/memory, Region failures.

#### Further reading
Adrian Hornsby Twitter and Medium

Injecting chaos on Lambda using Layers.