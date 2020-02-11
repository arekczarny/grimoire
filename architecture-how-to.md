# Architecture Done Right

## How to select an Architecture for a specific software system

How to go through a known toolset for specifying correct architecture for the computer system.
Following steps and their output in form of code or documentation will aid this process: 

### Describe Architecture Drivers

* Limitations --> specify all limitations that the build system will be constrained with
* Quality attributes --> Those are **NONE** functional drivers that could cost a lot when moved to later phases of
system development. Some examples could be: scalability, observability, security, load e.g. 100-150 rps,
SLA system accessibility 99,99% that is 4m 23s of system downtime per month.

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





## System Architecture styles
Styles of Software Architecture their advantages and problems.

### Monolith

### Modular Monolith

### Distributed Systems

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

## Application Architecture styles

### Layered Architecture

Has specific layers that become boundaries in your code those usually are:

    1. Presentation
    2. Logic
    3. Persistence
    
Higher layer depends on the lower layer e.g. Presentation Layer depends on Logic Layer and Logic layer 
depends on Persistence Layer.
Problem here is that module present in Higher Layer should ideally depend on a single specific module of Lower Layer.
In practice this is not true and hard to achieve. Modules present in Higher Layer can access any module present in
Lower Layer and that is what is happening giving relation one High Layer module depending on many Lower Layer modules.
Making it quite a mess to maintain and develop further.

Solution would be to use Layered Architecture per module in the System rather than per whole System. This would naturally 
create boundaries that could not be broken e.g. module from Higher Layer would not be able to access module from Lower Layer 
of a totally different System module. 

**Problems of Layerd Architecture**

Shared Utilities --> this usually is a toolbox of specific to system classes that realize specific actions. More those 
utilities are mostly accessed by modules from all Layers in the Module. This looks like a good approach as we are creating
common Shared module the only thing to remember here is implementations in this module shoud be **Utilities** implementations
that are not providing any e.g. business logic.

#### Tier vs. Layer

Tier is a physical boundary where as Layer is a logical boundary as examples Browser, Application, Database are part of Tier.
Those could be mapped to deployment units in C4 that would be Containers. 
Presentation, Logic, Persistence parts of our System Module architecture are Layers.

#### Why use Layered Architecture

* Less complex implementation --> building on lower layer of code additional layers that provide wider functionality for
my implementation. Later I will not have to use Low level API and build everything always "from scratch" but I will have
some specialized implementations that are being build on the low level API to fulfill more complex behaviours with much
less effort from programmers side.

* Separation of concerns --> Single Responsibility Principle, if we have different reasons for a change or we might need
to change a tool being used in the solution e.g. Database then we change only the specific layer implementation without
a need to change others.

### Hexagonal Architecture

### Pipes and Filters Architecture

### Micro core Architecture 

### How to select specific Application Architecture style

### Testing Strategy based on selected Application Architecture style

### CQRS - Command Query Responsibility Segregation

Will be used for local BCs.

