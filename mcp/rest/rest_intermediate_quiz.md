# 🌐 REST Intermediate - Advanced Concepts Quiz

Welcome to the REST Intermediate Quiz! This quiz builds upon fundamental REST concepts and tests your understanding of advanced API design patterns, authentication strategies, performance optimization, and real-world REST implementation scenarios.

**Instructions:**

- Each question has 4 multiple choice options
- Only one answer is correct
- Read the explanation after answering to understand the concept better
- This quiz covers intermediate-level REST concepts

---

## Question 1

```json
{
  "question": "What is the difference between PUT and PATCH in REST?",
  "options": [
    "PUT is faster than PATCH",
    "PUT replaces the entire resource, PATCH updates specific fields",
    "PUT is for creation, PATCH is for updates",
    "PUT is idempotent, PATCH is not"
  ],
  "correctAnswer": "PUT replaces the entire resource, PATCH updates specific fields",
  "explanation": "PUT replaces the entire resource with the provided representation, while PATCH applies partial modifications to a resource. PUT requires the complete resource state, while PATCH only needs the fields to be updated."
}
```

## Question 2

```json
{
  "question": "What is the purpose of the 'Link' header in REST responses?",
  "options": [
    "To specify the server location",
    "To provide HATEOAS navigation links",
    "To link to external resources",
    "To specify the content type"
  ],
  "correctAnswer": "To provide HATEOAS navigation links",
  "explanation": "The Link header provides HATEOAS (Hypermedia as the Engine of Application State) navigation links. It tells clients what actions are available and how to navigate the API, making the API self-documenting and discoverable."
}
```

## Question 3

```json
{
  "question": "What is the purpose of the 'Prefer' header in REST requests?",
  "options": [
    "To specify preferred content type",
    "To indicate client preferences for server behavior",
    "To specify preferred authentication method",
    "To indicate preferred server location"
  ],
  "correctAnswer": "To indicate client preferences for server behavior",
  "explanation": "The Prefer header allows clients to indicate their preferences for how the server should behave. For example, 'Prefer: return=minimal' asks the server to return minimal response data, or 'Prefer: respond-async' for asynchronous processing."
}
```

## Question 4

```json
{
  "question": "What is the purpose of the 'If-Match' header in REST?",
  "options": [
    "To match request and response formats",
    "To implement optimistic concurrency control",
    "To match client and server versions",
    "To match authentication tokens"
  ],
  "correctAnswer": "To implement optimistic concurrency control",
  "explanation": "The If-Match header implements optimistic concurrency control. It contains an ETag value, and the server will only process the request if the resource's current ETag matches the provided value, preventing conflicts when multiple clients modify the same resource."
}
```

## Question 5

```json
{
  "question": "What is the purpose of the 'If-Unmodified-Since' header?",
  "options": [
    "To check if the server has been modified",
    "To conditionally update a resource only if it hasn't changed since a specific time",
    "To check if the client has been modified",
    "To specify when the request was created"
  ],
  "correctAnswer": "To conditionally update a resource only if it hasn't changed since a specific time",
  "explanation": "The If-Unmodified-Since header allows conditional updates. The server will only process the request if the resource hasn't been modified since the specified date, preventing overwriting changes made by other clients."
}
```

## Question 6

```json
{
  "question": "What is the purpose of the 'Vary' header in REST responses?",
  "options": [
    "To vary the response format",
    "To indicate which request headers affect the response",
    "To vary the server location",
    "To indicate response variations"
  ],
  "correctAnswer": "To indicate which request headers affect the response",
  "explanation": "The Vary header tells caches which request headers affect the response content. For example, 'Vary: Accept-Language' indicates that responses may differ based on the Accept-Language header, helping caches store appropriate versions."
}
```

## Question 7

```json
{
  "question": "What is the purpose of the 'Retry-After' header?",
  "options": [
    "To indicate when to retry a failed request",
    "To specify the retry count",
    "To indicate server retry behavior",
    "To specify retry intervals"
  ],
  "correctAnswer": "To indicate when to retry a failed request",
  "explanation": "The Retry-After header tells clients when they can retry a request after receiving a 429 (Too Many Requests) or 503 (Service Unavailable) response. It can contain either a number of seconds or an HTTP date."
}
```

## Question 8

