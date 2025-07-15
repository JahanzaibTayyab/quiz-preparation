# 🌐 JSON-RPC 2.0 Basics - Beginner Quiz

Welcome to the JSON-RPC 2.0 Basics Quiz! This quiz will test your understanding of fundamental JSON-RPC concepts including the protocol structure, request/response objects, error handling, and basic remote procedure call principles.

**Instructions:**

- Each question has 4 multiple choice options
- Only one answer is correct
- Read the explanation after answering to understand the concept better
- This quiz covers beginner-level JSON-RPC concepts

---

## Question 1

```json
{
  "question": "What does JSON-RPC stand for?",
  "options": [
    "JavaScript Object Notation Remote Procedure Call",
    "JSON Remote Protocol Communication",
    "JavaScript Remote Procedure Call",
    "JSON Remote Process Communication"
  ],
  "correctAnswer": "JavaScript Object Notation Remote Procedure Call",
  "explanation": "JSON-RPC stands for JavaScript Object Notation Remote Procedure Call. It's a lightweight, stateless protocol that uses JSON as its data format to enable remote procedure calls between clients and servers."
}
```

## Question 2

```json
{
  "question": "What version of JSON-RPC is currently the standard?",
  "options": ["1.0", "2.0", "3.0", "1.5"],
  "correctAnswer": "2.0",
  "explanation": "JSON-RPC 2.0 is the current standard version. It was designed to be simple, lightweight, and transport-agnostic, making it suitable for various communication protocols like HTTP, WebSockets, and TCP."
}
```

## Question 3

```json
{
  "question": "What is the purpose of the 'jsonrpc' field in a JSON-RPC request?",
  "options": [
    "To specify the JSON format",
    "To specify the protocol version",
    "To identify the request type",
    "To specify the transport method"
  ],
  "correctAnswer": "To specify the protocol version",
  "explanation": "The 'jsonrpc' field specifies the version of the JSON-RPC protocol being used. For JSON-RPC 2.0, this field MUST be exactly '2.0' to indicate compliance with the 2.0 specification."
}
```

## Question 4

```json
{
  "question": "Which field in a JSON-RPC request contains the name of the method to be invoked?",
  "options": ["function", "method", "call", "procedure"],
  "correctAnswer": "method",
  "explanation": "The 'method' field contains the name of the method to be invoked on the server. This is a string that identifies which remote procedure the client wants to execute."
}
```

## Question 5

```json
{
  "question": "What is the purpose of the 'params' field in a JSON-RPC request?",
  "options": [
    "To specify the protocol parameters",
    "To hold the parameters for the method being called",
    "To specify the response format",
    "To identify the request type"
  ],
  "correctAnswer": "To hold the parameters for the method being called",
  "explanation": "The 'params' field holds the parameters that will be passed to the method being called. It can be either an array (for positional parameters) or an object (for named parameters), and can be omitted if the method doesn't require parameters."
}
```

## Question 6

```json
{
  "question": "What is the purpose of the 'id' field in a JSON-RPC request?",
  "options": [
    "To identify the server",
    "To identify the client",
    "To correlate requests with responses",
    "To specify the request type"
  ],
  "correctAnswer": "To correlate requests with responses",
  "explanation": "The 'id' field is used to correlate requests with their corresponding responses. It can be a string, number, or null. If omitted, the request becomes a notification (one-way communication)."
}
```

## Question 7

```json
{
  "question": "What is a JSON-RPC notification?",
  "options": [
    "A server-to-client message",
    "A request without an 'id' field",
    "An error message",
    "A response message"
  ],
  "correctAnswer": "A request without an 'id' field",
  "explanation": "A JSON-RPC notification is a request object that does not include the 'id' field. When a client sends a notification, it's not interested in a response from the server, and the server MUST NOT reply to it."
}
```

## Question 8

```json
{
  "question": "What are the two ways to structure parameters in JSON-RPC?",
  "options": [
    "By position and by name",
    "By type and by value",
    "By order and by key",
    "By index and by property"
  ],
  "correctAnswer": "By position and by name",
  "explanation": "JSON-RPC supports two parameter structures: by-position (using an array where each value corresponds to a parameter in order) and by-name (using an object where each key-value pair represents a named parameter)."
}
```

