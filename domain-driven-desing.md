# Domain Driven Design (DDD) 

## Big Picture Event Storming

Allows for horizontal exploration of our business domain. In the end participants can cluster discovered events into
Bounded Contexts. 

### Examples
* [Awesome Eventstorming - Mariusz Gil](https://github.com/mariuszgil/awesome-eventstorming)

## Process Level Event Storming

## Design Level Event Storming

Allows for exploration of construction elements that in the end will allow to create domain model of the designed solution.
In DLES we are exploring specific Bounded Contexts and are limited by its boundaries. It is contrary to BPES vertical
exploration of system being designed.  

Result of DLES:
* Events --> make us think about the behaviour of the system not its structure. Event can be triggered by Command. They can
* also be some scheduled activities or being triggered by some other events. 
* Commands --> are the causes for Events in the system.
* Actors --> are users of the system that are executing Commands. Actors can be People or other Systems. 
* Rules --> rules are discovered when looking at the flows of communication starting from an Actor calling Command and then
finding some business rules that will allow called Command to trigger (or not) specific event or some other event.
* Policies --> describe that certain domain event can cause other part of the system to be interested in it. E.g. when 
an event for Activation of an account is triggered the other part of the system that is responsible for sending an invoice
might need to know this. Policies add separation of concerns in the system. We don't want to have a Activation of an account
command to do too much including invoicing. 
* Read Models --> are Views that our system is using to answer specific queries. View is reflection of current system state.
Which indicates that View is representing all the events that had happened in the system until generation of the View. 
* Hot Spots --> places in the system being designed where domain experts (business people) are not clear on how the system
should react or what should it do in this specific case.

### Advantages
* Very quick discovering of the domain language
* Good visualization of what is happening and how this is happening in designed system
* Exploration of particular domain/BC

## Behavior-Driven Development

This is a technique that allows for much better understanding of business problem at hand. This is happening through creation
of automated examples (tests) that serve as \"live\" documentation of the system. Those automated examples are also a tool
to guide our Model so it would fulfill all business requirements and would stay simple (would do only what it it required
to do and nothing more)
Tools used for BDD in different languages are:
- Cucumber
- Spock
- JBehave
- Jasmine
- NBehave
- Behat

## Bounded Context
Bounded Context - Bounded as it has clearly stated boundaries \(borders, lines\). Inside we have Domain Model.
Domain Model is not being shared between other Bounded Contexts. If there is a need to communicate between Bounded 
Contexts (sharing data) this *MUST* be done via API \(interface, contract\). Each Bounded Context has its own Domain
Language described by specific Subdomain problems. Each Bounded Context (Sub System) has its own Ubiquitous Language.
Context as the boundaries of Bounded Context are linguistic boundaries within specific Context e.g. a Book will mean  
something different if talked about in the Contexts of Delivery Subdomain and Invoicing Subdomain. Everyone knows its 
meaning because they talk about it within certain Context. All in all Bounded Context solves a problem of its Subdomain.

### Ubiquitous Language
Ubiquitous Language - it's being used in the Sub System documentation, in talks about Sub System between Domain Experts  
or Engineering folks it is also present in the code base. It evolves through the time when talking to Domain Experts, 
very important communication platform as everybody know exactly what they are talking about. Thanks to that Domain Model
becomes much more "readable" and maintainable. That means that Domain Model should reflect concepts/words used by 
Domain Expert rather than an Engineer e.g. no more SthUtil, SthService, SthManager, SthFactory :). Don't use such
language in the Domain Model contracts \(high level of abstraction\) if necessary use it in as low level implementation
detail.
There would be many Ubiquitous Languages within the company based on the number of Bounded Contexts in the domain.

### Subdomain & Bounded Context
Bounded Context solves a problem of it Subdomain. Ideally there would be one Bounded Context per Subdomain. 
This situation can be found in the new Greenfield projects where we know exactly how to model our domain.
In old projects we might have Bounded Contexts that are "leaking" between different Subdomains doing too much. 
This also might be because of evolving Subsystem and changing requirements where new Subdomains are being discovered
that are overlapping others or are extension to previously defined Subdomains and are using theirs Bounded Contexts
to solve their problems.

### Deployment Architecture & Bounded Context.
What is really a Bounded Context when it comes to implementation and how it is being deployed? Is that a single 
Microservice or maybe it is a module in a Monolith? 

### Validation of Bounded Context's boundaries

####Heuristics
1. Context Autonomy
* Does our Context can "make decisions" on its own?
* Does our Context must "ask" other Bounded Contexts for permission to "make decision"?  
Bounded Context must be self sufficient and must be able to make decisions on its own. If that is not the case then
it might indicate that our decision on selecting Bounded Context is wrong and we have too much level of granularity.

2. Number of Bounded Contexts in business process
* How many Bounded Contexts plays a part in a single business process?
The least BC in the single business process the better. If there are many BCs involved that must integrate with each
other and especially when those BCs are calling each other several times that is sign of a bad architecture decisions. 
When caching, repeated calls comes into play that is yet another technical way to cover the problem.   
This might mean that the boundaries are incorrect and needs to be revisited.

3. Look for data/information that change at the same time
If in the design some data *must* change in two different places (BCs) at the same time (Atomic change) it means that
there should be only *one* Bounded Context made out of those two.

4. Look for data/information that are being used together
If there is a need for e.g. two BCs to query each other for a data this needs to be revised. We could try to look at
the implementation from the different perspective and replace existing BCs with the new ones that will have all what
they require within it.