```json
{
  "question": "What is the purpose of the 'X-Request-ID' header?",
  "options": [
    "To identify the request type",
    "To provide a unique identifier for request tracing",
    "To identify the client",
    "To identify the server"
  ],
  "correctAnswer": "To provide a unique identifier for request tracing",
  "explanation": "The X-Request-ID header provides a unique identifier for request tracing across distributed systems. It helps correlate logs, debug issues, and track requests as they flow through multiple services."
}
```

## Question 9

```json
{
  "question": "What is the purpose of the 'X-RateLimit-*' headers?",
  "options": [
    "To specify rate limiting rules",
    "To provide rate limiting information to clients",
    "To enforce rate limiting",
    "To configure rate limiting"
  ],
  "correctAnswer": "To provide rate limiting information to clients",
  "explanation": "X-RateLimit-* headers (like X-RateLimit-Limit, X-RateLimit-Remaining, X-RateLimit-Reset) provide clients with information about their rate limiting status, helping them manage their API usage effectively."
}
```

## Question 10

```json
{
  "question": "What is the purpose of the 'X-Content-Type-Options: nosniff' header?",
  "options": [
    "To prevent content type sniffing",
    "To specify content type options",
    "To enable content type sniffing",
    "To configure content type handling"
  ],
  "correctAnswer": "To prevent content type sniffing",
  "explanation": "The X-Content-Type-Options: nosniff header prevents browsers from MIME-sniffing (guessing) the content type. This security header forces browsers to use the declared Content-Type, preventing potential security vulnerabilities."
}
```

## Question 11

```json
{
  "question": "What is the purpose of the 'X-Frame-Options' header?",
  "options": [
    "To specify frame options",
    "To prevent clickjacking attacks",
    "To configure frame behavior",
    "To enable frame embedding"
  ],
  "correctAnswer": "To prevent clickjacking attacks",
  "explanation": "The X-Frame-Options header prevents clickjacking attacks by controlling whether a browser should be allowed to render a page in a frame, iframe, embed, or object. Values include DENY, SAMEORIGIN, or ALLOW-FROM."
}
```

## Question 12

```json
{
  "question": "What is the purpose of the 'X-XSS-Protection' header?",
  "options": [
    "To enable XSS protection",
    "To configure XSS protection settings",
    "To disable XSS protection",
    "To specify XSS protection rules"
  ],
  "correctAnswer": "To enable XSS protection",
  "explanation": "The X-XSS-Protection header enables the browser's built-in XSS (Cross-Site Scripting) protection. It can be set to '1' to enable protection or '1; mode=block' to enable protection and block the page if an attack is detected."
}
```

## Question 13

```json
{
  "question": "What is the purpose of the 'Strict-Transport-Security' header?",
  "options": [
    "To enforce HTTPS connections",
    "To specify transport security",
    "To configure security settings",
    "To enable security features"
  ],
  "correctAnswer": "To enforce HTTPS connections",
  "explanation": "The Strict-Transport-Security (HSTS) header tells browsers to only connect to the site using HTTPS, even if the user types HTTP. This prevents protocol downgrade attacks and cookie hijacking."
}
```

## Question 14

```json
{
  "question": "What is the purpose of the 'Content-Security-Policy' header?",
  "options": [
    "To specify content security rules",
    "To prevent XSS and other injection attacks",
    "To configure security policies",
    "To enable security features"
  ],
  "correctAnswer": "To prevent XSS and other injection attacks",
  "explanation": "The Content-Security-Policy header helps prevent XSS and other injection attacks by specifying which resources (scripts, styles, images, etc.) are allowed to be loaded and executed."
}
```

## Question 15

```json
{
  "question": "What is the purpose of the 'Access-Control-Allow-Origin' header?",
  "options": [
    "To allow cross-origin requests",
    "To specify allowed origins",
    "To configure CORS settings",
    "To enable CORS"
  ],
  "correctAnswer": "To allow cross-origin requests",
  "explanation": "The Access-Control-Allow-Origin header is part of CORS (Cross-Origin Resource Sharing) and specifies which origins are allowed to access the resource. It can be set to a specific origin, '*' for all origins, or omitted to deny access."
}
```

## Question 16

```json
{
  "question": "What is the purpose of the 'Access-Control-Allow-Methods' header?",
  "options": [
    "To specify allowed HTTP methods",
    "To configure CORS methods",
    "To enable CORS methods",
    "To allow specific methods"
  ],
  "correctAnswer": "To specify allowed HTTP methods",
  "explanation": "The Access-Control-Allow-Methods header specifies which HTTP methods are allowed for cross-origin requests. It's used in preflight responses to tell the browser which methods the server accepts."
}
```