## Question 9

```json
{
  "question": "What is the correct format for a JSON-RPC request with positional parameters?",
  "options": [
    "{\"jsonrpc\": \"2.0\", \"method\": \"add\", \"params\": [1, 2], \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"method\": \"add\", \"params\": {\"a\": 1, \"b\": 2}, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"method\": \"add\", \"args\": [1, 2], \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"function\": \"add\", \"params\": [1, 2], \"id\": 1}"
  ],
  "correctAnswer": "{\"jsonrpc\": \"2.0\", \"method\": \"add\", \"params\": [1, 2], \"id\": 1}",
  "explanation": "This is the correct format for a JSON-RPC request with positional parameters. The 'params' field is an array containing the values [1, 2] that will be passed to the 'add' method in order."
}
```

## Question 10

```json
{
  "question": "What is the correct format for a JSON-RPC request with named parameters?",
  "options": [
    "{\"jsonrpc\": \"2.0\", \"method\": \"subtract\", \"params\": [42, 23], \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"method\": \"subtract\", \"params\": {\"minuend\": 42, \"subtrahend\": 23}, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"method\": \"subtract\", \"args\": {\"minuend\": 42, \"subtrahend\": 23}, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"function\": \"subtract\", \"params\": {\"minuend\": 42, \"subtrahend\": 23}, \"id\": 1}"
  ],
  "correctAnswer": "{\"jsonrpc\": \"2.0\", \"method\": \"subtract\", \"params\": {\"minuend\": 42, \"subtrahend\": 23}, \"id\": 1}",
  "explanation": "This is the correct format for a JSON-RPC request with named parameters. The 'params' field is an object where each key-value pair represents a named parameter that will be passed to the 'subtract' method."
}
```

## Question 11

```json
{
  "question": "What is the purpose of the 'result' field in a JSON-RPC response?",
  "options": [
    "To indicate success",
    "To hold the return value from the method",
    "To specify the response type",
    "To identify the response"
  ],
  "correctAnswer": "To hold the return value from the method",
  "explanation": "The 'result' field in a JSON-RPC response holds the return value from the method that was invoked. It's required on success and contains the actual data returned by the remote procedure."
}
```

## Question 12

```json
{
  "question": "What is the purpose of the 'error' field in a JSON-RPC response?",
  "options": [
    "To indicate failure",
    "To hold error information when something goes wrong",
    "To specify the error type",
    "To identify the error"
  ],
  "correctAnswer": "To hold error information when something goes wrong",
  "explanation": "The 'error' field in a JSON-RPC response holds error information when something goes wrong during the RPC call. It contains an Error object with details about what went wrong."
}
```

## Question 13

```json
{
  "question": "Can a JSON-RPC response contain both 'result' and 'error' fields?",
  "options": [
    "Yes, always",
    "No, never",
    "Only in batch requests",
    "Only for notifications"
  ],
  "correctAnswer": "No, never",
  "explanation": "A JSON-RPC response object MUST contain either the 'result' or the 'error' member, but not both. This ensures clear distinction between successful and failed operations."
}
```

## Question 14

```json
{
  "question": "What is the correct format for a successful JSON-RPC response?",
  "options": [
    "{\"jsonrpc\": \"2.0\", \"result\": 19, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"success\": true, \"result\": 19, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"status\": \"success\", \"result\": 19, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"data\": 19, \"id\": 1}"
  ],
  "correctAnswer": "{\"jsonrpc\": \"2.0\", \"result\": 19, \"id\": 1}",
  "explanation": "This is the correct format for a successful JSON-RPC response. It includes the protocol version, the result value, and the same id that was in the original request for correlation."
}
```

## Question 15

```json
{
  "question": "What is the correct format for a JSON-RPC error response?",
  "options": [
    "{\"jsonrpc\": \"2.0\", \"error\": \"Method not found\", \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"error\": {\"code\": -32601, \"message\": \"Method not found\"}, \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"error\": -32601, \"message\": \"Method not found\", \"id\": 1}",
    "{\"jsonrpc\": \"2.0\", \"status\": \"error\", \"error\": \"Method not found\", \"id\": 1}"
  ],
  "correctAnswer": "{\"jsonrpc\": \"2.0\", \"error\": {\"code\": -32601, \"message\": \"Method not found\"}, \"id\": 1}",
  "explanation": "This is the correct format for a JSON-RPC error response. The 'error' field contains an object with a 'code' (numeric error code) and 'message' (human-readable error description)."
}
```

