# 🌐 HTTP Advanced - Expert Level Quiz

Welcome to the HTTP Advanced Quiz! This quiz will test your expert-level understanding of HTTP including deep protocol mechanics, performance optimization, security vulnerabilities, advanced debugging, and cutting-edge HTTP technologies.

**Instructions:**

- Each question has 4 multiple choice options
- Only one answer is correct
- Read the explanation after answering to understand the concept better
- This quiz covers expert-level HTTP concepts and implementation details

---

## Question 1

```json
{
  "question": "What is the difference between HTTP/2's Server Push and HTTP/3's Server Push?",
  "options": [
    "HTTP/3 doesn't support Server Push",
    "HTTP/3 Server Push uses QUIC streams instead of HTTP/2 frames",
    "HTTP/2 Server Push is faster",
    "HTTP/3 Server Push requires different headers"
  ],
  "correctAnswer": "HTTP/3 Server Push uses QUIC streams instead of HTTP/2 frames",
  "explanation": "HTTP/3 Server Push uses QUIC streams (bidirectional byte streams) rather than HTTP/2's frame-based approach. This provides better flow control and eliminates stream-level Head-of-Line blocking that can still occur in HTTP/2."
}
```

## Question 2

```json
{
  "question": "What is the purpose of the 'Alt-Svc' header in HTTP responses?",
  "options": [
    "To specify alternative services for the same resource",
    "To indicate server availability",
    "To specify content encoding alternatives",
    "To provide authentication alternatives"
  ],
  "correctAnswer": "To specify alternative services for the same resource",
  "explanation": "Alt-Svc (Alternative Services) allows servers to advertise alternative endpoints for the same resource, such as HTTP/3 endpoints or different protocols. This enables protocol negotiation and service discovery."
}
```

## Question 3

```json
{
  "question": "What is the difference between 'Cache-Control: immutable' and 'Cache-Control: max-age'?",
  "options": [
    "Immutable is for static files, max-age is for dynamic content",
    "Immutable tells browsers the resource will never change, max-age sets a time limit",
    "Immutable is faster, max-age is slower",
    "Immutable requires revalidation, max-age doesn't"
  ],
  "correctAnswer": "Immutable tells browsers the resource will never change, max-age sets a time limit",
  "explanation": "'immutable' indicates the resource will never change, so browsers can skip revalidation entirely. 'max-age' sets a time limit after which the cache entry expires and must be revalidated."
}
```

## Question 4

```json
{
  "question": "What is the purpose of the 'Link' header with 'rel=preload'?",
  "options": [
    "To preload critical resources",
    "To indicate linked resources",
    "To specify content relationships",
    "To provide authentication links"
  ],
  "correctAnswer": "To preload critical resources",
  "explanation": "The Link header with 'rel=preload' tells browsers to fetch and cache resources early, even before they're needed. This improves performance by reducing the critical rendering path."
}
```

## Question 5

```json
{
  "question": "What is the difference between HTTP/2's HPACK and HTTP/3's QPACK compression?",
  "options": [
    "QPACK is faster but less efficient",
    "QPACK is designed for QUIC's stream-based nature",
    "HPACK is more secure",
    "QPACK doesn't support dynamic tables"
  ],
  "correctAnswer": "QPACK is designed for QUIC's stream-based nature",
  "explanation": "QPACK is specifically designed for QUIC's stream-based architecture, handling the challenges of compressing headers across multiple streams where packet loss can affect different streams independently."
}
```

## Question 6

```json
{
  "question": "What is the purpose of the 'Early-Data' header in HTTP requests?",
  "options": [
    "To indicate 0-RTT data",
    "To specify early content",
    "To request fast responses",
    "To indicate protocol version"
  ],
  "correctAnswer": "To indicate 0-RTT data",
  "explanation": "The Early-Data header indicates that the request was sent as 0-RTT data (before the TLS handshake completed). This helps servers identify and handle such requests appropriately, often with additional validation."
}
```

