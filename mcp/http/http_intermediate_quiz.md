# 🌐 HTTP Intermediate - Advanced Quiz

Welcome to the HTTP Intermediate Quiz! This quiz will test your understanding of advanced HTTP concepts including protocol evolution, security mechanisms, performance optimization, advanced headers, and practical HTTP debugging.

**Instructions:**

- Each question has 4 multiple choice options
- Only one answer is correct
- Read the explanation after answering to understand the concept better
- This quiz covers intermediate to advanced HTTP concepts

---

## Question 1

```json
{
  "question": "What is the main advantage of HTTP/2 over HTTP/1.1?",
  "options": [
    "Better security with built-in encryption",
    "Multiplexing multiple requests over a single connection",
    "Smaller header sizes only",
    "Faster connection establishment"
  ],
  "correctAnswer": "Multiplexing multiple requests over a single connection",
  "explanation": "HTTP/2's main advantage is multiplexing - it allows multiple requests and responses to be sent concurrently over a single TCP connection, eliminating the Head-of-Line blocking problem of HTTP/1.1."
}
```

## Question 2

```json
{
  "question": "What is Head-of-Line (HOL) blocking in HTTP/1.1?",
  "options": [
    "When a server blocks malicious requests",
    "When a slow request blocks subsequent requests on the same connection",
    "When headers are too large",
    "When the connection is encrypted"
  ],
  "correctAnswer": "When a slow request blocks subsequent requests on the same connection",
  "explanation": "HOL blocking occurs when a slow request (like a large image download) blocks all subsequent requests on the same TCP connection, even if they're for smaller, faster resources. HTTP/2 solves this with multiplexing."
}
```

## Question 3

```json
{
  "question": "What does the 'Cache-Control: no-cache' header directive mean?",
  "options": [
    "The response should never be cached",
    "The response should be cached for a short time only",
    "The response can be cached but must be revalidated before use",
    "The response should be cached indefinitely"
  ],
  "correctAnswer": "The response can be cached but must be revalidated before use",
  "explanation": "'no-cache' doesn't mean 'don't cache' - it means the response can be stored in a cache, but it must be revalidated with the server before being used to serve a subsequent request."
}
```

## Question 4

```json
{
  "question": "What is the purpose of the 'ETag' header in HTTP responses?",
  "options": [
    "To encrypt the response content",
    "To specify the content type",
    "To indicate the server software",
    "To provide a unique identifier for resource versioning and caching"
  ],
  "correctAnswer": "To provide a unique identifier for resource versioning and caching",
  "explanation": "ETag (Entity Tag) provides a unique identifier for a specific version of a resource. Clients can use it with 'If-None-Match' headers to check if their cached version is still valid, enabling efficient caching."
}
```

## Question 5

```json
{
  "question": "What does the 'Vary' header in an HTTP response indicate?",
  "options": [
    "Which request headers the response depends on",
    "The response varies based on time",
    "The version of HTTP being used",
    "The variability of the content"
  ],
  "correctAnswer": "Which request headers the response depends on",
  "explanation": "The Vary header tells caches which request headers the response depends on. This helps caches determine if a cached response can be used for a new request with different header values."
}
```

## Question 6

```json
{
  "question": "What is the purpose of the 'If-Modified-Since' header in HTTP requests?",
  "options": [
    "To check if the server has been updated",
    "To conditionally request a resource only if it has changed since a specific date",
    "To specify when the request was created",
    "To indicate the client's timezone"
  ],
  "correctAnswer": "To conditionally request a resource only if it has changed since a specific date",
  "explanation": "If-Modified-Since allows clients to make conditional requests. If the resource hasn't changed since the specified date, the server returns 304 Not Modified, saving bandwidth and improving performance."
}
```

## Question 7

```json
{
  "question": "What is the difference between 'Connection: close' and 'Connection: keep-alive'?",
  "options": [
    "Close uses HTTPS, keep-alive uses HTTP",
    "Close is for errors, keep-alive is for success",
    "Close terminates the connection after the request, keep-alive reuses it",
    "Close is for GET requests, keep-alive is for POST requests"
  ],
  "correctAnswer": "Close terminates the connection after the request, keep-alive reuses it",
  "explanation": "'Connection: close' tells the server to close the TCP connection after sending the response, while 'keep-alive' allows the connection to be reused for multiple requests, improving performance."
}
```

## Question 8