## Question 16

```json
{
  "question": "What does error code -32700 mean in JSON-RPC?",
  "options": [
    "Invalid Request",
    "Parse error",
    "Method not found",
    "Internal error"
  ],
  "correctAnswer": "Parse error",
  "explanation": "Error code -32700 means 'Parse error' - invalid JSON was received by the server. This occurs when the server cannot parse the JSON in the request."
}
```

## Question 17

```json
{
  "question": "What does error code -32600 mean in JSON-RPC?",
  "options": [
    "Parse error",
    "Invalid Request",
    "Method not found",
    "Invalid params"
  ],
  "correctAnswer": "Invalid Request",
  "explanation": "Error code -32600 means 'Invalid Request' - the JSON sent is not a valid Request object. This occurs when the request structure is malformed or missing required fields."
}
```

## Question 18

```json
{
  "question": "What does error code -32601 mean in JSON-RPC?",
  "options": [
    "Invalid Request",
    "Method not found",
    "Invalid params",
    "Internal error"
  ],
  "correctAnswer": "Method not found",
  "explanation": "Error code -32601 means 'Method not found' - the method does not exist or is not available on the server. This occurs when the client tries to call a method that the server doesn't implement."
}
```

## Question 19

```json
{
  "question": "What does error code -32602 mean in JSON-RPC?",
  "options": [
    "Method not found",
    "Invalid params",
    "Internal error",
    "Server error"
  ],
  "correctAnswer": "Invalid params",
  "explanation": "Error code -32602 means 'Invalid params' - invalid method parameter(s). This occurs when the parameters provided don't match what the method expects."
}
```

## Question 20

```json
{
  "question": "What does error code -32603 mean in JSON-RPC?",
  "options": [
    "Invalid params",
    "Internal error",
    "Server error",
    "Parse error"
  ],
  "correctAnswer": "Internal error",
  "explanation": "Error code -32603 means 'Internal error' - internal JSON-RPC error. This occurs when there's an internal error in the JSON-RPC implementation itself."
}
```

## Question 21

```json
{
  "question": "What is the range for server error codes in JSON-RPC?",
  "options": [
    "-32000 to -32099",
    "-32700 to -32799",
    "-32600 to -32699",
    "-32500 to -32599"
  ],
  "correctAnswer": "-32000 to -32099",
  "explanation": "Server error codes range from -32000 to -32099. These codes are reserved for implementation-defined server errors and can be used by servers to indicate specific error conditions."
}
```

## Question 22

```json
{
  "question": "What is a batch request in JSON-RPC?",
  "options": [
    "Multiple requests sent simultaneously",
    "An array of Request objects sent together",
    "A single request with multiple methods",
    "Multiple responses sent together"
  ],
  "correctAnswer": "An array of Request objects sent together",
  "explanation": "A batch request in JSON-RPC is an array of Request objects sent together. The server processes all requests and responds with an array of corresponding Response objects."
}
```

## Question 23

