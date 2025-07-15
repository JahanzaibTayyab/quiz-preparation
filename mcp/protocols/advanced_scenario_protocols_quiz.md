# 🧠 Advanced Scenario-Based Protocols Quiz (HTTP, REST, JSON-RPC)

**Instructions:**

- Each question presents a real-world scenario or code example.
- Choose the best answer from the options.
- Read the explanation for deep understanding.

---

## Question 1: Diagnosing Intermittent Data Loss in a Hybrid System

You are the principal engineer for a logistics platform. The system uses REST APIs (HTTP/2) for CRUD operations, JSON-RPC over WebSockets for real-time vehicle tracking, and a nightly batch job that syncs data to a data warehouse. Recently, operations staff report that some vehicle location updates are missing from the warehouse, but the real-time dashboard always shows the correct current location. You review the code and see that the batch job fetches data from the REST API, not the WebSocket stream. The REST API endpoint for locations is eventually consistent, with a cache layer in front.

Which is the most likely cause of the missing data in the warehouse?

- A) The WebSocket stream is unreliable and drops messages
- B) The REST API cache is not updated in real time, so the batch job misses some updates
- C) The batch job is not parsing JSON correctly
- D) The REST API is returning HTTP 500 errors
- E) The data warehouse is not ingesting all records

**Correct Answer:** B

**Explanation:**
The REST API is eventually consistent and uses a cache, so the batch job may read stale data and miss updates that were only visible in the real-time WebSocket stream. The dashboard is always correct because it uses the live stream, but the warehouse lags behind due to the cache.

---

## Question 2: Debugging a REST API with Inconsistent Error Handling

You inherit a REST API for a payment system. The API sometimes returns HTTP 200 with an error message in the body, sometimes HTTP 400 or 500 with a JSON error object, and sometimes just plain text. Clients are reporting unpredictable behavior and difficulty handling errors. Here is a sample endpoint implementation:

```python
@app.route('/pay', methods=['POST'])
def pay():
    data = request.json
    if not data.get('amount'):
        return {'error': 'Missing amount'}, 200
    if data['amount'] < 0:
        return 'Negative amount', 400
    try:
        process_payment(data)
    except Exception as e:
        return str(e), 500
    return {'status': 'success'}, 200
```

What is the best way to refactor this endpoint for robust, predictable error handling?

- A) Always return HTTP 200 with an error message in the body
- B) Use appropriate HTTP status codes and a consistent JSON error format
- C) Return plain text for errors and JSON for success
- D) Only return HTTP 500 for all errors
- E) Use HTTP 204 for all responses

**Correct Answer:** B

**Explanation:**
REST APIs should use appropriate HTTP status codes (400 for client errors, 500 for server errors) and a consistent JSON error format. This allows clients to reliably parse and handle errors.

---

## Question 3: Teaching Protocol Migration and Backward Compatibility

You are mentoring a team migrating a public API from REST (HTTP/1.1) to JSON-RPC over HTTP/2 for efficiency. The API is used by hundreds of third-party clients, some of which are slow to upgrade. The new JSON-RPC API supports batch requests and notifications, but the old REST API does not. The team wants to deprecate the REST API immediately.

What is the best approach to ensure a smooth migration and backward compatibility?

- A) Deprecate the REST API immediately and force all clients to upgrade
- B) Run both APIs in parallel, provide clear migration guides, and monitor usage
- C) Only support JSON-RPC for new features, keep REST for existing endpoints
- D) Use a proxy to translate REST calls to JSON-RPC
- E) Remove the REST API after a short grace period

**Correct Answer:** B

**Explanation:**
Running both APIs in parallel allows clients to migrate at their own pace. Providing migration guides and monitoring usage ensures a smooth transition and minimizes disruption.

---

## Question 4: Analyzing a Security Breach in API Authentication

A SaaS platform exposes both REST and JSON-RPC endpoints. REST endpoints use OAuth2 with short-lived tokens, while JSON-RPC endpoints accept an API key in a query parameter. After a security audit, you discover that attackers have accessed user data by replaying URLs with leaked API keys from server logs. The team proposes switching to HTTP Basic Auth for JSON-RPC.

What is the most secure and practical solution?

- A) Continue using API keys, but rotate them frequently
- B) Use HTTP Basic Auth with credentials in the URL
- C) Require API keys in HTTP headers, not query parameters
- D) Switch JSON-RPC endpoints to OAuth2 with token-based auth
- E) Only allow JSON-RPC over internal networks

**Correct Answer:** D

**Explanation:**
OAuth2 with token-based authentication is more secure and consistent with the REST endpoints. API keys in query parameters are easily leaked; headers are better, but OAuth2 is the industry standard for secure, auditable access.

---

## Question 5: Debugging HTTP/2 Multiplexing and Head-of-Line Blocking

A global e-commerce platform uses HTTP/2 for all REST APIs. During peak sales, users report slow checkout times. Analysis shows that large image uploads from sellers are causing delays for unrelated API calls. The system uses a single HTTP/2 connection per client. What is the most likely cause and best mitigation?

- A) HTTP/2 does not support multiplexing; switch to HTTP/1.1
- B) TCP head-of-line blocking affects all streams in a single connection; use separate connections for large uploads
- C) The server is not compressing images; enable compression
- D) The client is not using persistent connections
- E) Use HTTP/3 to eliminate all blocking

**Correct Answer:** B

**Explanation:**
TCP head-of-line blocking in HTTP/2 can cause large uploads to delay other streams. Using separate connections for large uploads prevents this and improves overall performance.

---

## Question 6: Diagnosing Data Consistency in Event-Driven Architectures