#### Blogs / Online Articles
* [CQRS Documents by Greg Young](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)
* [Race Conditions Don’t Exist - Udi Dahan](http://udidahan.com/2010/08/31/race-conditions-dont-exist/)


### Books
* [Design It!: From Programmer to Software Architect](https://www.amazon.com/dp/1680502093/)
* [Clean Architecture: A Craftsman's Guide to Software Structure and Design](https://www.amazon.com/dp/0134494164)
* [Software Architect's Handbook](https://www.packtpub.com/application-development/software-architects-handbook)


## Architecture Drivers
Architecture Drivers direct us to make concrete Software Architecture decisions. Those drivers are being described 
by specific Classes described below.

### Classes of Architecture Drivers


### Local Architecture Drivers
Those Drivers would be considered per e.g. Bounded Context. They would be one of the Classes described above but
local to a specific BC instead of the whole system.
This also implies that specific Architecture decision can be specific to a local Bounded Context instead of the whole
solution e.g. if we decided that we will use MVC design pattern for one sub system then it is *not* mandatory for 
all our BCs to be build based on the MVC layers. We can use a different design patter that solves our problem in
different BC. 

## ADL & ADR
Best practices and examples on how to create and maintain Architecture Decision Log and Architecture Decision Records.
Architecture Guild resources.

### References
* [Repository of ADRs templates and howto on GitHub \(1500 start\)](https://github.com/joelparkerhenderson/architecture_decision_record) \
* [Repository of example ARDs on GitHub \(116 stars\)](https://github.com/arachne-framework/architecture)
* [Mediawiki ADR examples on GitHub \(27 starts)](https://github.com/wikimedia/mediawiki-extensions-Popups/tree/master/docs/adr)
* [Architecture guild overview - Jakub Nabrdalik on GitHub](https://github.com/jakubnabrdalik/architecture-guild)


## Estimates (how to do them and when they really work)

Two main movements when it comes to Estimating or Not
1. \#NoEstimates
Estimates are not very precise. Delivered value is much more important than the cost of it. Estimation lead to dysfunctional
behaviour (too optimistic size that when not met leads to over hours, cutting on quality or event functionality).

2. \#YesEstimates
Estimates can be precise under certain conditions. Estimation of cost of making something is important for the business.
No Estimates makes Business people very uncomfortable and sort of alienated.  

### When Estimation works
* when we have done similar thing in the past
* when we understand how exactly the thing we want to build works
* when scope of work is small
* when during work requirements does NOT change
* when we don't have to wait for other people, teams work (our word does not depend on the result of others work)



### Blogs / Online Articles
* [Debiasing Training Improves Decision Making in the Field](https://journals.sagepub.com/doi/abs/10.1177/0956797619861429)

### Videos
* [12 Cognitive Biases Explained - How to Think Better and More Logically Removing Bias](https://www.youtube.com/watch?v=wEwGBIr_RIw)
* [James Shore - ESTIMATES OR NO ESTIMATES?](https://vimeo.com/145049619)
* [#NoEstimates - Allen Holub](https://www.youtube.com/watch?v=A1Bsq8HbaAY)

## Architecture Metrics

### Tools
* [Jenkins CI metrics plugin](https://github.com/jenkinsci/metrics-plugin)
* [ADR Tools on GitHub \(1663 stars\)](https://github.com/npryce/adr-tools/tree/master/src)

## Architecture Modeling Tools

### C4

C4 consist of following parts (abstractions):
* Code - class / function
* Component - set of classes that together form a contract
* Container - run environment for Components e.g. application server / web server / database communication 
between containers done via API (SOAP/REST/TCP/Messaging)
* System - Set of containers forming single system e.g. Browser + App Server + Database

C4 conists of following Diagrams:
* C1 - Context Diagram - who is using the system, why it was created, what integrations it has what those integrations do
* C2 - Container Diagram - Container diagram description uses (name, responsibility, technology, interaction, protocol)
* C3 - Component Diagram - for technical user working on the System.
* C4 - Class Diagram - UML (optional) standard stuff done the old school way

![Image Link2](https://raw.githubusercontent.com/arekczarny/grimoire/master/pics/c4-example.png "C4 Example")

#### C4 Tutorial
* [C4 Official FAQ](https://c4model.com/#faq)
* [Structurizr GUI tutorial](https://www.youtube.com/watch?v=OjRB8ol3JnI)
* [Strucrurizr diagram in Java code](https://github.com/structurizr/java/tree/master/structurizr-examples/src/com/structurizr/example)

#### C4 Tools
* [PlantUML C4](http://plantuml.com/)
* [C4-PlantUML plugin](https://github.com/RicardoNiepel/C4-PlantUML)
* [IntelliJ PlantUML Integration](https://plugins.jetbrains.com/plugin/7017-plantuml-integration)
* [C4 Plugin for draw.io](https://github.com/tobiashochguertel/c4-draw.io)


### UML

#### Tutorials
* [UML Basics - Polish](https://www.samouczekprogramisty.pl/podstawy-uml/)

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
* TraceID --> ID of the whole system workflow
* SpanID --> identifier of the request
* ParentSpanID --> identifier of the previous request in the requests chain
* Sampled --> a 0/1 information if particular trace is being sampled
* Headers X-B3-{element}

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