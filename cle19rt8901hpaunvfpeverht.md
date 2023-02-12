# What is REST?

REST (Representational State Transfer) is a software architectural style that defines a set of constraints and properties for creating web services. RESTful APIs are APIs that follow this architectural style and use HTTP methods (such as GET, POST, PUT, DELETE, etc.) to manipulate resources identified by URIs (Uniform Resource Identifiers).

The key characteristics of REST APIs include:

1. Client-server architecture: REST APIs separate the client and server components of an application, allowing each to evolve independently.
    
2. Statelessness: REST APIs do not maintain client-specific information on the server between requests.
    
3. Cacheability: REST APIs allow clients to cache responses, reducing the amount of data transferred and improving performance.
    
4. Layered system: REST APIs can be composed of multiple layers of components, such as load balancers, proxies, and servers, allowing for greater scalability and flexibility.
    
5. Use of HTTP methods: REST APIs use standard HTTP methods (such as GET, POST, PUT, and DELETE) to perform operations on resources.
    

REST APIs are used in a wide variety of applications and services, including social media, e-commerce, and weather data, and are typically preferred for their simplicity, scalability, and flexibility.

### Understanding REST vs HTTP

REST (Representational State Transfer) is a software architectural style for building web services, while HTTP (Hypertext Transfer Protocol) is a protocol for transmitting data over the internet. An API that conforms to the REST constraints is called a REST API, while an API that uses HTTP as its underlying protocol is referred to as an HTTP API.

The main difference between REST and HTTP APIs lies in the design principles and constraints, such as statelessness, caching, and the use of HTTP methods, that guide the development of REST APIs. REST APIs are typically more scalable and flexible, while HTTP APIs are simpler and often used for server-to-server communication.

In summary, REST APIs are built on top of HTTP and are designed to take advantage of its features, while HTTP APIs are simply APIs that use HTTP as the transport protocol

### Example of REST pattern

Let's consider a REST API for a simple online library management system. The API allows users to perform operations such as searching for books, checking out books, and returning books.

Here's how some of the API's resources and methods might be defined:

1. Book resource: Represented by the URI `/books/{id}`, where `{id}` is the unique identifier of a book.
    
2. Search for books: The API supports searching for books by sending a GET request to the URI `/books?q={query}`, where `{query}` is the search term. The API returns a list of books matching the search criteria.
    
3. Check out a book: To check out a book, a user sends a PUT request to the URI `/books/{id}/checkout`, where `{id}` is the identifier of the book. The API updates the book's availability status and returns a confirmation message.
    
4. Return a book: To return a book, a user sends a PUT request to the URI `/books/{id}/return`, where `{id}` is the identifier of the book. The API updates the book's availability status and returns a confirmation message.
    

These are just a few examples of how a REST API might be used in a library management system. By using standard HTTP methods and following the principles of REST, the API provides a flexible and scalable way for clients (such as mobile apps or web-based library management tools) to interact with the library's data.

### Where is REST used?

REST (Representational State Transfer) is a widely used architectural style for building web services, and its applications are many and varied. Some of the most common uses of REST APIs include:

1. **Social media:** Many social media platforms, such as Twitter, Facebook, and Instagram, provide REST APIs that allow developers to access and manipulate data, such as posts, comments, and user profiles.
    
2. **E-commerce:** Online stores and marketplaces use REST APIs to expose their products and services, allowing developers to build custom integrations, such as mobile shopping apps, price comparison tools, and order management systems.
    
3. **Weather data:** National weather services, such as the National Oceanic and Atmospheric Administration (NOAA) in the United States, provide REST APIs that allow developers to access current weather conditions and forecasts for locations around the world.
    
4. **Financial services:** Banks, payment providers, and other financial institutions use REST APIs to provide access to financial data and services, such as account information, transactions, and payment processing.
    
5. **Geolocation services:** Companies like Google and OpenStreetMap provide REST APIs for geolocation services, such as mapping, directions, and search-based location services.
    
6. **Healthcare:** Healthcare providers and medical research institutions use REST APIs to securely access and manage patient data, such as medical records, test results, and treatment plans.
    
7. **Internet of Things (IoT):** REST APIs are often used in IoT applications to connect devices, such as smart home devices and industrial sensors, to the internet, allowing them to exchange data and perform remote operations.
    

These are just a few examples of the many applications of REST APIs. The ease of integration, scalability, and flexibility offered by RESTful web services makes them an ideal choice for a wide range of industries and use cases.

### Resources

%[https://restfulapi.net/] 

%[https://www.redhat.com/en/topics/api/what-is-a-rest-api]