A fintech startup uses REST APIs for account management and JSON-RPC notifications for transaction events. Occasionally, account balances in the REST API lag behind the events shown in the real-time dashboard. The REST API is backed by a relational database with eventual consistency. The dashboard subscribes to JSON-RPC notifications from a message broker. What is the most likely cause of the inconsistency?

- A) The REST API is not using HTTP/2
- B) The message broker is dropping events
- C) The REST API database replication lags behind the event stream
- D) The dashboard is not parsing JSON correctly
- E) The JSON-RPC notifications are not idempotent

**Correct Answer:** C

**Explanation:**
Eventual consistency in the REST API's database means that updates from the event stream may not be immediately visible in the REST API, causing temporary inconsistencies between the dashboard and the API.

---

## Question 7: Teaching Students to Debug Protocol Integration Bugs

You are teaching a class on integrating REST and JSON-RPC in a microservices architecture. A student reports that their service, which calls a REST API and then sends a JSON-RPC notification, sometimes fails to deliver the notification. Logs show HTTP 200 from the REST call, but no response from the JSON-RPC server. What is the most likely cause?

- A) The REST API is returning incorrect status codes
- B) The JSON-RPC notification is sent without an 'id', so no response is expected
- C) The REST call is not committed before the notification is sent
- D) The JSON-RPC server is down
- E) The client is not using HTTP/2

**Correct Answer:** B

**Explanation:**
JSON-RPC notifications (requests without an 'id') do not generate responses. The student may be expecting a response where none is defined by the protocol.

---

## Question 8: Evaluating Protocol Trade-Offs for Mobile APIs

You are designing an API for a mobile app that must work offline, sync data efficiently, and minimize bandwidth. The team proposes using REST for all operations. You suggest considering JSON-RPC with batch requests and offline queuing. What is the main advantage of JSON-RPC in this scenario?

- A) JSON-RPC is more secure than REST
- B) Batch requests reduce network overhead and support offline queuing
- C) REST cannot be used on mobile devices
- D) JSON-RPC is easier to document
- E) REST does not support authentication

**Correct Answer:** B

**Explanation:**
JSON-RPC supports batch requests and can queue operations for later sync, reducing network overhead and improving offline support. REST is stateless and less suited to these requirements.

---

## Question 9: Analyzing a Protocol Migration Failure

A company migrates its public API from REST to JSON-RPC over WebSockets to support real-time features. After launch, clients report that some requests never receive a response, and the client libraries hang indefinitely. The migration plan did not include changes to client-side error handling. What is the most likely root cause?

- A) WebSockets are unreliable and drop messages
- B) JSON-RPC notifications do not generate responses, and clients are not handling this case
- C) The server is not supporting batch requests
- D) The REST API was more reliable
- E) The WebSocket server is overloaded

**Correct Answer:** B

**Explanation:**
JSON-RPC notifications (requests without an 'id') do not generate responses. If clients expect a response for every request, they may hang indefinitely when none is returned. Proper client-side handling is required.

---

## Question 10: Mentoring on API Evolution and Deprecation Strategies

You are mentoring a team on evolving a widely used REST API. The team needs to add a required field to a resource, but many clients are slow to update. What is the best approach to maintain backward compatibility and minimize disruption?

- A) Add the field as required immediately
- B) Add the field as optional, notify clients, and deprecate old clients gradually
- C) Remove the old resource and add a new one
- D) Require all clients to update within a week
- E) Only support the new field in the next major version

**Correct Answer:** B

**Explanation:**
Adding the field as optional and notifying clients allows for a smooth transition. Gradual deprecation minimizes disruption and maintains backward compatibility.

---

## Question 11: Debugging a Multi-Protocol Payment Gateway

You are the lead engineer for a payment gateway that exposes both REST and JSON-RPC APIs. The REST API is used by e-commerce clients for order management, while the JSON-RPC API (over HTTP/2) is used by internal microservices for transaction processing. Recently, some transactions are being processed twice, resulting in double charges. The relevant code for the JSON-RPC handler is below:

```python
@app.route('/rpc', methods=['POST'])
def rpc_handler():
    req = request.get_json()
    if req['method'] == 'processPayment':
        # idempotency check
        if db.has_processed(req['params']['orderId']):
            return {'jsonrpc': '2.0', 'result': 'already processed', 'id': req['id']}
        result = process_payment(req['params'])
        db.mark_processed(req['params']['orderId'])
        return {'jsonrpc': '2.0', 'result': result, 'id': req['id']}
    return {'jsonrpc': '2.0', 'error': {'code': -32601, 'message': 'Method not found'}, 'id': req.get('id')}
```

Logs show that, under high load, the same orderId is processed twice within milliseconds. What is the most likely cause and best fix?

- A) The idempotency check is not atomic; use a database transaction or lock
- B) The REST API is not checking for duplicate orders
- C) The JSON-RPC client is retrying requests on timeout
- D) The mark_processed call is missing; add it before process_payment
- E) Use HTTP/1.1 instead of HTTP/2

**Correct Answer:** A

**Explanation:**
The idempotency check and mark are not atomic, so two concurrent requests can both pass the check before either marks the order as processed. Use a database transaction or lock to ensure atomicity and prevent double processing.

---

## Question 12: Refactoring a REST API for Security and Maintainability

A legacy REST API for user management exposes endpoints like `/users`, `/users/{id}`, and `/users/{id}/reset-password`. The codebase uses the following pattern for authentication and authorization:

```python
def is_admin(token):
    # Decodes JWT and checks admin claim
    ...

@app.route('/users/<id>/reset-password', methods=['POST'])
def reset_password(id):
    token = request.headers.get('Authorization')
    if not is_admin(token):
        return {'error': 'Unauthorized'}, 403
    user = db.get_user(id)
    if not user:
        return {'error': 'User not found'}, 404
    user.password = generate_password()
    db.save(user)
    return {'status': 'reset'}, 200
```

