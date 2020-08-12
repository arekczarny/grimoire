# Identity Management & Access Control

## Mechanisms for Authentication

### Single Sign-On (SSO) 
* single login into system
* centralized data store with users or access server
* using protocols such as LDAP or Kerberos

### Federated Identity
* SSO on many organizations level
* set of standards for exchange of identity
* user does not login into the application directly. He is redirected to IdM (Identity management system)

### Kerberos
* it is a protocol used for Authentication and Authorization
* main purpose is NOT to send user password anywhere (for authentication request to KDC server hash of the password is being sent)
* it is an SSO mechanism where user logs in only once
* based on trusted 3rd side
* its a mutual authentication mechanism. Bots user and the service to which users log in must prove they are valid

#### Based on 3A principle
* Authentication
* Authorization
* Auditing

#### Components of Kerberos
* KDC (Key Distribution Centre) which contains:
* AS (Authentication Server)
* TGS (Ticket Granting Server)
* Principal that represent the user of the system
* Service (server the system contacts with)
* Realm (Domain) e.g. DEVELOPER.COM
* Principal (User) e.g. arek@DEVELOPER.COM, host/java.developer.com@DEVELOPER.COM

#### Cons of Kerberos
* constant availability of KDC
* sensitive to time synchronization issues
* in case of TGS hash breach. Attacker can act as any user in the system.

### Blogs / Online Articles

* [What is Strong Authentication?](https://www.okta.com/identity-101/what-is-strong-authentication/)

## SAML 2.0

## OAuth 2.0 & OpenID Connect

* [RFC 6749 The OAuth 2.0 Authorization Framework](https://tools.ietf.org/html/rfc6749)
* [OAuth 2.0 Servers](https://www.oauth.com/)
* [Auth0 resources](https://auth0.com/)

### Blogs / Online Articles

[Diagrams And Movies Of All The OAuth 2.0 Flows](https://medium.com/@darutk/diagrams-and-movies-of-all-the-oauth-2-0-flows-194f3c3ade85)
[Wprowadzenie do OAuth 2.0 i OpenID Connect - Aleksander Żelazny](https://www.youtube.com/watch?v=9LRZXg0NK5k&utm_source=jvm-bloggers.com&utm_medium=link&utm_campaign=jvm-bloggers)

## JWT 

## Edge Services

## Securing API

### Blogs / Online Articles

* [API Authorization at Auth0](https://auth0.com/docs/api-auth)

## IdM Providers

### Auth0

* [Get Started - Learn the basics of Auth0](https://auth0.com/docs/getting-started)