## Question 7

```json
{
  "question": "What is the difference between 'Cache-Control: stale-while-revalidate' and 'Cache-Control: stale-if-error'?",
  "options": [
    "stale-while-revalidate is for errors, stale-if-error is for revalidation",
    "stale-while-revalidate serves stale content during revalidation, stale-if-error serves stale content on errors",
    "stale-while-revalidate is faster",
    "stale-if-error is more secure"
  ],
  "correctAnswer": "stale-while-revalidate serves stale content during revalidation, stale-if-error serves stale content on errors",
  "explanation": "'stale-while-revalidate' allows serving stale content while revalidating in the background. 'stale-if-error' allows serving stale content only when the server returns an error."
}
```

## Question 8

```json
{
  "question": "What is the purpose of the 'Cross-Origin-Embedder-Policy' header?",
  "options": [
    "To control cross-origin embedding",
    "To enable SharedArrayBuffer and other features",
    "To specify CORS policies",
    "To control frame embedding"
  ],
  "correctAnswer": "To enable SharedArrayBuffer and other features",
  "explanation": "COEP (Cross-Origin-Embedder-Policy) enables features like SharedArrayBuffer by ensuring all resources are either same-origin or explicitly marked as CORS-enabled, creating a secure context."
}
```

## Question 9

```json
{
  "question": "What is the difference between HTTP/2's PRIORITY frame and HTTP/3's stream prioritization?",
  "options": [
    "HTTP/3 doesn't support prioritization",
    "HTTP/3 uses QUIC's native stream prioritization",
    "HTTP/2 prioritization is more efficient",
    "HTTP/3 requires different priority headers"
  ],
  "correctAnswer": "HTTP/3 uses QUIC's native stream prioritization",
  "explanation": "HTTP/3 leverages QUIC's built-in stream prioritization mechanisms rather than HTTP/2's separate PRIORITY frames, providing more efficient and flexible prioritization."
}
```

## Question 10

```json
{
  "question": "What is the purpose of the 'Sec-Fetch-*' headers in HTTP requests?",
  "options": [
    "To provide security context for requests",
    "To specify fetch policies",
    "To indicate protocol security",
    "To control CORS policies"
  ],
  "correctAnswer": "To provide security context for requests",
  "explanation": "Sec-Fetch-* headers (like Sec-Fetch-Dest, Sec-Fetch-Mode, Sec-Fetch-Site) provide servers with context about how the request was initiated, helping implement security policies and prevent certain attacks."
}
```

## Question 11

```json
{
  "question": "What is the difference between 'Content-Security-Policy' and 'Content-Security-Policy-Report-Only'?",
  "options": [
    "Report-Only is for testing, CSP is for enforcement",
    "CSP is stricter",
    "Report-Only doesn't block violations",
    "CSP is faster"
  ],
  "correctAnswer": "Report-Only doesn't block violations",
  "explanation": "CSP-Report-Only monitors violations and sends reports but doesn't block content. Regular CSP actively blocks violations. Report-Only is useful for testing policies before enforcement."
}
```

## Question 12

```json
{
  "question": "What is the purpose of the 'Accept-CH' header in HTTP requests?",
  "options": [
    "To accept challenge responses",
    "To indicate client hints support",
    "To specify content handling",
    "To control caching behavior"
  ],
  "correctAnswer": "To indicate client hints support",
  "explanation": "Accept-CH (Accept Client Hints) tells the server that the client supports Client Hints headers, allowing the server to send optimized responses based on client capabilities."
}
```

## Question 13

```json
{
  "question": "What is the difference between HTTP/2's flow control and HTTP/3's flow control?",
  "options": [
    "HTTP/3 doesn't have flow control",
    "HTTP/3 has both connection-level and stream-level flow control",
    "HTTP/2 flow control is more efficient",
    "HTTP/3 requires different flow control headers"
  ],
  "correctAnswer": "HTTP/3 has both connection-level and stream-level flow control",
  "explanation": "HTTP/3 implements flow control at both the QUIC connection level and individual stream level, providing more granular control than HTTP/2's stream-only flow control."
}
```