A security audit finds that attackers can reset passwords for any user if they reuse a valid admin token from another session. What is the best way to refactor for security and maintainability?

- A) Rotate admin tokens more frequently
- B) Use short-lived tokens and check session validity on every request
- C) Add CSRF protection to the endpoint
- D) Require multi-factor authentication for password resets
- E) Only allow password resets from internal IPs

**Correct Answer:** B

**Explanation:**
Short-lived tokens and session validation prevent attackers from reusing stolen or replayed tokens. This is a best practice for sensitive operations like password resets.

---

## Question 13: Migrating a Monolith to Microservices with Protocol Boundaries

A monolithic application is being split into microservices. The new architecture will use REST for public APIs and JSON-RPC over HTTP/2 for internal service-to-service communication. The following code is part of the legacy monolith:

```python
def create_order(user_id, items):
    order = Order(user_id=user_id, items=items)
    db.save(order)
    send_email(user_id, 'Order created')
    update_inventory(items)
    return order
```

In the new architecture, `send_email` and `update_inventory` will be handled by separate services via JSON-RPC. What is the best way to refactor this logic for reliability and maintainability?

- A) Call both services synchronously via JSON-RPC and return when both succeed
- B) Use an event-driven approach: emit an 'order_created' event, let services subscribe
- C) Call send_email synchronously, update_inventory asynchronously
- D) Use REST for all internal calls for consistency
- E) Batch both JSON-RPC calls in a single request

**Correct Answer:** B

**Explanation:**
Event-driven architecture decouples services, improves reliability, and allows for retries and scaling. Synchronous calls can cause cascading failures and tight coupling.

---

## Question 14: Analyzing a Complex HTTP/2 Performance Issue

A SaaS analytics platform uses HTTP/2 for all REST APIs. Clients report that, during large data exports, unrelated API calls become very slow. The export endpoint streams gigabytes of data over a single HTTP/2 connection. The relevant server code is:

```python
@app.route('/export', methods=['GET'])
def export():
    def generate():
        for row in db.get_large_dataset():
            yield json.dumps(row) + '\n'
    return Response(generate(), mimetype='application/json')
```

What is the most likely cause of the slowdown, and how should you address it?

- A) HTTP/2 multiplexing is not working; switch to HTTP/1.1
- B) TCP head-of-line blocking; use separate connections for large exports
- C) The server is not compressing responses; enable gzip
- D) The client is not using persistent connections
- E) Use HTTP/2 server push for exports

**Correct Answer:** B

**Explanation:**
Large streams over a single HTTP/2 connection can block other streams due to TCP head-of-line blocking. Use a separate connection for large exports to avoid impacting other API calls.

---

## Question 15: Debugging a JSON-RPC Batch Processing Bug

A fintech company uses JSON-RPC batch requests for high-throughput trading. Occasionally, some requests in a batch are not processed, and the client receives fewer responses than requests sent. The batch request and server handler are as follows:

```json
[
  {
    "jsonrpc": "2.0",
    "method": "buy",
    "params": { "symbol": "AAPL", "qty": 10 },
    "id": 1
  },
  {
    "jsonrpc": "2.0",
    "method": "sell",
    "params": { "symbol": "GOOG", "qty": 5 },
    "id": 2
  },
  {
    "jsonrpc": "2.0",
    "method": "buy",
    "params": { "symbol": "TSLA", "qty": 2 },
    "id": 3
  }
]
```

Server handler (pseudo-code):

```python
def handle_batch(requests):
    responses = []
    for req in requests:
        try:
            result = handle_request(req)
            responses.append({'jsonrpc': '2.0', 'result': result, 'id': req['id']})
        except Exception as e:
            # log error, skip response
            continue
    return responses
```

What is the main bug, and how should it be fixed?

- A) The server should return an error response for failed requests, not skip them
- B) The client is not handling partial responses
- C) The server should process requests sequentially
- D) The batch should be split into individual requests
- E) The server should use HTTP/1.1

**Correct Answer:** A

**Explanation:**
The JSON-RPC spec requires an error response for each failed request in a batch. Skipping responses leads to missing results and client confusion. Always return an error object for failed requests.

---

## Question 16: Debugging HTTP/3 Connection Migration in Mobile Apps

You are the lead mobile engineer for a ride-sharing app that uses HTTP/3 for all API communication. The app needs to maintain connections when users switch between WiFi and cellular networks. Recently, users report that ride requests fail when switching networks, and the app shows "Connection lost" errors. The connection handling code is:

```typescript
class APIClient {
  private connection: Http3Connection;

  async makeRequest(endpoint: string, data: any): Promise<any> {
    try {
      if (!this.connection || this.connection.isClosed()) {
        this.connection = await Http3Connection.create();
      }
      return await this.connection.request(endpoint, data);
    } catch (error) {
      if (error.code === "NETWORK_CHANGE") {
        // Recreate connection on network change
        this.connection = await Http3Connection.create();
        return await this.connection.request(endpoint, data);
      }
      throw error;
    }
  }
}
```

What is the most likely cause of the connection failures?

- A) HTTP/3 doesn't support connection migration
- B) The app is not handling QUIC connection migration properly
- C) The server doesn't support HTTP/3
- D) Network switching causes TCP connection drops
- E) The retry logic is not implemented correctly

**Correct Answer:** B

**Explanation:**
HTTP/3 over QUIC supports connection migration, but the client code needs to properly handle the migration process. The current code recreates the connection instead of migrating it, causing unnecessary overhead and potential failures.

---

## Question 17: Analyzing REST API Rate Limiting Implementation

