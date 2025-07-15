# 🌐 REST Basics - Beginner Quiz

Welcome to the REST Basics Quiz! This quiz will test your understanding of fundamental REST concepts including architectural principles, HTTP methods, resources, representations, and basic API design.

**Instructions:**

- Each question has 4 multiple choice options
- Only one answer is correct
- Read the explanation after answering to understand the concept better
- This quiz covers beginner-level REST concepts

---

## Question 1

```json
{
  "question": "What does REST stand for?",
  "options": [
    "Remote State Transfer",
    "Representational State Transfer",
    "Resource State Transfer",
    "Request State Transfer"
  ],
  "correctAnswer": "Representational State Transfer",
  "explanation": "REST stands for Representational State Transfer. It's an architectural style for designing networked applications, particularly web services. The name reflects that clients interact with representations of resources rather than the resources themselves."
}
```

## Question 2

```json
{
  "question": "Is REST a protocol like HTTP?",
  "options": [
    "Yes, REST is a protocol",
    "No, REST is an architectural style",
    "Yes, REST is a programming language",
    "No, REST is a software tool"
  ],
  "correctAnswer": "No, REST is an architectural style",
  "explanation": "REST is not a protocol, programming language, or software tool. It's an architectural style - a set of design principles and constraints for building web services. REST typically uses HTTP as its underlying protocol."
}
```

## Question 3

```json
{
  "question": "What is a 'resource' in REST?",
  "options": [
    "A computer server",
    "Any information or entity that can be named and addressed",
    "A programming language",
    "A network connection"
  ],
  "correctAnswer": "Any information or entity that can be named and addressed",
  "explanation": "In REST, a resource is any information or entity that can be named and addressed. Examples include users, products, orders, documents, images, or any piece of data that can be identified by a URI."
}
```

## Question 4

```json
{
  "question": "What is a 'representation' in REST?",
  "options": [
    "A server computer",
    "A copy or snapshot of a resource's state",
    "A programming language",
    "A network protocol"
  ],
  "correctAnswer": "A copy or snapshot of a resource's state",
  "explanation": "A representation is a copy or snapshot of a resource's state at a particular time. When a client requests a resource, the server sends back a representation (like JSON or XML) of that resource's current state."
}
```

## Question 5

```json
{
  "question": "Which HTTP method is used to retrieve a resource in REST?",
  "options": ["POST", "GET", "PUT", "DELETE"],
  "correctAnswer": "GET",
  "explanation": "The GET method is used to retrieve a representation of a resource. It's a safe, read-only operation that doesn't modify the resource. GET requests are typically used to fetch data from the server."
}
```

## Question 6

```json
{
  "question": "Which HTTP method is used to create a new resource in REST?",
  "options": ["GET", "POST", "PUT", "DELETE"],
  "correctAnswer": "POST",
  "explanation": "The POST method is used to create a new resource. When you send a POST request, you're asking the server to create a new resource based on the data you provide in the request body."
}
```

## Question 7

```json
{
  "question": "Which HTTP method is used to completely replace a resource in REST?",
  "options": ["GET", "POST", "PUT", "DELETE"],
  "correctAnswer": "PUT",
  "explanation": "The PUT method is used to completely replace an existing resource with a new representation. If the resource doesn't exist, PUT may create it. PUT replaces the entire resource, not just parts of it."
}
```

## Question 8

```json
{
  "question": "Which HTTP method is used to delete a resource in REST?",
  "options": ["GET", "POST", "PUT", "DELETE"],
  "correctAnswer": "DELETE",
  "explanation": "The DELETE method is used to remove a resource from the server. When you send a DELETE request, you're asking the server to delete the specified resource."
}
```

## Question 9

```json
{
  "question": "What does 'stateless' mean in REST?",
  "options": [
    "The server never stores any data",
    "Each request contains all information needed to process it",
    "The client never stores any data",
    "The server doesn't use HTTP"
  ],
  "correctAnswer": "Each request contains all information needed to process it",
  "explanation": "Stateless means that each request from a client to a server must contain all the information needed for the server to understand and process the request. The server doesn't store any client context between requests."
}
```

## Question 10

```json
{
  "question": "What is the purpose of a URI in REST?",
  "options": [
    "To identify the server",
    "To uniquely identify a resource",
    "To identify the client",
    "To identify the protocol"
  ],
  "correctAnswer": "To uniquely identify a resource",
  "explanation": "A URI (Uniform Resource Identifier) is used to uniquely identify a resource in REST. It's like an address that tells the client exactly where to find a specific resource on the server."
}
```

## Question 11

```json
{
  "question": "Which HTTP status code indicates a successful request in REST?",
  "options": ["200", "400", "404", "500"],
  "correctAnswer": "200",
  "explanation": "HTTP status code 200 means 'OK' - the request was successful. It's the most common success response in REST APIs, indicating that the server successfully processed the request and returned the requested data."
}
```

## Question 12

