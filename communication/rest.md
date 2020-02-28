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
* [REST Security Cheat Sheet](https://owasp.org/www-project-cheat-sheets/cheatsheets/REST_Security_Cheat_Sheet.html)

## REST API design check points