A SaaS platform implements rate limiting for its REST API. The current implementation uses Redis to track request counts per API key. During peak usage, some legitimate users are being rate limited incorrectly. The rate limiting code is:

```python
def rate_limit(api_key, endpoint):
    key = f"rate_limit:{api_key}:{endpoint}"
    current = redis.incr(key)
    if current == 1:
        redis.expire(key, 3600)  # 1 hour window

    if current > 1000:  # 1000 requests per hour
        return False, "Rate limit exceeded"
    return True, None

@app.route('/api/data', methods=['GET'])
def get_data():
    api_key = request.headers.get('X-API-Key')
    allowed, message = rate_limit(api_key, 'get_data')
    if not allowed:
        return {'error': message}, 429
    # ... rest of endpoint logic
```

What is the main issue with this rate limiting implementation?

- A) Redis expiration is not atomic with increment
- B) The rate limit window is too long
- C) Different endpoints should have different limits
- D) The implementation doesn't handle Redis failures
- E) Rate limiting should be per user, not per API key

**Correct Answer:** A

**Explanation:**
The Redis expiration is not atomic with the increment operation. This can lead to race conditions where the key expires between increment and expiration calls, causing inconsistent rate limiting behavior.

---

## Question 18: Debugging JSON-RPC Notification Reliability

A real-time chat application uses JSON-RPC notifications over WebSockets for message delivery. Users report that some messages are not delivered, especially during network interruptions. The notification sending code is:

```javascript
class ChatService {
  sendMessage(userId, message) {
    const notification = {
      jsonrpc: "2.0",
      method: "newMessage",
      params: { userId, message, timestamp: Date.now() },
    };

    // No 'id' field - this is a notification
    this.websocket.send(JSON.stringify(notification));
  }

  handleConnectionDrop() {
    // Reconnect after 5 seconds
    setTimeout(() => this.reconnect(), 5000);
  }
}
```

What is the fundamental issue with this approach for reliable message delivery?

- A) WebSockets are unreliable for message delivery
- B) JSON-RPC notifications don't guarantee delivery
- C) The reconnection delay is too long
- D) Messages should include an 'id' for tracking
- E) The service should use HTTP polling instead

**Correct Answer:** B

**Explanation:**
JSON-RPC notifications are fire-and-forget with no delivery guarantees. For reliable message delivery, use requests with IDs and implement acknowledgment mechanisms or use a message queue system.

---

## Question 19: Migrating from REST to GraphQL with Protocol Considerations

A team is migrating a REST API to GraphQL to reduce over-fetching and under-fetching. The current REST API has endpoints like `/users/{id}`, `/users/{id}/orders`, and `/users/{id}/profile`. The GraphQL schema is:

```graphql
type User {
  id: ID!
  name: String!
  email: String!
  orders: [Order!]!
  profile: Profile!
}

type Order {
  id: ID!
  amount: Float!
  status: String!
}

type Profile {
  avatar: String
  preferences: JSON
}
```

What protocol considerations should be made when exposing GraphQL alongside the existing REST API?

- A) Use HTTP/2 for GraphQL to improve multiplexing
- B) GraphQL should only use POST requests
- C) Implement proper caching headers for GraphQL responses
- D) Use WebSockets for GraphQL subscriptions
- E) All of the above

**Correct Answer:** E

**Explanation:**
GraphQL benefits from HTTP/2 multiplexing, typically uses POST for queries, requires careful caching strategy, and WebSockets for subscriptions. All these protocol considerations are important for optimal GraphQL performance.

---

## Question 20: Analyzing HTTP/2 Server Push Implementation

A content delivery platform implements HTTP/2 server push to preload critical resources. The server push implementation is:

```python
def serve_page(request):
    response = Response(html_content)

    # Push critical CSS and JS
    response.headers['Link'] = '</styles.css>; rel=preload; as=style'
    response.headers['Link'] += ', </app.js>; rel=preload; as=script'

    # Server push
    push_promise('/styles.css', 'GET')
    push_promise('/app.js', 'GET')

    return response
```

What is the main issue with this server push implementation?

- A) Server push is not supported in HTTP/2
- B) The Link headers are not needed with server push
- C) Server push should only be used for critical resources
- D) The implementation doesn't check if resources are already cached
- E) Server push should use HTTP/1.1

**Correct Answer:** D

**Explanation:**
Server push should check if resources are already in the client's cache to avoid unnecessary pushes. Pushing cached resources wastes bandwidth and can cause conflicts.

---

## Question 21: Debugging OAuth2 Token Validation in REST API

A REST API uses OAuth2 with JWT tokens for authentication. Recently, some requests are being rejected with "Invalid token" errors even though the tokens are valid. The token validation code is:

```python
def validate_token(token):
    try:
        # Decode JWT without verification first
        payload = jwt.decode(token, options={"verify_signature": False})

        # Check if token is expired
        if payload['exp'] < time.time():
            return False, "Token expired"

        # Verify signature
        jwt.decode(token, SECRET_KEY, algorithms=['HS256'])

        return True, payload
    except jwt.InvalidTokenError:
        return False, "Invalid token"

@app.route('/api/protected', methods=['GET'])
def protected_endpoint():
    token = request.headers.get('Authorization', '').replace('Bearer ', '')
    valid, result = validate_token(token)
    if not valid:
        return {'error': result}, 401
    # ... rest of endpoint logic
```

What is the security vulnerability in this token validation?

- A) The token is decoded twice unnecessarily
- B) The signature verification should happen before expiration check
- C) The code doesn't check token issuer
- D) The expiration check is not secure
- E) The token should be validated server-side only

**Correct Answer:** B

**Explanation:**
The signature should be verified before checking expiration to prevent timing attacks and ensure the token hasn't been tampered with. The current order allows potential security vulnerabilities.

