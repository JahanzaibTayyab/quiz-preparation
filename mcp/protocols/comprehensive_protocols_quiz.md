# 🌐 Comprehensive Protocols Quiz - HTTP, REST & JSON-RPC

Welcome to the Comprehensive Protocols Quiz! This quiz combines questions from HTTP theory, REST architectural principles, and JSON-RPC protocol to test your understanding of how these fundamental web technologies work together and when to use each one.

**Instructions:**

- Each question has 4 multiple choice options
- Only one answer is correct
- Read the explanation after answering to understand the concept better
- This quiz covers HTTP, REST, and JSON-RPC concepts and their practical applications

---

## Question 1: Protocol Selection for Real-Time Trading

```json
{
  "question": "You're building a real-time trading system that needs to handle 100,000+ orders per second with sub-millisecond latency. Which protocol combination would you choose?",
  "options": [
    "REST API over HTTP/2 for all operations",
    "JSON-RPC over WebSockets for control, binary protocol for market data",
    "HTTP/1.1 with REST for all operations",
    "JSON-RPC over HTTP for all operations"
  ],
  "correctAnswer": "JSON-RPC over WebSockets for control, binary protocol for market data",
  "explanation": "For high-frequency trading, JSON-RPC over WebSockets provides low-latency control operations, while binary protocols handle market data efficiently. This hybrid approach gives you the flexibility of JSON-RPC with the performance needed for real-time data."
}
```

## Question 2: HTTP/2 vs HTTP/1.1 Performance

```json
{
  "question": "Your REST API is experiencing performance issues with multiple concurrent requests. You're considering upgrading from HTTP/1.1 to HTTP/2. What's the main performance benefit you'll get?",
  "options": [
    "Faster JSON parsing",
    "Multiplexing multiple requests over a single connection",
    "Better compression",
    "Reduced server load"
  ],
  "correctAnswer": "Multiplexing multiple requests over a single connection",
  "explanation": "HTTP/2's main performance benefit is multiplexing, which allows multiple requests and responses to be sent concurrently over a single TCP connection. This eliminates the head-of-line blocking problem in HTTP/1.1 and significantly improves performance for multiple concurrent requests."
}
```

## Question 3: REST vs JSON-RPC for Mobile Apps

```json
{
  "question": "You're designing an API for a mobile app that needs to work offline and sync when connectivity is restored. Which protocol would be more suitable?",
  "options": [
    "REST API with proper caching headers",
    "JSON-RPC with batch operations and offline queue",
    "HTTP/2 with server push",
    "WebSockets with persistent connection"
  ],
  "correctAnswer": "JSON-RPC with batch operations and offline queue",
  "explanation": "JSON-RPC is more suitable for mobile apps with offline requirements because it supports batch operations, can queue requests when offline, and provides better control over request/response handling. REST is stateless and doesn't handle offline scenarios as well."
}
```

## Question 4: HTTP Status Codes in REST Context

```json
{
  "question": "In a REST API, what HTTP status code should be returned when a client tries to create a resource that already exists?",
  "options": ["200 OK", "201 Created", "409 Conflict", "400 Bad Request"],
  "correctAnswer": "409 Conflict",
  "explanation": "HTTP status code 409 Conflict is the appropriate response when a client tries to create a resource that already exists. This indicates that the request conflicts with the current state of the server and the resource cannot be created."
}
```

## Question 5: JSON-RPC Error Handling vs REST

```json
{
  "question": "How does error handling differ between JSON-RPC and REST APIs?",
  "options": [
    "JSON-RPC uses HTTP status codes, REST uses error objects",
    "REST uses HTTP status codes, JSON-RPC uses error objects in response body",
    "Both use HTTP status codes only",
    "Both use error objects in response body only"
  ],
  "correctAnswer": "REST uses HTTP status codes, JSON-RPC uses error objects in response body",
  "explanation": "REST APIs use HTTP status codes to indicate success/failure, while JSON-RPC uses error objects in the response body with specific error codes, messages, and optional data. This gives JSON-RPC more detailed error information but requires parsing the response body."
}
```

## Question 6: HTTP Headers for CORS