## Question 17

```json
{
  "question": "What is the purpose of the 'Access-Control-Allow-Headers' header?",
  "options": [
    "To specify allowed request headers",
    "To configure CORS headers",
    "To enable CORS headers",
    "To allow specific headers"
  ],
  "correctAnswer": "To specify allowed request headers",
  "explanation": "The Access-Control-Allow-Headers header specifies which request headers are allowed in cross-origin requests. It's used in preflight responses to tell the browser which headers the server accepts."
}
```

## Question 18

```json
{
  "question": "What is the purpose of the 'Access-Control-Max-Age' header?",
  "options": [
    "To specify CORS cache duration",
    "To configure CORS age",
    "To enable CORS caching",
    "To set CORS timeout"
  ],
  "correctAnswer": "To specify CORS cache duration",
  "explanation": "The Access-Control-Max-Age header specifies how long (in seconds) the results of a preflight request can be cached. This reduces the number of preflight requests by allowing browsers to cache the CORS policy."
}
```

## Question 19

```json
{
  "question": "What is the purpose of the 'WWW-Authenticate' header?",
  "options": [
    "To specify authentication method",
    "To request authentication",
    "To configure authentication",
    "To enable authentication"
  ],
  "correctAnswer": "To request authentication",
  "explanation": "The WWW-Authenticate header is sent with 401 Unauthorized responses to tell the client what authentication method is required. It specifies the authentication scheme (like 'Basic' or 'Bearer') and any parameters."
}
```

## Question 20

```json
{
  "question": "What is the purpose of the 'Proxy-Authenticate' header?",
  "options": [
    "To specify proxy authentication",
    "To request proxy authentication",
    "To configure proxy authentication",
    "To enable proxy authentication"
  ],
  "correctAnswer": "To request proxy authentication",
  "explanation": "The Proxy-Authenticate header is sent with 407 Proxy Authentication Required responses to tell the client what authentication method is required to access the proxy server."
}
```

## Question 21

```json
{
  "question": "What is the purpose of the 'Authorization' header with 'Bearer' token?",
  "options": [
    "To provide bearer token authentication",
    "To specify bearer authentication",
    "To configure bearer authentication",
    "To enable bearer authentication"
  ],
  "correctAnswer": "To provide bearer token authentication",
  "explanation": "The Authorization header with 'Bearer' token provides OAuth 2.0 or JWT token authentication. The format is 'Authorization: Bearer <token>' where the token is sent without additional encoding."
}
```

## Question 22

```json
{
  "question": "What is the purpose of the 'Authorization' header with 'Basic' authentication?",
  "options": [
    "To provide basic authentication",
    "To specify basic authentication",
    "To configure basic authentication",
    "To enable basic authentication"
  ],
  "correctAnswer": "To provide basic authentication",
  "explanation": "The Authorization header with 'Basic' authentication provides username and password authentication. The credentials are base64-encoded and sent as 'Authorization: Basic <encoded-credentials>'."
}
```

## Question 23

```json
{
  "question": "What is the purpose of the 'Cookie' header?",
  "options": [
    "To send cookies to the server",
    "To specify cookie settings",
    "To configure cookies",
    "To enable cookies"
  ],
  "correctAnswer": "To send cookies to the server",
  "explanation": "The Cookie header sends cookies from the client to the server. It contains name-value pairs of cookies that the client has stored and wants to send with the request for session management or other purposes."
}
```

## Question 24

```json
{
  "question": "What is the purpose of the 'Set-Cookie' header?",
  "options": [
    "To set cookies on the client",
    "To specify cookie settings",
    "To configure cookies",
    "To enable cookies"
  ],
  "correctAnswer": "To set cookies on the client",
  "explanation": "The Set-Cookie header tells the client to store a cookie. It can include attributes like Expires, Max-Age, Domain, Path, Secure, HttpOnly, and SameSite to control cookie behavior and security."
}
```

## Question 25

```json
{
  "question": "What is the purpose of the 'Cache-Control' header?",
  "options": [
    "To control caching behavior",
    "To specify cache settings",
    "To configure caching",
    "To enable caching"
  ],
  "correctAnswer": "To control caching behavior",
  "explanation": "The Cache-Control header controls how responses are cached by browsers, proxies, and other intermediaries. It can specify directives like 'no-cache', 'no-store', 'max-age', 'public', 'private', etc."
}
```

## Question 26