---

## Question 22: Optimizing JSON-RPC Batch Processing for High Throughput

A trading platform processes thousands of JSON-RPC batch requests per second. The current batch processing implementation is:

```python
def process_batch(requests):
    results = []
    for request in requests:
        try:
            result = process_single_request(request)
            results.append({
                'jsonrpc': '2.0',
                'result': result,
                'id': request.get('id')
            })
        except Exception as e:
            results.append({
                'jsonrpc': '2.0',
                'error': {'code': -32603, 'message': str(e)},
                'id': request.get('id')
            })
    return results
```

What is the main performance bottleneck in this implementation?

- A) The sequential processing of requests
- B) The error handling overhead
- C) The JSON serialization
- D) The database connections
- E) The HTTP/2 multiplexing

**Correct Answer:** A

**Explanation:**
Sequential processing of batch requests is the main bottleneck. Parallel processing using asyncio or threading would significantly improve throughput for independent requests.

---

## Question 23: Implementing CORS for Multi-Protocol APIs

A platform exposes both REST and JSON-RPC APIs to web clients. The CORS configuration is:

```python
@app.after_request
def after_request(response):
    response.headers['Access-Control-Allow-Origin'] = '*'
    response.headers['Access-Control-Allow-Methods'] = 'GET, POST, PUT, DELETE'
    response.headers['Access-Control-Allow-Headers'] = 'Content-Type, Authorization'
    return response
```

What is the main security issue with this CORS configuration?

- A) Wildcard origin allows any domain to access the API
- B) The methods list is too permissive
- C) CORS is not needed for JSON-RPC
- D) The headers list is incomplete
- E) CORS should be disabled for internal APIs

**Correct Answer:** A

**Explanation:**
Using '\*' for Access-Control-Allow-Origin allows any domain to access the API, which is a security risk. Should specify allowed origins explicitly or use dynamic origin validation.

---

## Question 24: Debugging HTTP/2 Flow Control Issues

A video streaming service uses HTTP/2 for adaptive bitrate streaming. During peak usage, some video segments fail to load, and clients report buffering issues. The streaming implementation is:

```python
@app.route('/video/<segment_id>', methods=['GET'])
def stream_video(segment_id):
    video_data = get_video_segment(segment_id)

    response = Response(video_data)
    response.headers['Content-Type'] = 'video/mp4'
    response.headers['Content-Length'] = len(video_data)

    return response
```

What is the most likely cause of the streaming issues?

- A) HTTP/2 doesn't support video streaming
- B) The flow control window is too small for video segments
- C) The server is not using HPACK compression
- D) The video segments are too large
- E) The client is not supporting HTTP/2

**Correct Answer:** B

**Explanation:**
Large video segments can exhaust the HTTP/2 flow control window, causing streams to stall. The server needs to properly manage flow control for large responses.

---

## Question 25: Analyzing REST API Versioning Strategy

A company maintains a public REST API with multiple versions. The current versioning strategy uses URL versioning:

```
/api/v1/users
/api/v2/users
/api/v3/users
```

The team wants to deprecate v1 and v2 while maintaining backward compatibility. What is the best approach for this migration?

- A) Immediately remove v1 and v2 endpoints
- B) Use HTTP 301 redirects to point old versions to v3
- C) Implement content negotiation with custom media types
- D) Keep all versions running indefinitely
- E) Use query parameters for versioning

**Correct Answer:** C

**Explanation:**
Content negotiation with custom media types (e.g., `application/vnd.company.users-v3+json`) is more RESTful and flexible than URL versioning. It allows for smoother transitions and better API evolution.

---

## Question 26: Debugging WebSocket Connection Pooling

A real-time dashboard application uses WebSockets for live data updates. The application opens multiple WebSocket connections to different services. During high load, some connections are dropped and not re-established. The connection management code is:

```javascript
class WebSocketManager {
  constructor() {
    this.connections = new Map();
    this.maxConnections = 10;
  }

  connect(serviceUrl) {
    if (this.connections.size >= this.maxConnections) {
      // Close oldest connection
      const oldest = this.connections.keys().next().value;
      this.connections.get(oldest).close();
      this.connections.delete(oldest);
    }

    const ws = new WebSocket(serviceUrl);
    ws.onclose = () => this.connections.delete(serviceUrl);
    this.connections.set(serviceUrl, ws);
    return ws;
  }
}
```

What is the main issue with this connection pooling strategy?

- A) The connection limit is too low
- B) No automatic reconnection logic
- C) WebSockets don't support connection pooling
- D) The oldest connection selection is inefficient
- E) The manager doesn't handle connection failures

**Correct Answer:** B

**Explanation:**
The manager doesn't automatically reconnect when connections are dropped. Should implement exponential backoff and automatic reconnection logic for reliable WebSocket connections.

---

## Question 27: Implementing Idempotency in REST APIs

A payment processing API needs to implement idempotency for POST requests. The current implementation is:

```python
@app.route('/payments', methods=['POST'])
def create_payment():
    idempotency_key = request.headers.get('Idempotency-Key')

    if idempotency_key:
        # Check if payment already exists
        existing = db.get_payment_by_key(idempotency_key)
        if existing:
            return existing, 200

    # Create new payment
    payment = create_payment_from_request(request)
    db.save_payment(payment, idempotency_key)
    return payment, 201
```

What is the main issue with this idempotency implementation?

- A) The idempotency check is not atomic
- B) The key should be in the request body
- C) The implementation doesn't handle concurrent requests
- D) The response status code is incorrect
- E) Idempotency is not needed for POST requests

**Correct Answer:** A

**Explanation:**
The idempotency check and save operations are not atomic, which can lead to race conditions and duplicate payments. Should use database transactions or distributed locks.