```json
{
  "question": "What HTTP header is used to specify which origins are allowed to access a REST API?",
  "options": [
    "Access-Control-Allow-Origin",
    "Access-Control-Allow-Methods",
    "Access-Control-Allow-Headers",
    "Access-Control-Max-Age"
  ],
  "correctAnswer": "Access-Control-Allow-Origin",
  "explanation": "The Access-Control-Allow-Origin header specifies which origins are allowed to access the resource. It can be set to a specific origin, '*' for all origins, or omitted to deny access. This is the primary CORS header for controlling cross-origin access."
}
```

## Question 7: Protocol Selection for Microservices

```json
{
  "question": "You're designing a microservices architecture with 20+ services. Which protocol would be most suitable for inter-service communication?",
  "options": [
    "REST APIs over HTTP/2",
    "JSON-RPC over HTTP",
    "JSON-RPC over WebSockets",
    "It depends on the specific service requirements"
  ],
  "correctAnswer": "It depends on the specific service requirements",
  "explanation": "The choice depends on service requirements. REST is good for resource-oriented services, JSON-RPC for procedure-oriented services, and WebSockets for real-time communication. A hybrid approach often works best in microservices architectures."
}
```

## Question 8: HTTP/3 and QUIC Benefits

```json
{
  "question": "What is the main advantage of HTTP/3 over HTTP/2 for mobile applications?",
  "options": [
    "Better compression",
    "Improved multiplexing",
    "Better performance over unreliable networks",
    "Reduced server load"
  ],
  "correctAnswer": "Better performance over unreliable networks",
  "explanation": "HTTP/3's main advantage is better performance over unreliable networks (like mobile networks) because it uses QUIC (UDP-based) instead of TCP. This reduces connection establishment time and handles packet loss more efficiently."
}
```

## Question 9: REST Resource Design

```json
{
  "question": "What is the correct REST URI design for managing user orders?",
  "options": [
    "/getUserOrders, /createOrder, /updateOrder, /deleteOrder",
    "/users/{id}/orders, /users/{id}/orders/{orderId}",
    "/api/orders?user={id}",
    "/orders/user/{id}"
  ],
  "correctAnswer": "/users/{id}/orders, /users/{id}/orders/{orderId}",
  "explanation": "The correct REST URI design uses hierarchical resource relationships. '/users/{id}/orders' represents the collection of orders for a specific user, and '/users/{id}/orders/{orderId}' represents a specific order. This follows REST principles of resource hierarchy."
}
```

## Question 10: JSON-RPC Batch Operations

```json
{
  "question": "What is the advantage of JSON-RPC batch operations over multiple individual REST requests?",
  "options": [
    "Better compression",
    "Reduced network overhead and atomic operations",
    "Faster JSON parsing",
    "Better caching"
  ],
  "correctAnswer": "Reduced network overhead and atomic operations",
  "explanation": "JSON-RPC batch operations reduce network overhead by sending multiple requests in a single HTTP request. They also provide atomic operations where all requests succeed or fail together, which is not possible with individual REST requests."
}
```

## Question 11: HTTP Caching Headers

```json
{
  "question": "What HTTP header is used to specify how long a response can be cached?",
  "options": ["Cache-Control", "Expires", "Last-Modified", "ETag"],
  "correctAnswer": "Cache-Control",
  "explanation": "The Cache-Control header is used to specify caching directives including how long a response can be cached. It provides more granular control than the Expires header and is the preferred method for controlling caching behavior."
}
```

## Question 12: REST vs JSON-RPC for CRUD Operations

```json
{
  "question": "For standard CRUD operations on resources, which protocol is more intuitive and follows HTTP semantics better?",
  "options": [
    "JSON-RPC with custom methods",
    "REST with standard HTTP methods",
    "Both are equally intuitive",
    "It depends on the data structure"
  ],
  "correctAnswer": "REST with standard HTTP methods",
  "explanation": "REST is more intuitive for CRUD operations because it maps naturally to HTTP methods: GET (read), POST (create), PUT (update), DELETE (delete). This follows HTTP semantics and is more self-documenting than JSON-RPC method names."
}
```

## Question 13: HTTP/2 Server Push

