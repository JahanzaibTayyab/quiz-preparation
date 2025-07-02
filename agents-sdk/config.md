# SDK Configuration Quiz

Below are 10 professional-level questions on configuring the OpenAI Agents SDK, including API key management, client setup, tracing, logging, and sensitive data handling.

---

## Questions

### Question 1

```json
{
    "question": "You want to set the OpenAI API key for LLM requests and tracing, but cannot set the environment variable before your app starts. What should you do?",
    "options": [
        "Set the key as a top-level argument to Agent",
        "Call set_default_openai_key() in your code",
        "Set the key in a .env file only",
        "Use set_default_openai_client() with a custom client"
    ],
    "correctAnswer": "Call set_default_openai_key() in your code",
    "explanation": "set_default_openai_key() lets you set the API key programmatically if you can't set the environment variable."
}
```

---

### Question 2

```json
{
    "question": "A developer wants to use a custom OpenAI-compatible endpoint for all LLM requests. What is the recommended approach?",
    "options": [
        "Set the base_url in the environment variable",
        "Override the model property on each Agent",
        "Call set_default_openai_api('chat_completions')",
        "Use set_default_openai_client() with an AsyncOpenAI instance"
    ],
    "correctAnswer": "Use set_default_openai_client() with an AsyncOpenAI instance",
    "explanation": "set_default_openai_client() lets you set a custom client with a custom base_url and API key."
}
```

---

### Question 3

```json
{
    "question": "By default, which OpenAI API does the SDK use for LLM requests?",
    "options": [
        "Moderation API",
        "Chat Completions API",
        "Responses API",
        "Embeddings API"
    ],
    "correctAnswer": "Responses API",
    "explanation": "The SDK uses the OpenAI Responses API by default, but you can override this."
}
```

---

### Question 4

```json
{
    "question": "You want to switch the SDK to use the Chat Completions API instead of the default. What should you do?",
    "options": [
        "Call set_default_openai_api('chat_completions')",
        "Set OPENAI_API_KEY to a different value",
        "Change the model name to 'gpt-3.5-turbo'",
        "Use set_default_openai_client() with a custom client"
    ],
    "correctAnswer": "Call set_default_openai_api('chat_completions')",
    "explanation": "set_default_openai_api('chat_completions') switches the API used for LLM requests."
}
```

---

### Question 5

```json
{
    "question": "A team wants to use a different API key for tracing than for LLM requests. What is the correct way to do this?",
    "options": [
        "Call set_tracing_export_api_key() with the tracing key",
        "Set a different key in the environment variable",
        "Disable tracing entirely",
        "Use set_default_openai_key() twice"
    ],
    "correctAnswer": "Call set_tracing_export_api_key() with the tracing key",
    "explanation": "set_tracing_export_api_key() lets you set a separate API key for tracing."
}
```

---

### Question 6

```json
{
    "question": "How can you globally disable tracing in the SDK?",
    "options": [
        "Set the model to 'gpt-3.5-turbo'",
        "Call set_tracing_disabled(True)",
        "Remove the OPENAI_API_KEY environment variable",
        "Call set_default_openai_api('chat_completions')"
    ],
    "correctAnswer": "Call set_tracing_disabled(True)",
    "explanation": "set_tracing_disabled(True) disables tracing globally."
}
```

---

### Question 7

```json
{
    "question": "You want to enable verbose logging for debugging. What is the recommended function to call?",
    "options": [
        "set_tracing_export_api_key()",
        "enable_verbose_stdout_logging()",
        "set_default_openai_key()",
        "set_default_openai_client()"
    ],
    "correctAnswer": "enable_verbose_stdout_logging()",
    "explanation": "enable_verbose_stdout_logging() enables verbose logging to stdout."
}
```

---

### Question 8

```json
{
    "question": "A developer wants to customize logging (e.g., add handlers, set log levels). What is the correct approach?",
    "options": [
        "Set environment variables for log level",
        "Override the Agent class",
        "Call set_default_openai_api() with a log level argument",
        "Use Python's logging module to configure the 'openai.agents' logger"
    ],
    "correctAnswer": "Use Python's logging module to configure the 'openai.agents' logger",
    "explanation": "You can fully customize logging using Python's logging module."
}
```

---

### Question 9

```json
{
    "question": "You want to prevent LLM inputs and outputs from being logged for privacy reasons. What should you do?",
    "options": [
        "Set the OPENAI_AGENTS_DONT_LOG_MODEL_DATA environment variable to 1",
        "Disable all logging in Python",
        "Remove the OPENAI_API_KEY",
        "Call set_tracing_disabled(True)"
    ],
    "correctAnswer": "Set the OPENAI_AGENTS_DONT_LOG_MODEL_DATA environment variable to 1",
    "explanation": "Setting this environment variable disables logging of LLM inputs and outputs."
}
```

---

### Question 10

```json
{
    "question": "How can you prevent tool inputs and outputs from being logged by the SDK?",
    "options": [
        "Set the OPENAI_AGENTS_DONT_LOG_TOOL_DATA environment variable to 1",
        "Disable tracing",
        "Remove the OPENAI_API_KEY",
        "Set the log level to WARNING"
    ],
    "correctAnswer": "Set the OPENAI_AGENTS_DONT_LOG_TOOL_DATA environment variable to 1",
    "explanation": "This environment variable disables logging of tool inputs and outputs."
}
```

---