```json
{
  "question": "Which HTTP status code indicates that a resource was successfully created?",
  "options": ["200", "201", "204", "400"],
  "correctAnswer": "201",
  "explanation": "HTTP status code 201 means 'Created' - the request was successful and a new resource was created as a result. This is commonly returned after successful POST requests that create new resources."
}
```

## Question 13

```json
{
  "question": "Which HTTP status code indicates that a resource was not found?",
  "options": ["400", "401", "404", "500"],
  "correctAnswer": "404",
  "explanation": "HTTP status code 404 means 'Not Found' - the server couldn't find the requested resource. This is a common error when a URI doesn't exist or the resource has been moved or deleted."
}
```

## Question 14

```json
{
  "question": "What does 'idempotent' mean in REST?",
  "options": [
    "The request is always successful",
    "Making the same request multiple times has the same effect as making it once",
    "The request is always fast",
    "The request never fails"
  ],
  "correctAnswer": "Making the same request multiple times has the same effect as making it once",
  "explanation": "Idempotent means that making the same request multiple times has the same effect as making it once. For example, deleting a resource multiple times results in the same state (the resource is deleted)."
}
```

## Question 15

```json
{
  "question": "Which HTTP methods are typically idempotent?",
  "options": [
    "GET, POST, PUT, DELETE",
    "GET, PUT, DELETE",
    "POST, PUT, DELETE",
    "GET, POST, PUT"
  ],
  "correctAnswer": "GET, PUT, DELETE",
  "explanation": "GET, PUT, and DELETE are typically idempotent. GET reads data (no side effects), PUT replaces a resource (same result each time), and DELETE removes a resource (still deleted after multiple requests). POST is generally not idempotent."
}
```

## Question 16

```json
{
  "question": "What is the most common data format used in REST APIs?",
  "options": ["XML", "JSON", "HTML", "Plain text"],
  "correctAnswer": "JSON",
  "explanation": "JSON (JavaScript Object Notation) is the most common data format used in REST APIs. It's lightweight, easy to read and write, and is supported by virtually all programming languages and platforms."
}
```

## Question 17

```json
{
  "question": "What does HATEOAS stand for?",
  "options": [
    "Hypermedia As The Engine Of Application State",
    "HTTP As The Engine Of Application State",
    "Hypertext As The Engine Of Application State",
    "HTML As The Engine Of Application State"
  ],
  "correctAnswer": "Hypermedia As The Engine Of Application State",
  "explanation": "HATEOAS stands for Hypermedia As The Engine Of Application State. It's a REST constraint that means the server should guide the client by sending links in responses, so the client knows what actions are available."
}
```

## Question 18

```json
{
  "question": "What is the purpose of the 'Accept' header in a REST request?",
  "options": [
    "To accept the response",
    "To specify what format the client wants in the response",
    "To accept cookies",
    "To accept authentication"
  ],
  "correctAnswer": "To specify what format the client wants in the response",
  "explanation": "The Accept header tells the server what format the client wants in the response. For example, 'Accept: application/json' tells the server to return the response in JSON format."
}
```

## Question 19

```json
{
  "question": "What is the purpose of the 'Content-Type' header in a REST request?",
  "options": [
    "To specify the type of content being sent",
    "To specify the type of content being received",
    "To specify the server type",
    "To specify the client type"
  ],
  "correctAnswer": "To specify the type of content being sent",
  "explanation": "The Content-Type header tells the server what type of content is being sent in the request body. For example, 'Content-Type: application/json' indicates that the request body contains JSON data."
}
```

## Question 20

```json
{
  "question": "What is a good URI design for a REST API that manages users?",
  "options": [
    "/getAllUsers, /createUser, /updateUser, /deleteUser",
    "/users, /users/{id}, /users/create, /users/delete",
    "/users, /users/{id}",
    "/api/getUsers, /api/createUser, /api/updateUser"
  ],
  "correctAnswer": "/users, /users/{id}",
  "explanation": "Good REST URI design uses nouns for resources and HTTP methods for actions. '/users' for the collection and '/users/{id}' for individual users is a clean, RESTful design that follows best practices."
}
```

## Question 21

```json
{
  "question": "What does 'cacheable' mean in REST?",
  "options": [
    "Responses can be stored and reused",
    "Requests can be stored and reused",
    "Servers can be stored and reused",
    "Clients can be stored and reused"
  ],
  "correctAnswer": "Responses can be stored and reused",
  "explanation": "Cacheable means that responses from the server can be stored (cached) and reused for later, equivalent requests. This improves performance by reducing server load and network traffic."
}
```

## Question 22

```json
{
  "question": "Which HTTP method is used for partial updates to a resource?",
  "options": ["GET", "POST", "PUT", "PATCH"],
  "correctAnswer": "PATCH",
  "explanation": "The PATCH method is used for partial updates to a resource. Unlike PUT which replaces the entire resource, PATCH allows you to update only specific fields or parts of a resource."
}
```

## Question 23

