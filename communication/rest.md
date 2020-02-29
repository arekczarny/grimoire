# REST API

Best practices for how to create REST API.

## REST Basics

REST is a REpresentational State Transfer. A standard for HTTP Client-Server communication.

REST has a following constraints:
    
    1. Separates Client and Server
    2. Ideally it is Stateless
    3. Has uniform interface
    4. It's responses are Cachable
    5. Layerd System
    
**Client Server separation**

This constrain fits well with distributed application structure. In this model Server provides
functions or services. Client on the other hand initiates requests for those services.

**Stateless** 

Each new request should be an independent transaction that is completely unrelated to any previously
issued request. It might use data coming in response from previous requests but Server should not hold
any session on its end that would needed to be used for processing of next incoming requests.
Each request from a Client must contain all data needed by the Server to handle the request.
Session state should be kept on the Client side.
In case session state needs to be stored on the Server side it should be moved to another service such
as database or distributed cache. This in turn should allow for simplification of clustering of the system.
Both Server and Client should be supporting HTTP 401 Unauthorized to handle cases of session invalidation
or server holding session in cache going down.

**Caching**

In order to eliminate part of Client-Server communication Server should use appropriate HTTP headers
and add them to the response in order to describe cache metadata. When such responses are being handled
by Clients they can be cached and thus do not issue following requests for cached resource.
Point to note here is that some of the browsers e.g. IE are doing aggressive caching which if not
handled properly might be source of "dirty reads" of system resources.

**Uniform Interface**

There are certain factors that determine the uniform interface of a REST service:
* REST is Resource Based --> resource is identified by URI and its ID
* REST Resource is separated from its representation (XML, JSON, HTML, Text)
* REST Resource is manipulated via its representation --> Client which holds resource representation
and its metadata can modify or delete this resource
* REST has self-descriptive messages --> Each request/response must include all information to describe how to process
the message (MIME, cache headers etc.)
* REST HATEOAS --> Hypermedia as the Engine of Application State where response contains dynamic hypermedia for operating
on resources e.g.:
```js
HTTP/1.1 201 Created
Location: http://api.dupa.com/users/12345
{
    "name": "Arek",
    "links": [ {
        "rel": "self",
        "href": "http://api.dupa.com/users/12345"
    } ]
}
```

**Layered System**

Client is not aware where it is directly connected to the end Server. There are intermediary network devices through
which Client's request goes through that might be Load Balancer, Caches, Firewalls, API Gateways etc. 
## REST Design Considerations

### REST Resource Naming

```js
http://{host}:{port}/{collection}/{id}/{element}
```

* host --> domain of the server hosting REST endpoint
* port --> port on which REST endpoint is being exposed on the server (could be empty when default HTTP(S))
* collection --> must be plural e.g. users, books, orders
* id --> unique identifier of a resource e.g. 12345, DES232WQ, LOT23432
* element - subordinate element (could be collection) e.g. name, pets, seats
 
Examples:
```js
http://api.dupa.com/users/12345/name
http://api.dupa.com/flights/LOT23432
http://api.dupa.com/flights/LOT23432/seats
http://api.dupa.com/flights/LOT23432/seats/10C
```
**IMPORTANT: DO NOT include operations (verb) in URI (like /flights/LOT23432/cancel)**

### REST HTTP Methods

* GET - retrieve resource
* POST - create new resource
* PUT - create resource when client can decide resource URI or update existing resource
* DELETE - delete resource
* OPTIONS - resources information

**What are idempotent and/or safe HTTP methods?**

**Idempotent Methods** --> making multiple identical requests has the same effect as making a single request.
Idempotency is important in building a fault-tolerant API. 

**Safe Methods** --> Calling the method does not modify the resource and cause side effects.  Using GET or HEAD on a resource URL, 
should NEVER change the resource. Safe methods are methods that can be **cached, prefetched** without any repercussions 
to the resource.
```
HTTP Method | Idempotent | Safe
-------------------------------
OPTIONS     |    yes     |  yes
GET         |    yes     |  yes
HEAD        |    yes     |  yes
PUT         |    yes     |  no
POST        |    no      |  no
DELETE      |    yes     |  no
PATCH       |    no      |  no 
```
### REST HTTP Status Codes
```
20x - all good bro
30x - don't ask me ask somewhere else
40x - it's your fault bro
50x - sorry it's our fault
```
## REST Caching
## REST Content Negotiation
### HTTP Headers
* cache-control: public, max-age=0, no-cache
    * public / private (public allows shared caches (LB/FW/CDN))
    * no-cache (on page reload)
    * no-store (also on history back)
    * max-age
    * s-maxage - all s-* paramters are for shared caches
    
* Entity Tag (ETag)

## REST Security

### Blogs / Online Articles
* [REST CookBook](http://restcookbook.com/)
* [REST Security Cheat Sheet](https://owasp.org/www-project-cheat-sheets/cheatsheets/REST_Security_Cheat_Sheet.html)

## REST API design check points