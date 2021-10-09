# Documentation
## What if clients not just communicate with APIs but also fix themselves and discover new APIs without human intervention.
SuperSDK : An API client layer on top of the existing APIs. Higher order APIs that decouples clients from server at business domain level.

## Problem1
API integration is done using imperative coding by hard coding URL and vocabulary. API response is hard coded and then transformed in to internal representation. This approach needs constant human intervention whenever the providers API changes or moving to a new API service provider. 
This also makes harder to update remote clients  and clients to dynamically use multiple service providers for same functionality to avoid single provider point of failure.

![alt text](https://github.com/SuperSDK/Documentation/blob/main/Block_Diagram.png?raw=true "Block Diagram")

## Problem 2
There is a very little notion of shared Vocabulary/ Application affordances and transitions among the API service providers.  
Example: In programmableweb (API Aggregator) there are approximately 400 APIs in Address category with hardly any shared vocabulary.

[Schema.org](http://schema.org/) and Dublin Core, Hypermedia Micro formats, activity streams tried to solve the problem of shared vocabularies. This only solves a part of problem of modeling the “What“

Ex: What is a Person, hProduct , Vcard

Vocabularies does not define the transitions “How“ to interact.  Using the language like ALPS alps.io  helps to define the state and transition for every domain 
In other words defining an Abstract class for a Domain by defining the vocabulary and action in that domain i.e; Communication Domain - Contact, send Emails, send SMS etc. 

This definition contract can be used both by the providers and clients to write their business logic independently and evolve independently.  
This can also enable sharing the vocabulary among multiple services. 

example: [Person](schema.org/person) can be used for contacts, user, matchmaking, giftlist etc.

## Problem 3
No standard way to share data between multiple services without human intervention.

## Key Objectives of SuperSDK :
- Easy to use/integrate with existing vendor APIs. 
- Resiliency of clients with vendor API changes.
- Possibility to use redundancy in providers to avoid single provider point of failure.
- No need to change the client code with changing the vendors
- Independent and effortless evolution of clients and servers
- Avoid human errors in API integration
- Avoid vendor API lock in (Client implementation Agnostic to vendor implementation)
- Interoperate between multiple datatypes(REST to GraphQL , GraphQL to REST) irrespective of vendor provided datatype.
- Abstract away API implementation by design. 
- Real time switching of vendors without client side code changes.
- Make API data interoperable among  multiple services without human intervention.

## Plan to Achieve this
Developing a client SDK that can be a single interface between client and API service provider.
1. Using a profile descriptive language to describe the affordances and semantics for specific domains.
Ex: Similar to ALPS (Application Level Profile Semantics).
- Ref: [Alps](alps.io) 
2. Create a registry where publishers publish their APIs and clients registers with specific publishers based on the profile information or description of the publisher API.
3. Create Mapping files to map the publisher APIs with the profile semantics.

![alt text](https://github.com/SuperSDK/Documentation/blob/main/Mapping_PDL.png?raw=true "Mapping Diagram")

## PDL (Profile Definition Language)
What if we have shared vocabulary between clients and servers without need to modify the storage, Logical and business model.
Profile Description Language defines the domain specific shared vocabulary and affordances.
similar ideas in the past  XMDP, Microformat Vocabularies and DCAP. 
ALPS is one of the prominent language that can be used to address the above issue using shared affordances and semantics.

## API Interface registry 

![alt text](https://github.com/SuperSDK/Documentation/blob/main/API_registry.png?raw=true "Registry Diagram")

1. Every domain will have a Profile description using PDL 
2. APIs from the provider are registered in the registry under particular profile (Weather, GeoCoding, Search etc).
3. Clients subscribes to multiple profiles. 
4. Incase if a particular service is down, SuperSDK searches in the registry for another similar service and uses it to fulfill the request.


## Other key profiles from various domains that needs definition.

- GeoCoding
- Communication: SMS, Email
- Finance: Payment Gateways 
- Search
- Logistics
- Translation
- Advertising
- CMS
