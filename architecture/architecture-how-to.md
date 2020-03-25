# Architecture Done Right

My framework for how to approach all system architecture activities from the beginning to an end.

## How to select an Architecture for a specific software system

How to go through a known toolset for specifying correct architecture for the computer system.
Following steps and their output in form of code or documentation will aid this process: 

### Describe Architecture Drivers

Describe all Architecture Drivers that would be steering towards particular System Architecture. Later on those
drivers should also be used to create metrics in order to become measurable.

### Architecture Metrics

Add metrics to previously discovered Architecture Drivers. Metric is quantification of specific driver.
Metric should provide clear understanding of particular driver meaning.  

### Select Architecture Style for System

Based od the drivers described in previous section select specific Architecture Style for system that will be build.
Those could be:

    1. Monolith
    2. Modular Monolith
    3. Microservices
    etc.

Document advantages and disadvantages of selected Architecture style so everyone in the team and later on people joining 
the team have no doubts that the style is correctly selected and all pros and cons of the selection were evaluated.

### Document and visualize selected Architecture

C4 and ADL & ADR.

### Select Application Architecture per specific module

## Architecture general references

### Autonomy

Types of Autonomy in Software developent:
1. Business
2. Technical
3. Technological

**Business Autonomy**

* Allows to develop software products independently of each other
* Different products have different SDLC and calendar of events (releases, planning etc.)
* Higher product specialization directly influences code complexity or rather less of code complexity and more readable
code

**Technical Autonomy**

Technical Autonomy enables product teams to separate components depending on:
1. the need to scale
2. specific security requirements 

**Technological Autonomy**

* Enables teams to select the best tools for a given problem
* Enables teams to select different programming languages
* Enables to select different Operating systems

### Distributed Tracing

* B3 Propagation (Zipkin) introduces certain identifiers and headers to make tracing bit more precise and accurate:
* TraceID --> ID of the whole system workflow (does not change for the whole workflow)
* SpanID --> identifier of the specific request (for the first request SpanID == TraceID)
* ParentSpanID --> identifier of the previous request in the requests chain (SpanID of the system that made a call to our system)
* Sampled --> a 0/1 information if particular trace is being sampled (if the log data should go to the system responsible for
gluing all the traces together)
* Headers X-B3-{element}

#### Blogs / Online Articles
* [B3 Propagation GitHug](https://github.com/openzipkin/b3-propagation)
* [Śledzenie komunikacji w systemach rozproszonych - Polish](https://pater.dev/sledzenie-komunikacji-w-systemach-rozproszonych-z-wykorzystaniem-spring-cloud-sleuth-zipkin/)
* [Distributed Tracing with Spring Cloud Sleuth and Spring Cloud Zipkin](https://spring.io/blog/2016/02/15/distributed-tracing-with-spring-cloud-sleuth-and-spring-cloud-zipkin)

### Event Driven Systems

#### Examples
* [On Eventual Consistency and REST](http://pillopl.github.io/eventual-consistency-and-rest/)

#### Books
* [Designing Event-Driven Systems - Ebook Online](https://www.confluent.io/wp-content/uploads/confluent-designing-event-driven-systems.pdf)

### Conway Law
Organizations which design systems ... are constrained to produce designs which are copies of the communication
structures of these organizations - M. Conway

Make sure that we preserve Bounded Contexts created via specific team setup (one team per BC) or by preserving the 
boundaries of BC in case different teams are required to work on different BCs (this can be achieved by automatic,
programmatic use of software tools e.g. Maven modules).

#### Blogs / Online Articles
* [How Do Committees Invent? - Melvin E. Conway](http://www.melconway.com/Home/Committees_Paper.html)
* [Exploring the Duality between Product and Organizational Architectures](https://hbswk.hbs.edu/item/exploring-the-duality-between-product-and-organizational-architectures-a-test-of-the-mirroring-hypothesis)

### Books
* [Design It!: From Programmer to Software Architect](https://www.amazon.com/dp/1680502093/)
* [Building Evolutionary Architectures: Support Constant Change](https://www.amazon.com/dp/1491986360)
* [Patterns of Enterprise Application Architecture - Martin Fowler](https://martinfowler.com/books/eaa.html)

### Blogs / Online Articles
* [Software Architecute is Overrated](https://blog.pragmaticengineer.com/software-architecture-is-overrated/)
* [TICK Stack](https://www.thoughtworks.com/radar/platforms/tick-stack)
* [Enterprise Integration Patterns](https://www.enterpriseintegrationpatterns.com/index.html)
* [How to learn Software Design & Architecture](https://khalilstemmler.com/articles/software-design-architecture/full-stack-software-design/)
* [Less is more](http://www.bredemeyer.com/pdf_files/MinimalistArchitecture.PDF)
* [Who needs an Architect \(Fowler\)](https://martinfowler.com/ieeeSoftware/whoNeedsArchitect.pdf)

### Videos

## APIs best practices 

### Blogs / Online Articles
[APIs as infrastructure: future-proofing Stripe with versioning](https://stripe.com/en-pl/blog/api-versioning)