```json
{
  "question": "What is the purpose of HTTP/2 server push?",
  "options": [
    "To push data to clients without requests",
    "To send related resources before the client requests them",
    "To improve compression",
    "To reduce server load"
  ],
  "correctAnswer": "To send related resources before the client requests them",
  "explanation": "HTTP/2 server push allows the server to send related resources (like CSS, JS, images) before the client requests them. This improves performance by reducing the number of round trips needed to load a complete page."
}
```

## Question 14: JSON-RPC Notifications

```json
{
  "question": "What is a JSON-RPC notification and how does it differ from a regular request?",
  "options": [
    "A notification is a server-to-client message",
    "A notification is a request without an 'id' field",
    "A notification is an error response",
    "A notification is a batch request"
  ],
  "correctAnswer": "A notification is a request without an 'id' field",
  "explanation": "A JSON-RPC notification is a request object that does not include the 'id' field. When a client sends a notification, it's not interested in a response from the server, and the server MUST NOT reply to it. This enables one-way communication."
}
```

## Question 15: REST HATEOAS Implementation

```json
{
  "question": "What is the purpose of HATEOAS in REST APIs?",
  "options": [
    "To improve performance",
    "To provide API documentation",
    "To make APIs self-documenting and discoverable",
    "To enable caching"
  ],
  "correctAnswer": "To make APIs self-documenting and discoverable",
  "explanation": "HATEOAS (Hypermedia as the Engine of Application State) makes REST APIs self-documenting and discoverable by including links in responses that tell clients what actions are available and how to navigate the API."
}
```

## Question 16: HTTP/3 Connection Establishment

```json
{
  "question": "How does HTTP/3 connection establishment differ from HTTP/2?",
  "options": [
    "HTTP/3 uses TCP, HTTP/2 uses UDP",
    "HTTP/3 uses UDP (QUIC), HTTP/2 uses TCP",
    "HTTP/3 is faster because it uses HTTP/1.1",
    "HTTP/3 doesn't require connection establishment"
  ],
  "correctAnswer": "HTTP/3 uses UDP (QUIC), HTTP/2 uses TCP",
  "explanation": "HTTP/3 uses QUIC (which runs over UDP) instead of TCP. This provides faster connection establishment, better handling of network changes, and improved performance over unreliable networks."
}
```

## Question 17: JSON-RPC vs REST for Complex Operations

```json
{
  "question": "For complex business operations that don't map well to CRUD, which protocol is more suitable?",
  "options": [
    "REST with custom endpoints",
    "JSON-RPC with descriptive method names",
    "Both are equally suitable",
    "HTTP/2 with server push"
  ],
  "correctAnswer": "JSON-RPC with descriptive method names",
  "explanation": "JSON-RPC is more suitable for complex business operations because it allows descriptive method names that clearly indicate the operation being performed, rather than trying to map everything to HTTP methods."
}
```

## Question 18: HTTP Security Headers

```json
{
  "question": "What HTTP header prevents clickjacking attacks?",
  "options": [
    "X-Frame-Options",
    "X-XSS-Protection",
    "X-Content-Type-Options",
    "Strict-Transport-Security"
  ],
  "correctAnswer": "X-Frame-Options",
  "explanation": "The X-Frame-Options header prevents clickjacking attacks by controlling whether a browser should be allowed to render a page in a frame, iframe, embed, or object. Values include DENY, SAMEORIGIN, or ALLOW-FROM."
}
```

## Question 19: REST Resource Versioning

```json
{
  "question": "What is the most RESTful approach to API versioning?",
  "options": [
    "URL versioning (/api/v1/users)",
    "Header versioning (Accept: application/vnd.api+json;version=1)",
    "Content negotiation with custom media types",
    "Query parameter versioning (?version=1)"
  ],
  "correctAnswer": "Content negotiation with custom media types",
  "explanation": "Content negotiation with custom media types (e.g., 'application/vnd.company.users-v1+json') is the most RESTful approach because it follows REST principles, provides clear semantic meaning, and allows multiple versions to coexist."
}
```

## Question 20: JSON-RPC Error Codes

```json
{
  "question": "What is the range for custom server error codes in JSON-RPC?",
  "options": [
    "-32000 to -32099",
    "-32700 to -32799",
    "-32600 to -32699",
    "-32500 to -32599"
  ],
  "correctAnswer": "-32000 to -32099",
  "explanation": "Custom server error codes in JSON-RPC range from -32000 to -32099. These codes are reserved for implementation-defined server errors and can be used by servers to indicate specific error conditions."
}
```

