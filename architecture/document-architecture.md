# Document Architecture 

Ways to document system, software architecture in clean and understandable form.

## Architecture Drivers
Architecture Drivers direct us to make concrete Software Architecture decisions. Those drivers are being described 
by specific Classes described below.

### Classes of Architecture Drivers

* Limitations --> specify all limitations that the build system will be constrained with
* Quality attributes --> Those are **NONE** functional drivers that could cost a lot when moved to later phases of
system development. Some examples could be: scalability, observability, security, load e.g. 100-150 rps,
SLA system accessibility 99,99% that is 4m 23s of system downtime per month.

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
1. NoEstimates
Estimates are not very precise. Delivered value is much more important than the cost of it. Estimation lead to dysfunctional
behaviour (too optimistic size that when not met leads to over hours, cutting on quality or event functionality).

2. YesEstimates
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
between containers done via API (SOAP/REST/TCP/Messaging). Containers could (but not necessarily have to be deployed separately of each other)
* System - Set of containers forming single system e.g. Browser + App Server + Database

C4 conists of following Diagrams:
* C1 - Context (System) Diagram - who is using the system, why it was created, what integrations it has what those integrations do.
Description of all the systems (being build and existing systems that are being used by build systems) and its relations to the user(s)
and itself.  
* C2 - Container Diagram - Container diagram shows list of all containers of the system we are building. Containers of the sytem could be
Different API containers, Database, Web Server, Message Broker, Mobile Application etc. Container diagram description uses (name, responsibility, 
technology, interaction, protocol)
* C3 - Component Diagram - List of components of particular container of our system e.g. all components that are building our API container.
Component Diagram is for technical user working on the System implementation. Component diagram description uses (name, responsibility, 
technology, interaction (sync, async), protocol).
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

### Diagraming tools

* [Diagrams.app](https://diagrams.app/) For MacOS, paid 20$
* [StarUML 3](http://staruml.io/) Cross OS, 90$
* [Whimsical](https://whimsical.com/) Online, Flowcharts, Wireframes Free and 10$ month
* [Lucidchart](https://www.lucidchart.com/pages/) Online, Free + 8$ month. Pretty powerful for all kinds of diagramming
* [PlantUML](https://plantuml.com/) Online + Java app, free, loads of diagrams covered