```json
{
  "question": "What is the purpose of the 'Authorization' header in HTTP requests?",
  "options": [
    "To identify the client software",
    "To specify the content type",
    "To indicate the protocol version",
    "To provide authentication credentials"
  ],
  "correctAnswer": "To provide authentication credentials",
  "explanation": "The Authorization header contains authentication credentials (like Bearer tokens, Basic auth, or API keys) that prove the client's identity to the server, allowing access to protected resources."
}
```

## Question 9

```json
{
  "question": "What does HTTP status code 301 indicate?",
  "options": [
    "Permanent redirect",
    "Temporary redirect",
    "Bad request",
    "Server error"
  ],
  "correctAnswer": "Permanent redirect",
  "explanation": "Status code 301 means 'Moved Permanently' - the requested resource has been permanently moved to a new location. Browsers should update their bookmarks and search engines should update their indexes."
}
```

## Question 10

```json
{
  "question": "What is the purpose of the 'Content-Encoding' header?",
  "options": [
    "To specify the character encoding",
    "To indicate how the content was compressed",
    "To specify the content type",
    "To indicate the protocol version"
  ],
  "correctAnswer": "To indicate how the content was compressed",
  "explanation": "Content-Encoding specifies how the response body was compressed (e.g., 'gzip', 'deflate', 'br'). The client must decompress the content before processing it."
}
```

## Question 11

```json
{
  "question": "What is the difference between HTTP/2 and HTTP/3?",
  "options": [
    "HTTP/3 is faster and uses QUIC instead of TCP",
    "HTTP/3 has better security",
    "HTTP/3 supports more compression",
    "HTTP/3 is an older version"
  ],
  "correctAnswer": "HTTP/3 is faster and uses QUIC instead of TCP",
  "explanation": "HTTP/3 runs on QUIC (a UDP-based protocol) instead of TCP, eliminating TCP-level Head-of-Line blocking and providing faster connection establishment with 0-RTT capabilities."
}
```

## Question 12

```json
{
  "question": "What is the purpose of the 'Set-Cookie' header in HTTP responses?",
  "options": [
    "To request cookies from the client",
    "To encrypt cookie data",
    "To send cookies to the client for storage",
    "To validate cookie format"
  ],
  "correctAnswer": "To send cookies to the client for storage",
  "explanation": "Set-Cookie tells the client to store a cookie. The client will automatically send this cookie back in subsequent requests to the same domain, enabling session management and stateful interactions."
}
```

## Question 13

```json
{
  "question": "What does the 'X-Forwarded-For' header indicate?",
  "options": [
    "The original client's IP address when behind a proxy",
    "The server's IP address",
    "The protocol version",
    "The content type"
  ],
  "correctAnswer": "The original client's IP address when behind a proxy",
  "explanation": "X-Forwarded-For contains the original client's IP address when the request passes through proxies or load balancers. This helps servers identify the true origin of requests."
}
```

## Question 14

```json
{
  "question": "What is the purpose of the 'Expect: 100-continue' header?",
  "options": [
    "To expect a 100 status code",
    "To request server confirmation before sending large request body",
    "To indicate HTTP/1.1 compatibility",
    "To specify content length"
  ],
  "correctAnswer": "To request server confirmation before sending large request body",
  "explanation": "Expect: 100-continue allows clients to send headers first, wait for server confirmation (100 Continue), then send the request body. This prevents wasting bandwidth on requests the server will reject."
}
```

## Question 15

```json
{
  "question": "What does HTTP status code 429 mean?",
  "options": [
    "Too many requests (rate limiting)",
    "Server overloaded",
    "Authentication required",
    "Resource not found"
  ],
  "correctAnswer": "Too many requests (rate limiting)",
  "explanation": "Status code 429 means 'Too Many Requests' - the client has exceeded the rate limit. The response should include headers indicating when the client can retry (like Retry-After)."
}
```

## Question 16

```json
{
  "question": "What is the purpose of the 'Transfer-Encoding: chunked' header?",
  "options": [
    "To encrypt the response",
    "To send data in variable-sized chunks",
    "To compress the response",
    "To specify the protocol version"
  ],
  "correctAnswer": "To send data in variable-sized chunks",
  "explanation": "Chunked transfer encoding allows servers to send responses in variable-sized chunks without knowing the total size beforehand. Each chunk includes its size, and a zero-sized chunk marks the end."
}
```

## Question 17

