# Domain Driven Design (DDD) 

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

## Books
[Domain-Driven Design: Tackling Complexity in the Heart of Software - Eric Evans](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215)\
[Hands-On Domain-Driven Design with .NET Core: Tackling complexity in the heart of software by putting DDD principles into practice - Alexey Zimarev](https://www.amazon.com/Hands-Domain-Driven-Design-NET-ebook/dp/B07C5WSR9B/ref=sr_1_1?crid=KJLST55P7X6P&keywords=hands-on+domain-driven+design+with+.net+core&qid=1563642184&s=books&sprefix=hands-on+domain+dri%2Cstripbooks-intl-ship%2C300&sr=1-1)\
[Domain Modeling Made Functional: Tackle Software Complexity with Domain-Driven Design and F# - Scott Wlaschin](https://www.amazon.com/Domain-Modeling-Made-Functional-Domain-Driven-ebook/dp/B07B44BPFB)

## Blogs / Online Articles
[The Bounded Context Explained](http://blog.sapiensworks.com/post/2012/04/17/DDD-The-Bounded-Context-Explained.aspx)

## Examples
[Real DDD project with hands on examples on GitHub - Jakub Pilimon](https://github.com/ddd-by-examples/library)