## Question 14

```json
{
  "question": "What is the purpose of the 'Permissions-Policy' header?",
  "options": [
    "To control browser permissions",
    "To specify security policies",
    "To control feature access",
    "To manage authentication"
  ],
  "correctAnswer": "To control feature access",
  "explanation": "Permissions-Policy (formerly Feature-Policy) allows servers to control which browser features and APIs can be used, such as camera, microphone, geolocation, and payment APIs."
}
```

## Question 15

```json
{
  "question": "What is the difference between 'Cache-Control: must-understand' and 'Cache-Control: proxy-revalidate'?",
  "options": [
    "must-understand is for proxies, proxy-revalidate is for browsers",
    "must-understand requires caches to understand the directive, proxy-revalidate applies only to proxy caches",
    "must-understand is stricter",
    "proxy-revalidate is faster"
  ],
  "correctAnswer": "must-understand requires caches to understand the directive, proxy-revalidate applies only to proxy caches",
  "explanation": "'must-understand' requires caches to understand and follow the directive or return an error. 'proxy-revalidate' applies revalidation rules only to proxy caches, not user agent caches."
}
```

## Question 16

```json
{
  "question": "What is the purpose of the 'Cross-Origin-Opener-Policy' header?",
  "options": [
    "To control cross-origin window opening",
    "To enable SharedArrayBuffer",
    "To specify CORS policies",
    "To control frame embedding"
  ],
  "correctAnswer": "To control cross-origin window opening",
  "explanation": "COOP (Cross-Origin-Opener-Policy) controls whether the browser creates a new browsing context group for the page, preventing cross-origin window access and enabling certain security features."
}
```

## Question 17

```json
{
  "question": "What is the difference between HTTP/2's SETTINGS frame and HTTP/3's transport parameters?",
  "options": [
    "HTTP/3 doesn't have settings",
    "HTTP/3 uses QUIC transport parameters instead of HTTP/2 settings",
    "HTTP/2 settings are more flexible",
    "HTTP/3 requires different configuration"
  ],
  "correctAnswer": "HTTP/3 uses QUIC transport parameters instead of HTTP/2 settings",
  "explanation": "HTTP/3 uses QUIC's transport parameters (negotiated during the handshake) rather than HTTP/2's SETTINGS frames, providing similar functionality but integrated with the transport layer."
}
```

## Question 18

```json
{
  "question": "What is the purpose of the 'Clear-Site-Data' header in HTTP responses?",
  "options": [
    "To clear browser data",
    "To specify data retention policies",
    "To control caching behavior",
    "To manage session data"
  ],
  "correctAnswer": "To clear browser data",
  "explanation": "Clear-Site-Data allows servers to instruct browsers to clear specific types of data (cookies, cache, storage) for the site, useful for logout functionality and privacy controls."
}
```

## Question 19

```json
{
  "question": "What is the difference between 'Cache-Control: only-if-cached' and 'Cache-Control: no-cache'?",
  "options": [
    "only-if-cached requires cache, no-cache allows cache",
    "only-if-cached only uses cached responses, no-cache requires revalidation",
    "only-if-cached is faster",
    "no-cache is more secure"
  ],
  "correctAnswer": "only-if-cached only uses cached responses, no-cache requires revalidation",
  "explanation": "'only-if-cached' tells the client to only return cached responses (504 if not cached). 'no-cache' allows caching by any cache but requires revalidation before use."
}
```

## Question 20

```json
{
  "question": "What is the purpose of the 'Sec-GPC' header in HTTP requests?",
  "options": [
    "To indicate Global Privacy Control preference",
    "To specify security protocols",
    "To control privacy settings",
    "To manage data collection"
  ],
  "correctAnswer": "To indicate Global Privacy Control preference",
  "explanation": "Sec-GPC (Global Privacy Control) indicates the user's privacy preference, allowing websites to respect opt-out signals for data collection and tracking."
}
```

