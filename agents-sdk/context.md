# Context Management Quiz

Below are 20 professional-level questions on context management in the OpenAI Agents SDK, covering concepts, implementation, and best practices.

---

## Questions

### Question 1

```json
{
    "question": "A developer wants to pass user-specific data and dependencies to all tool functions and lifecycle hooks during an agent run. Which mechanism should they use?",
    "options": [
        "Agent instructions",
        "Local context via RunContextWrapper",
        "Conversation history",
        "LLM input context"
    ],
    "correctAnswer": "Local context via RunContextWrapper",
    "explanation": "Local context is managed via RunContextWrapper, as described in the 'Local context' section. Agent instructions and conversation history are for LLM context only."
}
```

---

### Question 2

```json
{
    "question": "Which of the following is TRUE about the context object passed to tool functions?",
    "options": [
        "It is always visible to the LLM.",
        "It must be a dictionary.",
        "It is not sent to the LLM and is purely local.",
        "It is automatically serialized to JSON."
    ],
    "correctAnswer": "It is not sent to the LLM and is purely local.",
    "explanation": "Docs: 'The context object is not sent to the LLM. It is purely a local object...' Other options are incorrect or too restrictive."
}
```

---

### Question 3

```json
{
    "question": "You want to provide a logger and a user ID to all tool functions in your agent. What is the recommended pattern?",
    "options": [
        "Set them as global variables.",
        "Create a dataclass or Pydantic object with these fields and pass as context.",
        "Include them in the LLM input string.",
        "Add them to the agent instructions."
    ],
    "correctAnswer": "Create a dataclass or Pydantic object with these fields and pass as context.",
    "explanation": "Docs: 'A common pattern is to use a dataclass or a Pydantic object.' Globals and LLM input are not recommended for this use."
}
```

---

### Question 4

```json
{
    "question": "What is the main risk if you use different types of context objects for different tools in the same agent run?",
    "options": [
        "The agent will ignore the context.",
        "No risk; types are ignored.",
        "Type errors or runtime failures.",
        "The LLM will see all context data."
    ],
    "correctAnswer": "Type errors or runtime failures.",
    "explanation": "Docs: 'every agent, tool function, lifecycle etc for a given agent run must use the same type of context.' Otherwise, type errors may occur."
}
```

---

### Question 5

```json
{
    "question": "Which property allows you to access your custom context object inside a tool function?",
    "options": [
        "tool_context",
        "contextvar.get()",
        "wrapper.context",
        "self.context"
    ],
    "correctAnswer": "wrapper.context",
    "explanation": "Docs: 'you can access via wrapper.context'. The others are not correct for this API."
}
```

---

### Question 6

```json
{
    "question": "You want the LLM to know the user's name for every response. Which is the most robust approach?",
    "options": [
        "Set a global variable.",
        "Rely on tool function context.",
        "Add the user's name to the agent instructions (system prompt).",
        "Pass the name in the local context only."
    ],
    "correctAnswer": "Add the user's name to the agent instructions (system prompt).",
    "explanation": "Docs: 'You can add it to the Agent instructions... System prompts can be static strings, or dynamic functions.' Local context is not visible to the LLM."
}
```

---

### Question 7

```json
{
    "question": "Which of the following is NOT a valid way to make data available to the LLM?",
    "options": [
        "Adding it to agent instructions.",
        "Passing it in the local context only.",
        "Including it in the input to Runner.run().",
        "Exposing it via a function tool."
    ],
    "correctAnswer": "Passing it in the local context only.",
    "explanation": "Docs: 'The context object is not sent to the LLM.' The other methods are valid for LLM context."
}
```

---

### Question 8

```json
{
    "question": "What is the purpose of the RunContextWrapper[T] generic type in the SDK?",
    "options": [
        "To wrap LLM responses.",
        "To provide type safety for context objects passed to tools.",
        "To serialize context for the LLM.",
        "To enforce runtime validation only."
    ],
    "correctAnswer": "To provide type safety for context objects passed to tools.",
    "explanation": "Docs: 'RunContextWrapper[T], where T represents your context object type...' This enables type checking."
}
```

---

### Question 9

```json
{
    "question": "You want the LLM to access on-demand user data, but not always include it in every prompt. What is the best approach?",
    "options": [
        "Expose it via a function tool.",
        "Store it in a global variable.",
        "Add it to every input message.",
        "Include it in the agent instructions."
    ],
    "correctAnswer": "Expose it via a function tool.",
    "explanation": "Docs: 'Expose it via function tools. This is useful for on-demand context...' The other options are less flexible or not recommended."
}
```

---

### Question 10

```json
{
    "question": "Which of the following is TRUE about context and LLM visibility?",
    "options": [
        "Only data in the conversation history or prompt is visible to the LLM.",
        "All local context is automatically visible to the LLM.",
        "The LLM can access Python objects in context.",
        "Context passed to tools is always sent to the LLM."
    ],
    "correctAnswer": "Only data in the conversation history or prompt is visible to the LLM.",
    "explanation": "Docs: 'the only data it can see is from the conversation history.' Local context is not visible."
}
```

---

### Question 11

```json
{
    "question": "A developer wants to dynamically generate system prompts based on the current context. Which feature supports this?",
    "options": [
        "Static string instructions only.",
        "Dynamic functions for agent instructions.",
        "Global variables.",
        "Direct LLM context injection."
    ],
    "correctAnswer": "Dynamic functions for agent instructions.",
    "explanation": "Docs: 'System prompts can be static strings, or they can be dynamic functions that receive the context and output a string.'"
}
```

