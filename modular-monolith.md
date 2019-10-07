# Modular Monolith

## Standard Monolith
Monolith system that was implemented as a single application \(single deployment unit\). Monolith is a self sufficient
system that usually is not very modular.

### Advantages of Monolithic system:
* fast and mostly reliable communication between Monolithic application components
* transactional \(ACID\)
* secure communication \(everything stays within Monolith after initial request is accepted\) much harder for an attacker to 
intercept any messages from within Monolithic application.
* simple deployment architecture \(infrastructure\)
* much easier to develop in the beginning 

### Disadvantages of Monolith:
* not very resilient system and very fragile \(memory leak, high CPU utilization all affects the whole system not just its
single functionality and can also kill the whole system\)
* limited scalability of the system \(performance, infrastructure and productivity\)
* super hard to maintain and make any quick fixes and add new features

## Modular Monolith

Modular Monolith is still a single deployment unit although it has certain characteristics that makes it much better
choice than standard Monolithic system.
Modularity is the thing that makes Modular Monolith different from its cousin. Modularity is achieved by specifying 
autonomic business modules that have clear boundaries between themselves. It is worth to emphasise that those Modules
are autonomic and independent from each other.

### Advantages of Modular Monolith

* it is much easier to test such system, concentrating on specific modules and what they should be doing rather than
the whole system
* properly created boundaries between modules give an opportunity for those Modules to be migrated into Microservices
architecture. Modules should be autonomic and independent from the other modules in the system. This feature allows
to easily extract them from the Monolith and create a microservice.
* it is much better to maintain as there are autonomic modules that when necessary needs to be fixed without impacting
rest of the system. When single module is being fixed or changed only this module needs to be tested.

### Disadvantages of Modular Monolith
* data duplicaton
* much harder to keep the whole solution consistent
* limited usage of foreign keys

## Breaking apart the Monolith

### References
* [Building common libraries that aren't garbage (PL) - Piotr Betkier - Confitura 2016](https://www.youtube.com/watch?v=jLYMa5E4-z4&feature=youtu.be)