## Question 21

```json
{
  "question": "What is the difference between HTTP/2's GOAWAY frame and HTTP/3's connection closure?",
  "options": [
    "HTTP/3 doesn't support graceful shutdown",
    "HTTP/3 uses QUIC's connection closure mechanisms",
    "HTTP/2 shutdown is more efficient",
    "HTTP/3 requires different shutdown headers"
  ],
  "correctAnswer": "HTTP/3 uses QUIC's connection closure mechanisms",
  "explanation": "HTTP/3 leverages QUIC's built-in connection closure mechanisms rather than HTTP/2's GOAWAY frame, providing similar graceful shutdown capabilities."
}
```

## Question 22

```json
{
  "question": "What is the purpose of the 'Cross-Origin-Resource-Policy' header?",
  "options": [
    "To control cross-origin resource access",
    "To specify CORS policies",
    "To control frame embedding",
    "To manage authentication"
  ],
  "correctAnswer": "To control cross-origin resource access",
  "explanation": "CORP (Cross-Origin-Resource-Policy) controls whether the resource can be loaded by other origins, providing additional protection beyond CORS for certain types of resources."
}
```

## Question 23

```json
{
  "question": "What is the difference between 'Cache-Control: no-transform' and 'Cache-Control: no-store'?",
  "options": [
    "no-transform prevents modifications, no-store prevents caching",
    "no-transform is for proxies, no-store is for browsers",
    "no-transform is stricter",
    "no-store is faster"
  ],
  "correctAnswer": "no-transform prevents modifications, no-store prevents caching",
  "explanation": "'no-transform' prevents intermediaries from modifying the response (compression, format conversion). 'no-store' prevents any caching of the response."
}
```

## Question 24

```json
{
  "question": "What is the purpose of the 'Sec-CH-UA-*' headers in HTTP requests?",
  "options": [
    "To provide client capabilities information",
    "To specify security protocols",
    "To control user agent behavior",
    "To manage authentication"
  ],
  "correctAnswer": "To provide client capabilities information",
  "explanation": "Sec-CH-UA-* headers (Client Hints) provide servers with information about the client's capabilities, such as platform, browser version, and device characteristics, enabling optimized responses."
}
```

## Question 25

```json
{
  "question": "What is the difference between HTTP/2's PING frame and HTTP/3's connection health checks?",
  "options": [
    "HTTP/3 doesn't support health checks",
    "HTTP/3 uses QUIC's native connection health mechanisms",
    "HTTP/2 health checks are more efficient",
    "HTTP/3 requires different health check headers"
  ],
  "correctAnswer": "HTTP/3 uses QUIC's native connection health mechanisms",
  "explanation": "HTTP/3 leverages QUIC's built-in connection health checking mechanisms rather than HTTP/2's PING frames, providing similar functionality for connection monitoring."
}
```

## Question 26

```json
{
  "question": "What is the purpose of the 'Origin-Agent-Cluster' header in HTTP responses?",
  "options": [
    "To control origin isolation",
    "To specify agent clustering",
    "To manage authentication",
    "To control caching behavior"
  ],
  "correctAnswer": "To control origin isolation",
  "explanation": "Origin-Agent-Cluster allows servers to control whether the page should be isolated in its own agent cluster, providing additional security isolation between origins."
}
```

## Question 27

```json
{
  "question": "What is the difference between 'Cache-Control: private' and 'Cache-Control: no-cache'?",
  "options": [
    "private allows caching by user agent only, no-cache requires revalidation",
    "private is for HTTPS, no-cache is for HTTP",
    "private is stricter",
    "no-cache is faster"
  ],
  "correctAnswer": "private allows caching by user agent only, no-cache requires revalidation",
  "explanation": "'private' allows caching only by the user agent (browser), not shared caches. 'no-cache' allows caching by any cache but requires revalidation before use."
}
```