```json
{
  "question": "How does the server process batch requests in JSON-RPC?",
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

## Question 24

```json
{
  "question": "What is the correct format for a JSON-RPC notification?",
  "options": [
    "{\"jsonrpc\": \"2.0\", \"method\": \"update\", \"params\": [1, 2, 3, 4, 5]}",
    "{\"jsonrpc\": \"2.0\", \"method\": \"update\", \"params\": [1, 2, 3, 4, 5], \"id\": null}",
    "{\"jsonrpc\": \"2.0\", \"notification\": \"update\", \"params\": [1, 2, 3, 4, 5]}",
    "{\"jsonrpc\": \"2.0\", \"method\": \"update\", \"params\": [1, 2, 3, 4, 5], \"id\": 0}"
  ],
  "correctAnswer": "{\"jsonrpc\": \"2.0\", \"method\": \"update\", \"params\": [1, 2, 3, 4, 5]}",
  "explanation": "This is the correct format for a JSON-RPC notification. It omits the 'id' field entirely, indicating that no response is expected from the server."
}
```

## Question 25

```json
{
  "question": "What happens when a server receives a JSON-RPC notification?",
  "options": [
    "It must send an acknowledgment response",
    "It must not reply",
    "It can optionally send a response",
    "It must send an error response"
  ],
  "correctAnswer": "It must not reply",
  "explanation": "When a server receives a JSON-RPC notification (a request without an 'id' field), it MUST NOT reply. This is because notifications are designed for one-way communication where the client doesn't expect a response."
}
```

## Question 26

```json
{
  "question": "What is the purpose of the 'data' field in a JSON-RPC Error object?",
  "options": [
    "To specify the error type",
    "To provide additional information about the error",
    "To identify the error",
    "To specify the error code"
  ],
  "correctAnswer": "To provide additional information about the error",
  "explanation": "The 'data' field in a JSON-RPC Error object is optional and provides additional information about the error. It can contain a primitive or structured value with extra details that might be helpful for debugging."
}
```

## Question 27

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

## Question 28

```json
{
  "question": "Is JSON-RPC transport-agnostic?",
  "options": [
    "No, it only works over HTTP",
    "Yes, it can work over any transport",
    "No, it only works over WebSockets",
    "Yes, but only over TCP-based protocols"
  ],
  "correctAnswer": "Yes, it can work over any transport",
  "explanation": "JSON-RPC is transport-agnostic, meaning it can be used over HTTP, WebSockets, TCP, or any other message-passing environment. The protocol itself doesn't depend on any specific transport mechanism."
}
```

## Question 29

```json
{
  "question": "What is the main advantage of JSON-RPC over other RPC protocols?",
  "options": [
    "It's faster than other protocols",
    "It's simpler and easier to use",
    "It supports more data types",
    "It's more secure than other protocols"
  ],
  "correctAnswer": "It's simpler and easier to use",
  "explanation": "The main advantage of JSON-RPC is its simplicity and ease of use. It uses JSON as its data format, which is widely supported, human-readable, and easy to work with across different programming languages and platforms."
}
```

## Question 30

```json
{
  "question": "What is the relationship between JSON-RPC and HTTP?",
  "options": [
    "JSON-RPC is built on top of HTTP",
    "HTTP is built on top of JSON-RPC",
    "JSON-RPC can use HTTP as a transport",
    "They are completely independent protocols"
  ],
  "correctAnswer": "JSON-RPC can use HTTP as a transport",
  "explanation": "JSON-RPC can use HTTP as a transport mechanism, but it's not limited to HTTP. JSON-RPC is transport-agnostic and can work over any message-passing environment, with HTTP being one of the most common choices."
}
```

---

## 📊 **Quiz Summary**

**Total Questions:** 30  
**Difficulty Level:** Beginner  
**Topics Covered:**

- JSON-RPC protocol fundamentals and structure
- Request and response object formats
- Parameter passing (positional vs named)
- Notifications and batch requests
- Error handling and error codes
- Protocol versioning and transport independence
- Basic remote procedure call concepts

**Scoring Guide:**

- 25-30 correct: Excellent understanding of JSON-RPC basics
- 20-24 correct: Good understanding with some areas for improvement
- 15-19 correct: Basic understanding, review recommended
- Below 15: Fundamental review needed

**Key JSON-RPC Concepts Tested:**

- **Protocol Structure**: Understanding request/response object formats
- **Parameter Passing**: Positional vs named parameter structures
- **Error Handling**: Standard error codes and error object structure
- **Notifications**: One-way communication without responses
- **Batch Requests**: Multiple requests in a single call
- **Transport Independence**: Protocol agnostic nature
- **Versioning**: Protocol version specification

**Next Steps:**
After completing this quiz, consider exploring:

- JSON-RPC over HTTP implementation
- Advanced error handling and custom error codes
- JSON-RPC with WebSockets for real-time communication
- JSON-RPC vs REST API comparison
- JSON-RPC in microservices architecture
- JSON-RPC client and server implementations
- Performance optimization techniques

---

_This quiz is based on the JSON-RPC 2.0 specification content from the MCP learning repository. For more detailed explanations, refer to the original documentation._
