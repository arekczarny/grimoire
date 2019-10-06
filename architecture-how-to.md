# Architecture Done Right

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

Example C4 diagram
![Image Link2](https://raw.githubusercontent.com/arekczarny/grimoire/master/pics/c4-example.png "C4 Example")

#### C4 Tutorial
* [C4 Official FAQ](https://c4model.com/#faq)
* [Structurizr GUI tutorial](https://www.youtube.com/watch?v=OjRB8ol3JnI)
* [Strucrurizr diagram in Java code](https://github.com/structurizr/java/tree/master/structurizr-examples/src/com/structurizr/example)

#### C4 Tools
* [C4 Plugin for draw.io](https://github.com/tobiashochguertel/c4-draw.io)

## Architecture general references

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