---

## Question 28: Analyzing HTTP/3 Performance in Mobile Networks

A mobile app developer is testing HTTP/3 performance on various mobile networks. The app makes API calls to a server that supports HTTP/3. During testing, the developer notices that HTTP/3 performs worse than HTTP/2 on some networks. What is the most likely cause?

- A) HTTP/3 is not supported on mobile devices
- B) QUIC is blocked by corporate firewalls
- C) The server's QUIC implementation is suboptimal
- D) Mobile networks have better TCP optimization than UDP
- E) The app is not using HTTP/3 correctly

**Correct Answer:** D

**Explanation:**
Some mobile networks have better TCP optimization and may block or throttle UDP traffic, causing HTTP/3 to perform worse than HTTP/2. This is why fallback mechanisms are important.

---

## Question 29: Debugging JSON-RPC Method Introspection

A developer is implementing JSON-RPC method introspection for API documentation. The introspection implementation is:

```python
def get_method_info(method_name):
    methods = {
        'add': {'params': ['number', 'number'], 'returns': 'number'},
        'subtract': {'params': ['number', 'number'], 'returns': 'number'},
        'multiply': {'params': ['number', 'number'], 'returns': 'number'}
    }
    return methods.get(method_name)

@app.route('/rpc', methods=['POST'])
def rpc_handler():
    request_data = request.get_json()

    if request_data['method'] == 'rpc.discover':
        return {
            'jsonrpc': '2.0',
            'result': {
                'methods': list(get_method_info.keys()),
                'version': '1.0'
            },
            'id': request_data.get('id')
        }

    # Handle other methods...
```

What is the main limitation of this introspection implementation?

- A) It doesn't follow JSON-RPC 2.0 specification
- B) The method information is hardcoded
- C) It doesn't support parameter validation
- D) The discovery method is not standard
- E) It doesn't include error codes

**Correct Answer:** B

**Explanation:**
Hardcoding method information makes the API brittle and difficult to maintain. Should use reflection or dynamic method registration to automatically generate introspection data.

---

## Question 30: Implementing Circuit Breaker for REST APIs

A microservice architecture uses REST APIs for inter-service communication. The team wants to implement circuit breakers to prevent cascading failures. The circuit breaker implementation is:

```python
class CircuitBreaker:
    def __init__(self, failure_threshold=5, timeout=60):
        self.failure_threshold = failure_threshold
        self.timeout = timeout
        self.failure_count = 0
        self.last_failure_time = None
        self.state = 'CLOSED'  # CLOSED, OPEN, HALF_OPEN

    def call(self, func, *args, **kwargs):
        if self.state == 'OPEN':
            if time.time() - self.last_failure_time > self.timeout:
                self.state = 'HALF_OPEN'
            else:
                raise Exception('Circuit breaker is OPEN')

        try:
            result = func(*args, **kwargs)
            if self.state == 'HALF_OPEN':
                self.state = 'CLOSED'
                self.failure_count = 0
            return result
        except Exception as e:
            self.failure_count += 1
            self.last_failure_time = time.time()
            if self.failure_count >= self.failure_threshold:
                self.state = 'OPEN'
            raise e
```

What is the main issue with this circuit breaker implementation?

- A) It doesn't handle partial failures
- B) The timeout is too long
- C) It doesn't distinguish between different types of failures
- D) The state transitions are not thread-safe
- E) It doesn't support HTTP status codes

**Correct Answer:** D

**Explanation:**
The circuit breaker state transitions are not thread-safe, which can lead to race conditions in concurrent environments. Should use locks or atomic operations for state management.

---

## Question 31: Analyzing HTTP/2 Server Push Caching

A web application uses HTTP/2 server push to preload critical resources. The server push implementation includes caching headers:

```python
def push_resource(path, content_type):
    response = Response()
    response.headers['Content-Type'] = content_type
    response.headers['Cache-Control'] = 'public, max-age=3600'
    response.headers['ETag'] = generate_etag(content)

    # Server push
    push_promise(path, 'GET', response.headers)
    return response
```

What is the main issue with this server push caching implementation?

- A) Server push doesn't support caching
- B) The cache headers are not respected by clients
- C) The ETag is not used for validation
- D) The max-age is too short
- E) Server push bypasses client cache validation

**Correct Answer:** E

**Explanation:**
Server push can bypass client cache validation, potentially pushing resources that are already cached. Should check if resources are in the client's cache before pushing.

---

## Question 32: Debugging OAuth2 Token Refresh in REST APIs

A REST API client implements OAuth2 token refresh logic. The refresh implementation is:

```python
class OAuth2Client:
    def __init__(self, client_id, client_secret):
        self.client_id = client_id
        self.client_secret = client_secret
        self.access_token = None
        self.refresh_token = None

    def refresh_access_token(self):
        response = requests.post('/oauth/token', data={
            'grant_type': 'refresh_token',
            'refresh_token': self.refresh_token,
            'client_id': self.client_id,
            'client_secret': self.client_secret
        })

        if response.status_code == 200:
            data = response.json()
            self.access_token = data['access_token']
            self.refresh_token = data.get('refresh_token', self.refresh_token)
        else:
            raise Exception('Token refresh failed')

    def make_request(self, url, method='GET'):
        if not self.access_token:
            self.refresh_access_token()

        headers = {'Authorization': f'Bearer {self.access_token}'}
        response = requests.request(method, url, headers=headers)

        if response.status_code == 401:
            self.refresh_access_token()
            headers = {'Authorization': f'Bearer {self.access_token}'}
            response = requests.request(method, url, headers=headers)

        return response
```

What is the main issue with this token refresh implementation?