5. Creating Bounded Context helper questions
- What is BC responsibility?
If there are many sentences used to answer the question then it might mean that the BC does too much and needs a split.
- How many integrations does the BC have?
How many and why it has them also to what internal/external systems those integrations are being made.
Integration to an external system limits BCs autonomy much more than an integration to internal system.
- Is there a single source of truth for specific information/concept during a business process?
If there is a BC that is an owner of the information/concept if it is not then we have lost some BC and we have to  
add it.
- Does schizophrenic BC exist?
When BC needs to have some conditional logic to figure out "who" it is. Example when BC has a logic to do certain
actions for Individual Client and Corporate Client. In that case there should be two different BCs one for Individual
and one for Corporate Client handling.
- Look for anti-requirements?
Anti-requirement is a requirement that does not have any Business value \(sense\). Look for rules that could break our
BCs boundaries by asking questions to the end user about requirements that could possibly cross boundaries of our BCs.

### Blogs / Online Articles
* [The Bounded Context Explained](http://blog.sapiensworks.com/post/2012/04/17/DDD-The-Bounded-Context-Explained.aspx)
* [BoundedContext - Martin Fowler](https://www.martinfowler.com/bliki/BoundedContext.html)

## Implementation Models derived from DLES

### Anemic model 

Model for not very complex Sub-domain (BC). Usually implemented with Layered Application Architecture. Where model reflects
data structure of our Database and Domain Objects use getters and setters for checking and setting of their state.

### Rich model

Model for complex Sub-domain especially if there are still unknowns (hot spots) and we know that this sub-domain
will evolve and will be under heavy changes. Rich model usually is best suited when Hexagonal Application Architecture
is used to implement specific part of the system.

### Aggregate

Collection of Objects that is cohesive and sets the boundaries of transaction is called Aggregate in Tactical DDD.
Aggregates also verify the immutable parts of the system. Communication with Aggregate is **ONLY** possible via
object that is called Aggregate Root.
Aggregate does not have any reference to another Aggregate. During single transaction we must modify only a single
Aggregate. Aggregates are also units of persistence (they are being saved as a whole) this allows for partitioning and
much better scalability of the system. 
Aggregates are being persisted by implementing Repository Pattern. It can be persisted in Relational or Document Database.

Through an Aggregate we put together all the rules that have impact on its state. It is not about particular data (like in DAO)
it is more about rules that eventually will provide everything for an Aggregate to be cohesive! 
Aggregates have full knowledge on how and when generate domain events in the system. Aggregates are responsible for creation
of domain events (not Domain /Application Services)

## Tactical DDD

### Construction Elements

1. **Behaviour**

* Events
* Commands
* Queries (Views)
* Rules (immutable) and Aggregates
* Policies

2. Structure

* Values (Value Objects) --> **does not** change in time. It's value is it's identity. VO are attributes that describe
Entities of our domain.
* Entities --> entities do change in time although they do have its identity independent from its attributes. Entities
do have their own life cycle. e.g. a car that gets older, is being repaired and changed its colour its still the same car
identified by the unique VIN number thus having its identity independent from what changes it went through in its lifecycle.
* Domain Services --> operations that are not part of either Entities nor Value Objects. Domain Services do not have state
and are mostly used to encapsulate  algorithms or computations. 

2. Life cycle

* Factories --> being used to reate complex structures. Factories are purely technical notion and are not present in
our domain. If creation of some Structural elements is complex it could be beneficial to extract it into Factory.
* Repositories --> their responsibility is to persist (save) and read Entities and its Value Objects. Not present in the
domain either, purely technical notion. 

## Books
* [Hands-On Domain-Driven Design with .NET Core: Tackling complexity in the heart of software by putting DDD principles into practice - Alexey Zimarev](https://www.amazon.com/Hands-Domain-Driven-Design-NET-ebook/dp/B07C5WSR9B/ref=sr_1_1?crid=KJLST55P7X6P&keywords=hands-on+domain-driven+design+with+.net+core&qid=1563642184&s=books&sprefix=hands-on+domain+dri%2Cstripbooks-intl-ship%2C300&sr=1-1)
* [Implementing Domain-Driven Design - Vaughn Vernon](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)
* [Domain-Driven Design: Tackling Complexity in the Heart of Software - Eric Evans](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)
* [Domain Driven Design Quickly](https://www.infoq.com/minibooks/domain-driven-design-quickly/)
* [Domain Modeling Made Functional: Tackle Software Complexity with Domain-Driven Design and F# - Scott Wlaschin](https://www.amazon.com/Domain-Modeling-Made-Functional-Domain-Driven-ebook/dp/B07B44BPFB)
* [Domain-Driven Design: Tackling Complexity in the Heart of Software](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)

**Event Storming**
* [Introducing EventStorming - Alberto Brandolini](https://leanpub.com/introducing_eventstorming)

## Videos
* [DDD playlist youtube - great content on DDD in one place](https://www.youtube.com/playlist?list=PLC63ae3uCHHYZ2hb_pc6VlQabpi1DS7Yf&app=desktop)
* [Language in Context: And How Do We Go Forward From Here? - Eric Evans](https://www.youtube.com/watch?v=kjMZVYdwucs)
* [From legacy to DDD - Andrzej Krzywda - Boiling Frogs 2016](https://www.youtube.com/watch?time_continue=38&v=MzV2vGSTpo8)

## Examples
* [Real DDD project with hands on examples on GitHub - Jakub Pilimon](https://github.com/ddd-by-examples/library)
* [Modular Monolith with DDD](https://github.com/kgrzybek/modular-monolith-with-ddd)