## Question 28

```json
{
  "question": "What is the purpose of the 'Sec-Fetch-Site' header in HTTP requests?",
  "options": [
    "To indicate the relationship between the request origin and target",
    "To specify security protocols",
    "To control CORS policies",
    "To manage authentication"
  ],
  "correctAnswer": "To indicate the relationship between the request origin and target",
  "explanation": "Sec-Fetch-Site indicates the relationship between the request's origin and the target (same-origin, same-site, cross-site, or none), helping servers implement appropriate security policies."
}
```

## Question 29

```json
{
  "question": "What is the difference between HTTP/2's WINDOW_UPDATE frame and HTTP/3's flow control?",
  "options": [
    "HTTP/3 doesn't have flow control",
    "HTTP/3 uses QUIC's native flow control mechanisms",
    "HTTP/2 flow control is more efficient",
    "HTTP/3 requires different flow control headers"
  ],
  "correctAnswer": "HTTP/3 uses QUIC's native flow control mechanisms",
  "explanation": "HTTP/3 leverages QUIC's built-in flow control mechanisms rather than HTTP/2's WINDOW_UPDATE frames, providing similar functionality for managing data flow."
}
```

## Question 30

```json
{
  "question": "What is the purpose of the 'Cross-Origin-Embedder-Policy-Report-Only' header?",
  "options": [
    "To monitor COEP violations without enforcement",
    "To specify CORS policies",
    "To control frame embedding",
    "To manage authentication"
  ],
  "correctAnswer": "To monitor COEP violations without enforcement",
  "explanation": "COEP-Report-Only monitors violations of the Cross-Origin-Embedder-Policy and sends reports but doesn't enforce the policy, useful for testing before full implementation."
}
```

---

## 📊 **Quiz Summary**

**Total Questions:** 30  
**Difficulty Level:** Expert/Advanced  
**Topics Covered:**

- HTTP/3 and QUIC protocol details
- Advanced security headers and policies
- Modern caching strategies and directives
- Performance optimization techniques
- Browser security features and isolation
- Protocol evolution and implementation details
- Advanced debugging and monitoring
- Cutting-edge HTTP features and standards

**Scoring Guide:**

- 25-30 correct: Expert-level HTTP knowledge
- 20-24 correct: Advanced understanding with some areas for improvement
- 15-19 correct: Good intermediate knowledge, expert review recommended
- Below 15: Advanced fundamentals review needed

**Key Expert Concepts Tested:**

- **Protocol Deep Dive**: HTTP/3 QUIC streams, QPACK compression, transport parameters
- **Advanced Security**: COEP, COOP, CORP, CSP, permissions policies
- **Modern Caching**: Immutable, stale-while-revalidate, must-understand directives
- **Performance Optimization**: Server push, preloading, client hints
- **Browser Features**: SharedArrayBuffer, privacy controls, agent clusters
- **Protocol Mechanics**: Flow control, prioritization, connection management

**Expert-Level Topics:**

- **HTTP/3 Implementation**: QUIC streams, transport parameters, native features
- **Security Isolation**: Cross-origin policies, agent clusters, privacy controls
- **Advanced Caching**: Complex cache control directives, revalidation strategies
- **Performance Features**: Server push, preloading, client hints, early data
- **Modern Standards**: Latest HTTP features, browser security policies
- **Protocol Optimization**: Flow control, prioritization, connection management

**Next Steps:**
After completing this quiz, consider exploring:

- HTTP/3 implementation and QUIC protocol internals
- Advanced security headers and CSP implementation
- Performance monitoring and HTTP optimization at scale
- Browser security features and isolation mechanisms
- Protocol design and standardization processes
- HTTP in edge computing and CDN optimization

---

_This quiz covers expert-level HTTP concepts essential for protocol implementers, security experts, and performance optimization specialists._