```json
{
  "question": "What is the purpose of the 'Expires' header?",
  "options": [
    "To specify when a response expires",
    "To configure expiration",
    "To enable expiration",
    "To set expiration time"
  ],
  "correctAnswer": "To specify when a response expires",
  "explanation": "The Expires header specifies when a response expires and should no longer be considered fresh. It contains an HTTP date after which the response is considered stale and should be revalidated."
}
```

## Question 27

```json
{
  "question": "What is the purpose of the 'Last-Modified' header?",
  "options": [
    "To specify when the resource was last modified",
    "To configure modification time",
    "To enable modification tracking",
    "To set modification time"
  ],
  "correctAnswer": "To specify when the resource was last modified",
  "explanation": "The Last-Modified header specifies when the resource was last modified. It's used for caching and conditional requests, allowing clients to check if their cached version is still current."
}
```

## Question 28

```json
{
  "question": "What is the purpose of the 'If-None-Match' header?",
  "options": [
    "To check if the resource has changed",
    "To specify ETag matching",
    "To configure ETag behavior",
    "To enable ETag checking"
  ],
  "correctAnswer": "To check if the resource has changed",
  "explanation": "The If-None-Match header allows conditional requests using ETags. If the resource's current ETag doesn't match the provided value, the server returns the resource. If it matches, the server returns 304 Not Modified."
}
```

## Question 29

```json
{
  "question": "What is the purpose of the 'Accept-Encoding' header?",
  "options": [
    "To specify acceptable content encodings",
    "To configure encoding settings",
    "To enable encoding",
    "To set encoding preferences"
  ],
  "correctAnswer": "To specify acceptable content encodings",
  "explanation": "The Accept-Encoding header tells the server what content encodings the client can handle. Common values include 'gzip', 'deflate', 'br' (Brotli), allowing the server to compress responses appropriately."
}
```

## Question 30

```json
{
  "question": "What is the purpose of the 'Content-Encoding' header?",
  "options": [
    "To specify the encoding of the response content",
    "To configure content encoding",
    "To enable content encoding",
    "To set content encoding"
  ],
  "correctAnswer": "To specify the encoding of the response content",
  "explanation": "The Content-Encoding header specifies how the response content has been encoded (e.g., 'gzip', 'deflate', 'br'). It tells the client what decoding method to use before processing the content."
}
```

---

## 📊 **Quiz Summary**

**Total Questions:** 30  
**Difficulty Level:** Intermediate  
**Topics Covered:**

- Advanced HTTP headers and their purposes
- Security headers and best practices
- CORS (Cross-Origin Resource Sharing) implementation
- Authentication and authorization headers
- Caching and performance optimization headers
- Conditional requests and ETags
- Content negotiation and encoding
- Rate limiting and request tracing

**Scoring Guide:**

- 25-30 correct: Excellent understanding of intermediate REST concepts
- 20-24 correct: Good understanding with some areas for improvement
- 15-19 correct: Basic understanding, review recommended
- Below 15: Fundamental review needed

**Key Intermediate REST Concepts Tested:**

- **Advanced Headers**: Understanding specialized HTTP headers for specific use cases
- **Security**: Implementation of security headers to protect against common attacks
- **CORS**: Proper configuration of cross-origin resource sharing
- **Authentication**: Various authentication methods and their implementation
- **Performance**: Caching strategies and optimization techniques
- **Conditional Requests**: ETags and conditional request headers for efficient resource management
- **Content Negotiation**: Handling different content types and encodings
- **Rate Limiting**: Implementation of rate limiting headers and their purpose
- **Security Headers**: X-Content-Type-Options, X-Frame-Options, X-XSS-Protection, HSTS, CSP
- **CORS Headers**: Access-Control-Allow-\* headers for cross-origin requests
- **Authentication**: Bearer tokens, Basic auth, WWW-Authenticate, Proxy-Authenticate
- **Caching**: Cache-Control, Expires, ETags, conditional requests
- **Performance**: Content encoding, compression, rate limiting
- **Tracing**: Request IDs for distributed system debugging

**Next Steps:**
After completing this quiz, consider exploring:

- Advanced REST API design patterns and anti-patterns
- API versioning strategies (URL, header, content negotiation)
- GraphQL vs REST comparison and use cases
- REST in microservices architecture
- API documentation with OpenAPI/Swagger
- REST API testing strategies and tools
- Performance monitoring and optimization
- Advanced security implementations (OAuth 2.0, JWT, API keys)

---

_This quiz is based on the REST theory content from the MCP learning repository. For more detailed explanations, refer to the original documentation._