```json
{
  "question": "What is the purpose of the 'Authorization' header in REST?",
  "options": [
    "To identify the client",
    "To provide authentication credentials",
    "To specify the content type",
    "To specify the server"
  ],
  "correctAnswer": "To provide authentication credentials",
  "explanation": "The Authorization header is used to provide authentication credentials to the server. It typically contains tokens, API keys, or other credentials that prove the client's identity and permissions."
}
```

## Question 24

```json
{
  "question": "What does 'uniform interface' mean in REST?",
  "options": [
    "All servers look the same",
    "All clients look the same",
    "All resources are accessed using the same methods",
    "All responses look the same"
  ],
  "correctAnswer": "All resources are accessed using the same methods",
  "explanation": "Uniform interface means that all resources are accessed using the same set of methods (GET, POST, PUT, DELETE, etc.). This simplifies the architecture and makes it easier to understand and use."
}
```

## Question 25

```json
{
  "question": "What is the purpose of query parameters in a REST URI?",
  "options": [
    "To identify the resource",
    "To provide additional information for filtering, sorting, or pagination",
    "To specify the HTTP method",
    "To specify the server"
  ],
  "correctAnswer": "To provide additional information for filtering, sorting, or pagination",
  "explanation": "Query parameters in a REST URI provide additional information for filtering, sorting, pagination, or other operations. For example, '/users?status=active&limit=10' filters users by status and limits results to 10."
}
```

## Question 26

```json
{
  "question": "What is the purpose of the 'Location' header in a REST response?",
  "options": [
    "To specify where the server is located",
    "To specify the URI of a newly created resource",
    "To specify where the client is located",
    "To specify the content location"
  ],
  "correctAnswer": "To specify the URI of a newly created resource",
  "explanation": "The Location header specifies the URI of a newly created resource. It's commonly used with 201 Created responses to tell the client where to find the resource that was just created."
}
```

## Question 27

```json
{
  "question": "What does 'layered system' mean in REST?",
  "options": [
    "The server has multiple layers",
    "The client has multiple layers",
    "Components can only interact with adjacent layers",
    "The network has multiple layers"
  ],
  "correctAnswer": "Components can only interact with adjacent layers",
  "explanation": "Layered system means that components in one layer can only interact with components in adjacent layers. This allows for load balancers, proxies, and other intermediaries without the client knowing about them."
}
```

## Question 28

```json
{
  "question": "What is the purpose of the 'ETag' header in REST?",
  "options": [
    "To identify the server",
    "To provide a unique identifier for resource versioning",
    "To identify the client",
    "To specify the content type"
  ],
  "correctAnswer": "To provide a unique identifier for resource versioning",
  "explanation": "The ETag header provides a unique identifier for a specific version of a resource. Clients can use it with 'If-None-Match' headers to check if their cached version is still valid."
}
```

## Question 29

```json
{
  "question": "What is the purpose of the 'If-Modified-Since' header in REST?",
  "options": [
    "To check if the server has been modified",
    "To conditionally request a resource only if it has changed",
    "To check if the client has been modified",
    "To specify when the request was created"
  ],
  "correctAnswer": "To conditionally request a resource only if it has changed",
  "explanation": "The If-Modified-Since header allows clients to make conditional requests. If the resource hasn't changed since the specified date, the server returns 304 Not Modified, saving bandwidth."
}
```

## Question 30

```json
{
  "question": "What is the main benefit of REST's stateless constraint?",
  "options": [
    "It makes requests faster",
    "It improves scalability and reliability",
    "It makes responses smaller",
    "It makes the protocol simpler"
  ],
  "correctAnswer": "It improves scalability and reliability",
  "explanation": "The stateless constraint improves scalability and reliability because any server can handle any request without needing to know about previous requests. This allows for better load balancing and easier recovery from failures."
}
```

---

## 📊 **Quiz Summary**

**Total Questions:** 30  
**Difficulty Level:** Beginner  
**Topics Covered:**

- REST fundamentals and architectural principles
- HTTP methods and their purposes
- Resources and representations
- REST constraints (stateless, cacheable, uniform interface, etc.)
- HTTP status codes in REST context
- Idempotence and HATEOAS concepts
- Basic URI design and best practices
- Common headers and their purposes

**Scoring Guide:**

- 25-30 correct: Excellent understanding of REST basics
- 20-24 correct: Good understanding with some areas for improvement
- 15-19 correct: Basic understanding, review recommended
- Below 15: Fundamental review needed

**Key REST Concepts Tested:**

- **Architecture**: Understanding REST as an architectural style
- **Resources**: Identifying and working with resources
- **HTTP Methods**: Proper use of GET, POST, PUT, DELETE, PATCH
- **Status Codes**: Understanding HTTP responses in REST context
- **Constraints**: Stateless, cacheable, uniform interface, layered system
- **Best Practices**: URI design, headers, data formats

**Next Steps:**
After completing this quiz, consider exploring:

- Advanced REST API design patterns
- Authentication and authorization in REST
- API versioning strategies
- Performance optimization techniques
- REST in microservices architecture
- OpenAPI/Swagger documentation

---

_This quiz is based on the REST theory content from the MCP learning repository. For more detailed explanations, refer to the original documentation._
