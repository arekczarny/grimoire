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



## Architecture styles
Styles of Software Architecture their advantages and problems.

### Monolith

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

### References
* [Repository of ADRs templates and howto on GitHub \(1500 start\)](https://github.com/joelparkerhenderson/architecture_decision_record) \
* [Repository of example ARDs on GitHub \(116 stars\)](https://github.com/arachne-framework/architecture)
* [Mediawiki ADR examples on GitHub \(27 starts)](https://github.com/wikimedia/mediawiki-extensions-Popups/tree/master/docs/adr)

## Architecture Metrics

### Tools
* [Jenkins CI metrics plugin](https://github.com/jenkinsci/metrics-plugin)
* [ADR Tools on GitHub \(1663 stars\)](https://github.com/npryce/adr-tools/tree/master/src)

## Architecture Modeling Tools

### C4

C4 consist of following parts (abstractions):
* Code - class / function
* Component - set of classes that together form a contract
* Container - run environment for Components e.g. application server / web server / database
              communication between containers done via API (SOAP/REST/TCP/Messaging)
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