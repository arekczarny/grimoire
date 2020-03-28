# System Architecture styles
Styles of Software Architecture their advantages and problems.

## Videos / Presentations

* [Architectures That Scale Deep - Regaining Control in Deep Systems by Ben Sigelman](https://www.infoq.com/presentations/properties-deep-systems/)

## Monolith

## Modular Monolith

[Modular Monolith](modular-monolith.md)

## Distributed Systems

[Microservices](microservices.md)

It's a computer system implemented as a set of independent components that communicate with each other over some
type of network protocol.

**Advantages of Distributed Systems**
* Scalability - each component of the system can be independently scaled. 
* Resilience
* Heterogeneous technology - different tech stack can be used to implement certain components of the system. Here we are
able to select the best tool/language for the job without being limited by tech stack of other components.
* Laws & Security - much easier to make Laws compliant of specific isolated components that the whole system. This allows
for components that must be compliant with certain rules, regulations to be enhanced with specific features without impacting
rest of the system (components).
* Productivity - specifying teams to work on certain components. 

**Disadvantages of Distributed Systems**
* Complexity of Infrastructure - many components with many pipelines that needs to be controlled and deployed.
* Transaction less - 
* Changes that span across many components makes things harder
* Making all this secure. Loads of network communication going from one component to another all this needs to be 
properly secured!
* Troubleshooting and Debugging not an easy task
* Running locally with so many different components again not an easy and pleasant thing to do  

## Self-Contained Systems

"The Self-contained System (SCS) approach is an architecture that focuses on a separation of the functionality into many independent systems, 
making the complete logical system a collaboration of many smaller software systems."

### Blogs / Online Articles

* [Self-contained System (SCS)](https://scs-architecture.org/index.html)