- A) It doesn't handle concurrent refresh requests
- B) The refresh token is not rotated
- C) It doesn't handle refresh token expiration
- D) The retry logic is not exponential backoff
- E) It doesn't validate the new access token

**Correct Answer:** A

**Explanation:**
Multiple concurrent requests can trigger multiple token refresh attempts, leading to race conditions and potential token conflicts. Should implement proper synchronization for token refresh.

---

## Question 33: Implementing Rate Limiting for JSON-RPC APIs

A JSON-RPC API needs to implement rate limiting per client. The rate limiting implementation is:

```python
def rate_limit_jsonrpc(request_data):
    client_id = extract_client_id(request_data)
    method = request_data.get('method')

    # Different limits for different methods
    limits = {
        'getData': 100,  # 100 requests per minute
        'updateData': 10,  # 10 requests per minute
        'deleteData': 5   # 5 requests per minute
    }

    limit = limits.get(method, 50)
    key = f"rate_limit:{client_id}:{method}"

    current = redis.incr(key)
    if current == 1:
        redis.expire(key, 60)  # 1 minute window

    if current > limit:
        return False, "Rate limit exceeded"

    return True, None

@app.route('/rpc', methods=['POST'])
def jsonrpc_handler():
    request_data = request.get_json()

    # Check rate limit
    allowed, message = rate_limit_jsonrpc(request_data)
    if not allowed:
        return {
            'jsonrpc': '2.0',
            'error': {'code': -32029, 'message': message},
            'id': request_data.get('id')
        }

    # Process request...
```

What is the main issue with this rate limiting implementation?

- A) It doesn't handle batch requests correctly
- B) The limits are too restrictive
- C) It doesn't support burst requests
- D) The Redis key expiration is not atomic
- E) It doesn't distinguish between different clients

**Correct Answer:** A

**Explanation:**
The rate limiting doesn't properly handle JSON-RPC batch requests. Each request in a batch should be counted individually, not as a single request.

---

## Question 34: Debugging HTTP/2 Priority and Dependencies

A web application uses HTTP/2 priority streams to optimize resource loading. The priority implementation is:

```javascript
// Load critical CSS first
fetch("/styles.css", {
  priority: "high",
  headers: {
    "X-Priority": "1",
  },
});

// Load JavaScript after CSS
fetch("/app.js", {
  priority: "medium",
  headers: {
    "X-Priority": "2",
  },
});

// Load images last
fetch("/logo.png", {
  priority: "low",
  headers: {
    "X-Priority": "3",
  },
});
```

What is the main issue with this HTTP/2 priority implementation?

- A) HTTP/2 doesn't support priority headers
- B) The priority values are not standardized
- C) The browser doesn't respect custom priority headers
- D) Priority should be set on the server side
- E) The implementation doesn't use HTTP/2 streams

**Correct Answer:** C

**Explanation:**
Custom priority headers are not part of the HTTP/2 specification and browsers don't respect them. HTTP/2 priority is handled through the stream dependency tree, not headers.

---

## Question 35: Analyzing REST API Pagination Implementation

A REST API implements pagination for large datasets. The pagination implementation is:

```python
@app.route('/users', methods=['GET'])
def get_users():
    page = int(request.args.get('page', 1))
    per_page = int(request.args.get('per_page', 10))

    offset = (page - 1) * per_page
    users = db.query('SELECT * FROM users LIMIT %s OFFSET %s',
                    per_page, offset)

    total = db.query('SELECT COUNT(*) FROM users')[0][0]
    total_pages = (total + per_page - 1) // per_page

    return {
        'data': users,
        'pagination': {
            'page': page,
            'per_page': per_page,
            'total': total,
            'total_pages': total_pages
        }
    }
```

What is the main performance issue with this pagination implementation?

- A) The COUNT query is expensive for large datasets
- B) The OFFSET is inefficient for deep pagination
- C) The page size is too small
- D) The implementation doesn't use cursors
- E) The database queries are not optimized

**Correct Answer:** B

**Explanation:**
Using OFFSET for deep pagination is inefficient because the database must skip many rows. Cursor-based pagination using keyset pagination is more efficient for large datasets.

---

## Question 36: Implementing WebSocket Heartbeat for Connection Health

A real-time application uses WebSockets for live updates. The application needs to detect connection health and reconnect when necessary. The heartbeat implementation is:

```javascript
class WebSocketManager {
  constructor(url) {
    this.url = url;
    this.ws = null;
    this.heartbeatInterval = null;
    this.reconnectAttempts = 0;
    this.maxReconnectAttempts = 5;
  }

  connect() {
    this.ws = new WebSocket(this.url);
    this.ws.onopen = () => {
      this.startHeartbeat();
      this.reconnectAttempts = 0;
    };

    this.ws.onclose = () => {
      this.stopHeartbeat();
      this.reconnect();
    };
  }

  startHeartbeat() {
    this.heartbeatInterval = setInterval(() => {
      if (this.ws.readyState === WebSocket.OPEN) {
        this.ws.send(JSON.stringify({ type: "ping" }));
      }
    }, 30000); // 30 seconds
  }

  stopHeartbeat() {
    if (this.heartbeatInterval) {
      clearInterval(this.heartbeatInterval);
      this.heartbeatInterval = null;
    }
  }

  reconnect() {
    if (this.reconnectAttempts < this.maxReconnectAttempts) {
      this.reconnectAttempts++;
      setTimeout(() => this.connect(), 1000 * this.reconnectAttempts);
    }
  }
}
```

What is the main issue with this heartbeat implementation?

- A) The heartbeat interval is too long
- B) It doesn't handle heartbeat timeouts
- C) The reconnection delay is too short
- D) It doesn't validate heartbeat responses
- E) The implementation doesn't use exponential backoff