```json
{
  "question": "What is the difference between 'Cache-Control: private' and 'Cache-Control: public'?",
  "options": [
    "Private is for HTTPS, public is for HTTP",
    "Private can only be cached by the user's browser, public can be cached by any cache",
    "Private is for errors, public is for success",
    "Private is faster, public is slower"
  ],
  "correctAnswer": "Private can only be cached by the user's browser, public can be cached by any cache",
  "explanation": "'private' means the response can only be cached by the user's browser, while 'public' means it can be cached by any cache (browsers, CDNs, proxy servers)."
}
```

## Question 18

```json
{
  "question": "What is the purpose of the 'Origin' header in HTTP requests?",
  "options": [
    "To specify the server origin",
    "To indicate the request's origin for CORS",
    "To specify the content type",
    "To indicate the protocol version"
  ],
  "correctAnswer": "To indicate the request's origin for CORS",
  "explanation": "The Origin header indicates the origin (scheme, hostname, port) of the request. It's used by servers to implement CORS (Cross-Origin Resource Sharing) policies."
}
```

## Question 19

```json
{
  "question": "What does HTTP status code 503 indicate?",
  "options": [
    "Server error",
    "Service unavailable (temporary)",
    "Bad request",
    "Authentication required"
  ],
  "correctAnswer": "Service unavailable (temporary)",
  "explanation": "Status code 503 means 'Service Unavailable' - the server is temporarily unable to handle the request due to maintenance, overload, or other temporary conditions."
}
```

## Question 20

```json
{
  "question": "What is the purpose of the 'Last-Modified' header in HTTP responses?",
  "options": [
    "To indicate when the server was last updated",
    "To indicate when the resource was last modified",
    "To specify the content type",
    "To indicate the protocol version"
  ],
  "correctAnswer": "To indicate when the resource was last modified",
  "explanation": "Last-Modified indicates when the resource was last changed. Clients can use this with 'If-Modified-Since' headers to implement efficient caching strategies."
}
```

## Question 21

```json
{
  "question": "What is the difference between 'Content-Type' and 'Accept' headers?",
  "options": [
    "Content-Type is for requests, Accept is for responses",
    "Content-Type specifies what's being sent, Accept specifies what can be received",
    "Content-Type is for HTML, Accept is for JSON",
    "Content-Type is required, Accept is optional"
  ],
  "correctAnswer": "Content-Type specifies what's being sent, Accept specifies what can be received",
  "explanation": "Content-Type tells the recipient what type of data is in the message body, while Accept tells the server what types of responses the client can handle (content negotiation)."
}
```

## Question 22

```json
{
  "question": "What is the purpose of the 'Retry-After' header in HTTP responses?",
  "options": [
    "To specify the protocol version",
    "To indicate when to retry a failed request",
    "To indicate the content type",
    "To specify the server software"
  ],
  "correctAnswer": "To indicate when to retry a failed request",
  "explanation": "Retry-After tells the client how long to wait before retrying a request, commonly used with 429 (Too Many Requests) or 503 (Service Unavailable) responses."
}
```

## Question 23

```json
{
  "question": "What does the 'X-Requested-With: XMLHttpRequest' header indicate?",
  "options": [
    "The request is an AJAX request",
    "The request contains XML data",
    "The request is for a specific API",
    "The request is encrypted"
  ],
  "correctAnswer": "The request is an AJAX request",
  "explanation": "This header indicates that the request was made via XMLHttpRequest (AJAX), helping servers distinguish between regular page requests and AJAX requests for different handling."
}
```

## Question 24

```json
{
  "question": "What is the purpose of the 'Access-Control-Allow-Origin' header?",
  "options": [
    "To specify which origins can access the resource (CORS)",
    "To indicate the server's origin",
    "To specify the content type",
    "To indicate the protocol version"
  ],
  "correctAnswer": "To specify which origins can access the resource (CORS)",
  "explanation": "This CORS header specifies which origins are allowed to access the resource. '*' allows all origins, or a specific origin can be specified for security."
}
```

## Question 25

```json
{
  "question": "What does HTTP status code 422 mean?",
  "options": [
    "Unprocessable Entity (semantic errors)",
    "Bad request",
    "Server error",
    "Authentication required"
  ],
  "correctAnswer": "Unprocessable Entity (semantic errors)",
  "explanation": "Status code 422 means 'Unprocessable Entity' - the request was well-formed but contains semantic errors (like validation failures) that prevent it from being processed."
}
```