## Question 21: HTTP/2 Flow Control

```json
{
  "question": "What is the purpose of flow control in HTTP/2?",
  "options": [
    "To control data compression",
    "To prevent overwhelming receivers with data",
    "To improve multiplexing",
    "To reduce server load"
  ],
  "correctAnswer": "To prevent overwhelming receivers with data",
  "explanation": "HTTP/2 flow control prevents overwhelming receivers with data by allowing them to control how much data they receive. This ensures that receivers can process data at their own pace and prevents memory issues."
}
```

## Question 22: REST Statelessness

```json
{
  "question": "What does 'stateless' mean in REST architecture?",
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

## Question 23: JSON-RPC Transport Independence

```json
{
  "question": "What does it mean that JSON-RPC is transport-agnostic?",
  "options": [
    "It only works over HTTP",
    "It can work over any transport protocol",
    "It doesn't require a transport layer",
    "It only works over WebSockets"
  ],
  "correctAnswer": "It can work over any transport protocol",
  "explanation": "JSON-RPC is transport-agnostic, meaning it can be used over HTTP, WebSockets, TCP, or any other message-passing environment. The protocol itself doesn't depend on any specific transport mechanism."
}
```

## Question 24: HTTP/3 Migration Strategy

```json
{
  "question": "What is the recommended strategy for migrating from HTTP/2 to HTTP/3?",
  "options": [
    "Immediate migration for all traffic",
    "Gradual migration with fallback to HTTP/2",
    "Use HTTP/3 only for new features",
    "Wait for full browser support"
  ],
  "correctAnswer": "Gradual migration with fallback to HTTP/2",
  "explanation": "Gradual migration with fallback to HTTP/2 is recommended because it allows for testing and validation while maintaining compatibility. HTTP/3 clients can fall back to HTTP/2 if needed, ensuring a smooth transition."
}
```

## Question 25: REST vs JSON-RPC Performance

```json
{
  "question": "Which protocol typically has lower overhead for simple operations?",
  "options": [
    "REST over HTTP/1.1",
    "JSON-RPC over HTTP",
    "REST over HTTP/2",
    "JSON-RPC over WebSockets"
  ],
  "correctAnswer": "REST over HTTP/2",
  "explanation": "REST over HTTP/2 typically has lower overhead for simple operations because HTTP/2's multiplexing and header compression reduce the per-request overhead, while REST's simple request/response model is more efficient than JSON-RPC's structured format."
}
```

## Question 26: HTTP/2 Priority and Dependencies

```json
{
  "question": "What is the purpose of HTTP/2 priority and dependencies?",
  "options": [
    "To control data compression",
    "To specify the order of resource loading",
    "To improve multiplexing",
    "To reduce server load"
  ],
  "correctAnswer": "To specify the order of resource loading",
  "explanation": "HTTP/2 priority and dependencies allow clients to specify the order in which resources should be loaded. This enables intelligent resource loading where critical resources (like CSS) are loaded before less important ones (like images)."
}
```

## Question 27: JSON-RPC Method Naming

```json
{
  "question": "What method names are reserved in JSON-RPC?",
  "options": [
    "Methods starting with 'rpc.'",
    "Methods starting with 'json.'",
    "Methods starting with 'system.'",
    "Methods starting with 'internal.'"
  ],
  "correctAnswer": "Methods starting with 'rpc.'",
  "explanation": "Method names that start with 'rpc.' are reserved for system extensions in JSON-RPC and should not be used for application-specific methods. This prevents conflicts with future protocol extensions."
}
```

## Question 28: REST Resource Identification

```json
{
  "question": "What is the primary way to identify resources in REST?",
  "options": ["HTTP headers", "URIs", "Query parameters", "Request body"],
  "correctAnswer": "URIs",
  "explanation": "URIs (Uniform Resource Identifiers) are the primary way to identify resources in REST. Each resource has a unique URI that clients use to access, modify, or delete the resource."
}
```

## Question 29: HTTP/3 0-RTT Connection

```json
{
  "question": "What is the main benefit of HTTP/3 0-RTT connections?",
  "options": [
    "Better compression",
    "Faster initial page loads for returning visitors",
    "Improved multiplexing",
    "Reduced server load"
  ],
  "correctAnswer": "Faster initial page loads for returning visitors",
  "explanation": "HTTP/3 0-RTT connections allow returning visitors to send requests immediately without waiting for connection establishment. This significantly reduces initial page load times for users who have previously visited the site."
}
```

## Question 30: JSON-RPC vs REST for Real-Time Updates

```json
{
  "question": "For real-time updates and notifications, which protocol is more suitable?",
  "options": [
    "REST with polling",
    "JSON-RPC over WebSockets",
    "REST with Server-Sent Events",
    "JSON-RPC over HTTP with long polling"
  ],
  "correctAnswer": "JSON-RPC over WebSockets",
  "explanation": "JSON-RPC over WebSockets is more suitable for real-time updates because it provides persistent bidirectional communication, low latency, and efficient message passing without the overhead of HTTP headers for each message."
}
```

## Question 31: HTTP/2 HPACK Compression

```json
{
  "question": "What does HPACK compression in HTTP/2 do?",
  "options": [
    "Compresses response bodies",
    "Compresses HTTP headers",
    "Compresses JSON payloads",
    "Compresses images"
  ],
  "correctAnswer": "Compresses HTTP headers",
  "explanation": "HPACK is HTTP/2's header compression format. It compresses HTTP headers to reduce overhead, especially important since HTTP/2 multiplexes multiple requests over a single connection where header overhead would otherwise accumulate."
}
```

## Question 32: REST Idempotence

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

## Question 33: JSON-RPC Batch Request Processing

```json
{
  "question": "How does a server process JSON-RPC batch requests?",
  "options": [
    "Sequentially in order",
    "In parallel, responses in same order",
    "In any order, responses can be in any order",
    "Only the first request is processed"
  ],
  "correctAnswer": "In any order, responses can be in any order",
  "explanation": "The server can process batch requests in any order, and the responses can also be in any order. The client should use the 'id' of each request to match it with its corresponding response."
}
```

## Question 34: HTTP/2 Server Push vs HTTP/1.1

```json
{
  "question": "What advantage does HTTP/2 server push have over HTTP/1.1 for loading web pages?",
  "options": [
    "Better compression",
    "Reduced number of round trips",
    "Faster connection establishment",
    "Improved multiplexing"
  ],
  "correctAnswer": "Reduced number of round trips",
  "explanation": "HTTP/2 server push reduces the number of round trips by allowing the server to send related resources (like CSS, JS, images) before the client requests them, eliminating the need for separate requests."
}
```

## Question 35: REST vs JSON-RPC for Mobile APIs

```json
{
  "question": "For a mobile API that needs to minimize bandwidth usage, which protocol is more suitable?",
  "options": [
    "REST with proper caching",
    "JSON-RPC with batch operations",
    "REST with compression",
    "JSON-RPC with compression"
  ],
  "correctAnswer": "JSON-RPC with batch operations",
  "explanation": "JSON-RPC with batch operations is more suitable for mobile APIs because it allows multiple operations to be sent in a single request, reducing network overhead and improving performance on bandwidth-constrained mobile networks."
}
```

## Question 36: HTTP/3 Connection Migration

```json
{
  "question": "What is the main advantage of HTTP/3 connection migration?",
  "options": [
    "Better compression",
    "Seamless connection handling during network changes",
    "Improved multiplexing",
    "Reduced server load"
  ],
  "correctAnswer": "Seamless connection handling during network changes",
  "explanation": "HTTP/3 connection migration allows connections to seamlessly handle network changes (like switching from WiFi to mobile data) without requiring reconnection, which improves performance and user experience."
}
```

## Question 37: REST Cacheability

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

## Question 38: JSON-RPC Error Object Structure

```json
{
  "question": "What fields are required in a JSON-RPC error object?",
  "options": [
    "code and message",
    "code, message, and data",
    "code only",
    "message only"
  ],
  "correctAnswer": "code and message",
  "explanation": "A JSON-RPC error object requires 'code' (numeric error code) and 'message' (human-readable error description). The 'data' field is optional and provides additional error information."
}
```

## Question 39: HTTP/2 vs HTTP/1.1 Headers

```json
{
  "question": "How do HTTP/2 headers differ from HTTP/1.1 headers?",
  "options": [
    "HTTP/2 headers are always compressed",
    "HTTP/2 headers use binary format",
    "HTTP/2 headers are always encrypted",
    "HTTP/2 headers are always larger"
  ],
  "correctAnswer": "HTTP/2 headers are always compressed",
  "explanation": "HTTP/2 headers are always compressed using HPACK, which reduces overhead especially important since HTTP/2 multiplexes multiple requests over a single connection."
}
```

## Question 40: REST Uniform Interface

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

## Question 41: JSON-RPC vs REST for Complex Queries

```json
{
  "question": "For complex database queries with multiple filters and aggregations, which protocol is more suitable?",
  "options": [
    "REST with query parameters",
    "JSON-RPC with structured parameters",
    "REST with POST body",
    "JSON-RPC with batch operations"
  ],
  "correctAnswer": "JSON-RPC with structured parameters",
  "explanation": "JSON-RPC is more suitable for complex queries because it allows structured parameters that can represent complex query objects, filters, and aggregations more naturally than REST query parameters."
}
```

## Question 42: HTTP/2 Priority Streams

```json
{
  "question": "What is the purpose of HTTP/2 priority streams?",
  "options": [
    "To control data compression",
    "To specify resource loading order",
    "To improve multiplexing",
    "To reduce server load"
  ],
  "correctAnswer": "To specify resource loading order",
  "explanation": "HTTP/2 priority streams allow clients to specify the order in which resources should be loaded, enabling intelligent resource loading where critical resources are prioritized over less important ones."
}
```

## Question 43: REST vs JSON-RPC for File Uploads

```json
{
  "question": "For large file uploads with progress tracking, which protocol is more suitable?",
  "options": [
    "REST with multipart/form-data",
    "JSON-RPC with chunked upload",
    "REST with streaming",
    "JSON-RPC with base64 encoding"
  ],
  "correctAnswer": "JSON-RPC with chunked upload",
  "explanation": "JSON-RPC with chunked upload is more suitable for large files because it provides better control over upload progress, resumable uploads, and error handling compared to REST multipart uploads."
}
```

## Question 44: HTTP/3 0-RTT Security

```json
{
  "question": "What security consideration is important for HTTP/3 0-RTT connections?",
  "options": [
    "Replay attacks",
    "Man-in-the-middle attacks",
    "DDoS attacks",
    "SQL injection"
  ],
  "correctAnswer": "Replay attacks",
  "explanation": "HTTP/3 0-RTT connections are vulnerable to replay attacks because requests sent in 0-RTT can be captured and replayed. This requires careful consideration of which operations are safe to perform in 0-RTT mode."
}
```

## Question 45: REST vs JSON-RPC for API Documentation

```json
{
  "question": "Which protocol is easier to document and generate client SDKs for?",
  "options": [
    "REST with OpenAPI/Swagger",
    "JSON-RPC with introspection",
    "Both are equally easy",
    "It depends on the API complexity"
  ],
  "correctAnswer": "REST with OpenAPI/Swagger",
  "explanation": "REST with OpenAPI/Swagger is easier to document and generate SDKs for because it has mature tooling, standardized documentation formats, and clear resource-based patterns that are easier to understand and implement."
}
```

## Question 46: HTTP/2 vs HTTP/1.1 Connection Limits

```json
{
  "question": "How do HTTP/2 connection limits differ from HTTP/1.1?",
  "options": [
    "HTTP/2 has no connection limits",
    "HTTP/2 uses a single connection for multiple requests",
    "HTTP/1.1 has no connection limits",
    "HTTP/2 has stricter connection limits"
  ],
  "correctAnswer": "HTTP/2 uses a single connection for multiple requests",
  "explanation": "HTTP/2 uses a single connection for multiple requests through multiplexing, eliminating the need for multiple connections that HTTP/1.1 requires due to its request/response model."
}
```

## Question 47: JSON-RPC Method Introspection

```json
{
  "question": "What is the purpose of JSON-RPC method introspection?",
  "options": [
    "To improve performance",
    "To provide API documentation and discovery",
    "To validate method calls",
    "To enable method chaining"
  ],
  "correctAnswer": "To provide API documentation and discovery",
  "explanation": "JSON-RPC method introspection provides API documentation and discovery capabilities by allowing clients to query available methods, their parameters, return types, and documentation, making the API self-documenting."
}
```

## Question 48: REST vs JSON-RPC for Event-Driven Systems

```json
{
  "question": "For event-driven systems with real-time notifications, which protocol is more suitable?",
  "options": [
    "REST with polling",
    "JSON-RPC over WebSockets",
    "REST with Server-Sent Events",
    "JSON-RPC over HTTP with long polling"
  ],
  "correctAnswer": "JSON-RPC over WebSockets",
  "explanation": "JSON-RPC over WebSockets is more suitable for event-driven systems because it provides persistent bidirectional communication, efficient message passing, and better support for real-time notifications."
}
```

## Question 49: HTTP/3 vs HTTP/2 Performance

```json
{
  "question": "In what scenarios does HTTP/3 typically outperform HTTP/2?",
  "options": [
    "High-speed networks",
    "Unreliable networks with packet loss",
    "Local networks",
    "All scenarios"
  ],
  "correctAnswer": "Unreliable networks with packet loss",
  "explanation": "HTTP/3 typically outperforms HTTP/2 on unreliable networks with packet loss because QUIC (UDP-based) handles packet loss more efficiently than TCP, reducing connection establishment time and improving overall performance."
}
```

## Question 50: Protocol Selection for IoT Devices

```json
{
  "question": "For IoT devices with limited resources and unreliable connectivity, which protocol combination is most suitable?",
  "options": [
    "REST over HTTP/2",
    "JSON-RPC over WebSockets",
    "JSON-RPC over HTTP with lightweight authentication",
    "REST over HTTP/1.1 with caching"
  ],
  "correctAnswer": "JSON-RPC over HTTP with lightweight authentication",
  "explanation": "JSON-RPC over HTTP with lightweight authentication is most suitable for IoT devices because it provides efficient communication, supports batch operations, works well with unreliable networks, and has lower overhead than WebSockets."
}
```

---

## 📊 **Quiz Summary**

**Total Questions:** 50  
**Difficulty Level:** Comprehensive (All Levels)  
**Topics Covered:**

- HTTP theory and protocol evolution (HTTP/1.1, HTTP/2, HTTP/3)
- REST architectural principles and best practices
- JSON-RPC protocol and implementation patterns
- Protocol comparison and selection criteria
- Real-world implementation scenarios
- Performance optimization and trade-offs
- Security considerations across protocols
- Practical application in modern systems

**Scoring Guide:**

- 40-50 correct: Expert-level understanding of web protocols
- 30-39 correct: Advanced understanding with some areas for improvement
- 20-29 correct: Good understanding, review recommended
- Below 20: Fundamental review needed

**Key Concepts Tested:**

- **Protocol Understanding**: Deep knowledge of HTTP, REST, and JSON-RPC
- **Protocol Selection**: Choosing the right protocol for specific use cases
- **Performance Optimization**: Understanding trade-offs and optimization strategies
- **Real-world Application**: Practical implementation in complex systems
- **Security Considerations**: Security implications across different protocols
- **Modern Web Technologies**: Understanding of HTTP/2, HTTP/3, and WebSockets
- **System Design**: Architectural decisions involving multiple protocols

**Advanced Topics Covered:**

- **Protocol Evolution**: HTTP/1.1 → HTTP/2 → HTTP/3 progression
- **Performance Characteristics**: Latency, throughput, and efficiency comparisons
- **Use Case Optimization**: Matching protocols to specific requirements
- **Hybrid Architectures**: Combining multiple protocols in single systems
- **Modern Web Standards**: QUIC, WebSockets, and emerging technologies
- **Production Considerations**: Scalability, reliability, and maintainability

**Next Steps:**
After completing this quiz, consider exploring:

- Advanced protocol design and optimization
- Protocol-specific security implementations
- Performance benchmarking and optimization
- Modern web standards and emerging protocols
- Protocol integration in microservices architectures
- Advanced monitoring and debugging techniques
- Protocol-specific testing strategies

---

_This comprehensive quiz tests understanding across HTTP, REST, and JSON-RPC protocols, their interrelationships, and practical application in modern web systems. It's designed for engineers who need to understand how these technologies work together in real-world scenarios._