**Correct Answer:** B

**Explanation:**
The implementation sends pings but doesn't wait for pong responses or handle timeouts. Should implement a timeout mechanism to detect when the connection is actually dead.

---

## Question 37: Debugging HTTP/3 0-RTT Security Implementation

A web application implements HTTP/3 0-RTT for faster initial page loads. The 0-RTT implementation is:

```python
def handle_0rtt_request(request):
    # Check if request is safe for 0-RTT
    safe_methods = ['GET', 'HEAD', 'OPTIONS']
    if request.method not in safe_methods:
        return {'error': 'Method not safe for 0-RTT'}, 400

    # Process the request
    result = process_request(request)
    return result

@app.route('/api/data', methods=['GET'])
def get_data():
    if request.headers.get('X-0RTT'):
        return handle_0rtt_request(request)
    # Normal request processing...
```

What is the main security consideration for this 0-RTT implementation?

- A) 0-RTT requests can be replayed by attackers
- B) The implementation doesn't validate the request
- C) 0-RTT is not supported in HTTP/3
- D) The safe methods list is incomplete
- E) 0-RTT should only be used for static content

**Correct Answer:** A

**Explanation:**
0-RTT requests can be captured and replayed by attackers, so only idempotent operations should use 0-RTT. The current implementation correctly restricts to safe methods.

---

## Question 38: Implementing API Gateway with Protocol Translation

An API gateway needs to translate between REST and JSON-RPC protocols. The translation implementation is:

```python
class ProtocolTranslator:
    def rest_to_jsonrpc(self, rest_request):
        # Convert REST request to JSON-RPC
        method = self.map_rest_method(rest_request.method, rest_request.path)
        params = self.extract_params(rest_request)

        return {
            'jsonrpc': '2.0',
            'method': method,
            'params': params,
            'id': generate_request_id()
        }

    def jsonrpc_to_rest(self, jsonrpc_response):
        # Convert JSON-RPC response to REST
        if 'error' in jsonrpc_response:
            return self.create_error_response(jsonrpc_response['error'])

        return self.create_success_response(jsonrpc_response['result'])

    def map_rest_method(self, method, path):
        # Map REST endpoints to JSON-RPC methods
        mappings = {
            ('GET', '/users'): 'getUsers',
            ('POST', '/users'): 'createUser',
            ('PUT', '/users/{id}'): 'updateUser',
            ('DELETE', '/users/{id}'): 'deleteUser'
        }
        return mappings.get((method, path), 'unknown')
```

What is the main limitation of this protocol translation?

- A) It doesn't handle batch requests
- B) The method mapping is hardcoded
- C) It doesn't preserve HTTP status codes
- D) The translation is not bidirectional
- E) It doesn't handle authentication

**Correct Answer:** B

**Explanation:**
Hardcoded method mappings make the translation brittle and difficult to maintain. Should use dynamic mapping based on API specifications or configuration.

---

## Question 39: Analyzing REST API Caching Strategy

A REST API implements caching for frequently accessed resources. The caching implementation is:

```python
@app.route('/products/<id>', methods=['GET'])
def get_product(id):
    # Check cache first
    cache_key = f"product:{id}"
    cached = redis.get(cache_key)

    if cached:
        return json.loads(cached), 200, {
            'X-Cache': 'HIT',
            'Cache-Control': 'public, max-age=3600'
        }

    # Fetch from database
    product = db.get_product(id)
    if not product:
        return {'error': 'Product not found'}, 404

    # Cache the result
    redis.setex(cache_key, 3600, json.dumps(product))

    return product, 200, {
        'X-Cache': 'MISS',
        'Cache-Control': 'public, max-age=3600'
    }
```

What is the main issue with this caching implementation?

- A) It doesn't handle cache invalidation
- B) The cache duration is too long
- C) It doesn't use ETags for validation
- D) The cache key is not secure
- E) It doesn't handle cache failures

**Correct Answer:** A

**Explanation:**
The implementation doesn't handle cache invalidation when products are updated. Should implement cache invalidation strategies or use cache validation with ETags.

---

## Question 40: Debugging JSON-RPC Error Handling in Distributed Systems

A distributed system uses JSON-RPC for inter-service communication. The error handling implementation is:

```python
def handle_jsonrpc_request(request_data):
    try:
        method = request_data.get('method')
        params = request_data.get('params', {})

        # Route to appropriate handler
        handler = get_handler(method)
        if not handler:
            return {
                'jsonrpc': '2.0',
                'error': {'code': -32601, 'message': 'Method not found'},
                'id': request_data.get('id')
            }

        result = handler(params)
        return {
            'jsonrpc': '2.0',
            'result': result,
            'id': request_data.get('id')
        }

    except ValidationError as e:
        return {
            'jsonrpc': '2.0',
            'error': {'code': -32602, 'message': str(e)},
            'id': request_data.get('id')
        }
    except DatabaseError as e:
        return {
            'jsonrpc': '2.0',
            'error': {'code': -32603, 'message': 'Internal error'},
            'id': request_data.get('id')
        }
    except Exception as e:
        # Log the actual error for debugging
        logger.error(f"Unexpected error: {e}")
        return {
            'jsonrpc': '2.0',
            'error': {'code': -32603, 'message': 'Internal error'},
            'id': request_data.get('id')
        }
```

What is the main issue with this error handling implementation?

- A) It doesn't handle timeouts
- B) The error codes are not standardized
- C) It doesn't distinguish between different error types
- D) The error messages are too generic
- E) It doesn't handle network failures

**Correct Answer:** D

**Explanation:**
Generic error messages like "Internal error" don't provide enough information for debugging while potentially leaking sensitive information. Should provide more specific error messages for different scenarios.

---