## Question 26

```json
{
  "question": "What is the purpose of the 'Prefer' header in HTTP requests?",
  "options": [
    "To specify preferred content types",
    "To indicate client preferences for server behavior",
    "To specify the protocol version",
    "To indicate authentication method"
  ],
  "correctAnswer": "To indicate client preferences for server behavior",
  "explanation": "The Prefer header allows clients to express preferences for how the server should handle the request, such as 'return=minimal' or 'wait=100' for different behaviors."
}
```

## Question 27

```json
{
  "question": "What is the difference between 'Cache-Control: must-revalidate' and 'Cache-Control: no-cache'?",
  "options": [
    "Must-revalidate is stricter than no-cache",
    "Must-revalidate allows caching but requires revalidation, no-cache is more flexible",
    "Must-revalidate is for HTTPS, no-cache is for HTTP",
    "Must-revalidate is faster, no-cache is slower"
  ],
  "correctAnswer": "Must-revalidate allows caching but requires revalidation, no-cache is more flexible",
  "explanation": "'must-revalidate' means cached responses must be revalidated before use, while 'no-cache' allows caching but requires revalidation. Both allow caching but with different revalidation requirements."
}
```

## Question 28

```json
{
  "question": "What is the purpose of the 'X-Frame-Options' header?",
  "options": [
    "To specify frame dimensions",
    "To prevent clickjacking attacks",
    "To indicate the content type",
    "To specify the protocol version"
  ],
  "correctAnswer": "To prevent clickjacking attacks",
  "explanation": "X-Frame-Options prevents clickjacking by controlling whether a browser should render a page in a frame. Values like 'DENY' or 'SAMEORIGIN' help secure web applications."
}
```

## Question 29

```json
{
  "question": "What does HTTP status code 308 mean?",
  "options": [
    "Temporary redirect",
    "Permanent redirect (preserves method and body)",
    "Bad request",
    "Server error"
  ],
  "correctAnswer": "Permanent redirect (preserves method and body)",
  "explanation": "Status code 308 means 'Permanent Redirect' - similar to 301, but it preserves the HTTP method and request body when redirecting, making it safer for POST requests."
}
```

## Question 30

```json
{
  "question": "What is the purpose of the 'Strict-Transport-Security' header?",
  "options": [
    "To enforce HTTPS connections",
    "To specify the content type",
    "To indicate the protocol version",
    "To specify the server software"
  ],
  "correctAnswer": "To enforce HTTPS connections",
  "explanation": "HSTS (HTTP Strict Transport Security) tells browsers to only connect to the site using HTTPS, even if the user types 'http://'. This prevents downgrade attacks and enforces secure connections."
}
```

---

## 📊 **Quiz Summary**

**Total Questions:** 30  
**Difficulty Level:** Intermediate to Advanced  
**Topics Covered:**

- HTTP/2 and HTTP/3 protocol evolution
- Advanced caching strategies and headers
- Security headers and mechanisms
- Performance optimization concepts
- Advanced HTTP methods and status codes
- CORS and cross-origin requests
- Conditional requests and validation
- Compression and encoding
- Rate limiting and error handling
- Modern HTTP features and best practices

**Scoring Guide:**

- 25-30 correct: Excellent understanding of advanced HTTP concepts
- 20-24 correct: Good understanding with some areas for improvement
- 15-19 correct: Intermediate understanding, review recommended
- Below 15: Fundamental review needed before advanced topics

**Key Advanced Concepts Tested:**

- **Protocol Evolution**: HTTP/2 multiplexing, HTTP/3 QUIC, HOL blocking
- **Caching**: ETags, conditional requests, cache control directives
- **Security**: CORS, HSTS, X-Frame-Options, authentication headers
- **Performance**: Compression, chunked transfer, keep-alive connections
- **Advanced Headers**: Vary, Expect, Prefer, custom headers
- **Error Handling**: Rate limiting, service unavailability, validation errors

**Next Steps:**
After completing this quiz, consider exploring:

- HTTP/3 implementation and QUIC protocol details
- Advanced security headers and CSP (Content Security Policy)
- HTTP/2 server push and stream prioritization
- WebSocket and Server-Sent Events
- HTTP in microservices and API design patterns
- Performance monitoring and HTTP optimization techniques

---

_This quiz builds upon the HTTP basics and covers intermediate to advanced concepts essential for web development, API design, and system architecture._
