

#REST

- Representational State Transfer
- API is organized around resourcess
- Resource representation is sent and fetched
- Mimick real world scenarios similar to object oriented programming
- REST APIs are driven by hypermedia links that are contained in the representation.

# REST Maturity Model 

In 2008, Leonard Richardson proposed the following maturity model for web APIs:

    Level 0: Define one URI, and all operations are POST requests to this URI.
    Level 1: Create separate URIs for individual resources.
    Level 2: Use HTTP methods to define operations on resources.
    Level 3: Use hypermedia (HATEOAS, described below).

Level 3 corresponds to a truly RESTful API according to Fielding's definition. In practice, many published web APIs fall somewhere around level 2.

# Organize the API design around resources

- Focus on the business entities that the web API exposes.
- resource URIs should be based on nouns (the resource) and not verbs (the operations on the resource).
- Do not expose internal implentation outside i.e. A resource doesn't have to be based on a single physical data item. 
  For example, an order resource might be implemented internally as several tables in a relational database, but presented to the client as a single entity.
- Sending an HTTP GET request to the collection URI retrieves a list of items in the collection. Each item in the collection also has its own unique URI. An HTTP GET request to the item's URI returns the details of that item.
- Adopt a consistent naming convention in URIs. In general, it helps to use plural nouns for URIs that reference collections.
- It can be mindboggling to implement relationships i.e customer orders relationship can be implemented as /customers/5/orders or /orders/5/customers, For such scenarios -
-   - Allow HAteOAS to enable navigation
    - Stick to physical world relationship (i.e a customer does the orders so implement it in /customers/5/orders way)
- Avoid requiring resource URIs more complex than collection/item/collection.
- Avoid chatty API (large number of small resources, causing multile requests)
    - Denormalize the data
- extraneous-fetching: Avoid fetching the data which client does not need
- Avoid introducing dependencies between the web API and the underlying data sources. For example, if your data is stored in a relational database, the web API doesn't need to expose each table as a collection of resources.
-  it might not be possible to map every operation implemented by a web API to a specific resource
-  

# Define API operations in terms of HTTP methods


- GET retrieves a representation of the resource at the specified URI. The body of the response message contains the details of the requested resource.
- POST creates a new resource at the specified URI. The body of the request message provides the details of the new resource. Note that POST can also be used to trigger operations that don't actually create resources.
- PUT either creates or replaces the resource at the specified URI. The body of the request message specifies the resource to be created or updated.
- PATCH performs a partial update of a resource. The request body specifies the set of changes to apply to the resource.
- DELETE removes the resource at the specified URI.



#### References

- https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design
- https://learn.microsoft.com/en-us/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources
- https://learn.microsoft.com/en-us/azure/architecture/antipatterns/chatty-io/
- https://learn.microsoft.com/en-us/azure/architecture/antipatterns/extraneous-fetching/
- 
