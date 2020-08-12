# Application Architecture styles

What are the Application Architecture styles and which one to choose for specific software.

## Layered Architecture

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

### Tier vs. Layer

Tier is a physical boundary where as Layer is a logical boundary as examples Browser, Application, Database are part of Tier.
Those could be mapped to deployment units in C4 that would be Containers. 
Presentation, Logic, Persistence parts of our System Module architecture are Layers.

### Why use Layered Architecture

* Less complex implementation --> building on lower layer of code additional layers that provide wider functionality for
my implementation. Later I will not have to use Low level API and build everything always "from scratch" but I will have
some specialized implementations that are being build on the low level API to fulfill more complex behaviours with much
less effort from programmers side.

* Separation of concerns --> Single Responsibility Principle, if we have different reasons for a change or we might need
to change a tool being used in the solution e.g. Database then we change only the specific layer implementation without
a need to change others.

## Hexagonal Architecture

###
* [Hexagonal Architecture by example - a hands-on introduction - AllegroTech](https://allegro.tech/2020/05/hexagonal-architecture-by-example.html?utm_source=jvm-bloggers.com&utm_medium=link&utm_campaign=jvm-bloggers)

## Pipes and Filters Architecture

## Micro core Architecture 

## How to select specific Application Architecture style

## Testing Strategy based on selected Application Architecture style

## CQRS - Command Query Responsibility Segregation

Will be used for local BCs.

### Blogs / Online Articles
* [CQRS Documents by Greg Young](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)
* [Race Conditions Don’t Exist - Udi Dahan](http://udidahan.com/2010/08/31/race-conditions-dont-exist/)


## Books
* [Design It!: From Programmer to Software Architect](https://www.amazon.com/dp/1680502093/)
* [Clean Architecture: A Craftsman's Guide to Software Structure and Design](https://www.amazon.com/dp/0134494164)
* [Software Architect's Handbook](https://www.packtpub.com/application-development/software-architects-handbook)