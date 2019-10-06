# Domain Driven Design (DDD) 

## Big Picture Event Storming

### Examples
* [Awesome Eventstorming - Mariusz Gil](https://github.com/mariuszgil/awesome-eventstorming)

## Process Level Event Storming


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


## Books
* [Hands-On Domain-Driven Design with .NET Core: Tackling complexity in the heart of software by putting DDD principles into practice - Alexey Zimarev](https://www.amazon.com/Hands-Domain-Driven-Design-NET-ebook/dp/B07C5WSR9B/ref=sr_1_1?crid=KJLST55P7X6P&keywords=hands-on+domain-driven+design+with+.net+core&qid=1563642184&s=books&sprefix=hands-on+domain+dri%2Cstripbooks-intl-ship%2C300&sr=1-1)
* [Implementing Domain-Driven Design - Vaughn Vernon](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577)
* [Domain-Driven Design: Tackling Complexity in the Heart of Software - Eric Evans](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)
* [Domain Driven Design Quickly](https://www.infoq.com/minibooks/domain-driven-design-quickly/)
* [Domain Modeling Made Functional: Tackle Software Complexity with Domain-Driven Design and F# - Scott Wlaschin](https://www.amazon.com/Domain-Modeling-Made-Functional-Domain-Driven-ebook/dp/B07B44BPFB)

## Videos
* [From legacy to DDD - Andrzej Krzywda - Boiling Frogs 2016](https://www.youtube.com/watch?time_continue=38&v=MzV2vGSTpo8)

## Examples
* [Real DDD project with hands on examples on GitHub - Jakub Pilimon](https://github.com/ddd-by-examples/library)