---

### Question 12

```json
{
    "question": "Which of the following is a use case for local context, but NOT for LLM context?",
    "options": [
        "Providing the user's name for LLM output.",
        "Passing a logger object to tools.",
        "Supplying the current date to the LLM.",
        "Grounding responses in external data."
    ],
    "correctAnswer": "Passing a logger object to tools.",
    "explanation": "Local context can include dependencies like loggers, which are not relevant to the LLM. The other options are for LLM context."
}
```

---

### Question 13

```json
{
    "question": "You want to ground LLM responses in up-to-date information from a database. Which approach is recommended?",
    "options": [
        "Set a global variable.",
        "Add the data to agent instructions.",
        "Use a retrieval or web search tool.",
        "Pass the database object in local context."
    ],
    "correctAnswer": "Use a retrieval or web search tool.",
    "explanation": "Docs: 'Use retrieval or web search... to fetch relevant data from files or databases.' Local context is not visible to the LLM."
}
```

---

### Question 14

```json
{
    "question": "What happens if you try to pass a context object of the wrong type to a tool function?",
    "options": [
        "The context will be converted to a dictionary.",
        "A type error or runtime failure may occur.",
        "The tool will silently succeed.",
        "The LLM will ignore the context."
    ],
    "correctAnswer": "A type error or runtime failure may occur.",
    "explanation": "Docs: 'the typechecker can catch errors (for example, if we tried to pass a tool that took a different context type).'"
}
```

---

### Question 15

```json
{
    "question": "Which of the following is NOT a recommended use of local context?",
    "options": [
        "Providing contextual data for a run.",
        "Making data available to the LLM directly.",
        "Storing helper functions and dependencies.",
        "Passing user-specific data to tools."
    ],
    "correctAnswer": "Making data available to the LLM directly.",
    "explanation": "Local context is not sent to the LLM. The other options are valid uses for local context."
}
```

---

### Question 16

```json
{
    "question": "Your team is building a multi-user chatbot platform where each user session should have access to their own preferences, authentication tokens, and a logger. You want to ensure that tool functions and lifecycle hooks can access these per-user resources, but that no user data leaks between sessions. What is the best way to architect your context management?",
    "options": [
        "Use a single shared context object for all sessions.",
        "Add all user data to the agent instructions.",
        "Create a per-session context object (e.g., a dataclass) and pass it as context to each agent run.",
        "Store all user data in global variables and reference them in tools."
    ],
    "correctAnswer": "Create a per-session context object (e.g., a dataclass) and pass it as context to each agent run.",
    "explanation": "Per-session context objects ensure isolation and correct dependency injection. Globals and shared objects risk data leakage; agent instructions are for LLM context only."
}
```

---

### Question 17

```json
{
    "question": "You are designing an agent that must fetch user profile data from a database and also log every tool call for auditing. The LLM should only see the user's name, not their authentication token or logger. How should you structure your context and prompts?",
    "options": [
        "Put all data in the agent instructions.",
        "Expose the logger as a function tool.",
        "Store the token and logger in local context, and add the user's name to agent instructions.",
        "Pass the token to the LLM via input."
    ],
    "correctAnswer": "Store the token and logger in local context, and add the user's name to agent instructions.",
    "explanation": "Sensitive data and dependencies should be in local context; only non-sensitive info should be in LLM-visible prompts."
}
```

---

### Question 18

```json
{
    "question": "A product team wants to allow the LLM to access a user's purchase history only when needed, not in every prompt. They also want to ensure that the purchase history is always up-to-date. What is the best design pattern for this requirement?",
    "options": [
        "Expose purchase history via a function tool that fetches data on demand.",
        "Add the purchase history to every agent instruction.",
        "Store the purchase history in a global variable.",
        "Pass the purchase history in the local context."
    ],
    "correctAnswer": "Expose purchase history via a function tool that fetches data on demand.",
    "explanation": "Function tools allow the LLM to request data only when needed, and can fetch the latest info each time."
}
```

---

### Question 19

```json
{
    "question": "You are building a workflow where the agent must use different tools depending on the user's role (admin, guest, member). The LLM should be aware of the user's role for decision-making, but only tool functions should access sensitive admin tokens. How do you achieve this separation?",
    "options": [
        "Add both role and tokens to the LLM input.",
        "Put both role and tokens in local context.",
        "Expose admin tokens as a function tool.",
        "Add the user's role to agent instructions and keep admin tokens in local context."
    ],
    "correctAnswer": "Add the user's role to agent instructions and keep admin tokens in local context.",
    "explanation": "Role info can be safely shared with the LLM; sensitive tokens should remain in local context for tool access only."
}
```

---

### Question 20

```json
{
    "question": "A developer is debugging an issue where a tool function is failing with a type error. The agent uses a Pydantic context object, but a new tool was added that expects a different context type. What is the most likely cause and solution?",
    "options": [
        "The context object must be a dictionary.",
        "Type errors are expected and can be ignored.",
        "The LLM is sending the wrong data.",
        "All tools and agent runs must use the same context type; update the new tool to accept the correct type."
    ],
    "correctAnswer": "All tools and agent runs must use the same context type; update the new tool to accept the correct type.",
    "explanation": "Docs: 'every agent, tool function, lifecycle etc for a given agent run must use the same type of context.' Type mismatches cause errors."
}
```

---
