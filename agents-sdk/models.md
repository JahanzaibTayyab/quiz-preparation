# Models Quiz

Below are 12 professional-level questions on model usage, configuration, and troubleshooting in the OpenAI Agents SDK, including OpenAI and non-OpenAI models, LiteLLM, model mixing, tracing, and best practices.

---

## Questions

### Question 1

```json
{
    "question": "You want to use a non-OpenAI model (e.g., Claude or Gemini) with the Agents SDK. What is the recommended way to do this?",
    "options": [
        "Directly subclass OpenAIResponsesModel",
        "Set OPENAI_API_KEY to your non-OpenAI provider's key",
        "Use the LiteLLM integration and prefix the model name with 'litellm/'",
        "Only use OpenAIChatCompletionsModel with a custom endpoint"
    ],
    "correctAnswer": "Use the LiteLLM integration and prefix the model name with 'litellm/'",
    "explanation": "LiteLLM integration allows you to use many non-OpenAI models by prefixing the model name with 'litellm/'."
}
```

---

### Question 2

```json
{
    "question": "A developer wants to use a custom LLM provider that is OpenAI API compatible. Which approach allows them to globally set the client for all agents?",
    "options": [
        "Override the ModelSettings for each agent",
        "Use set_default_openai_client with an AsyncOpenAI instance",
        "Set the model on each Agent individually",
        "Use ModelProvider at the Runner.run level"
    ],
    "correctAnswer": "Use set_default_openai_client with an AsyncOpenAI instance",
    "explanation": "set_default_openai_client lets you globally set an OpenAI-compatible client for all agents."
}
```

---

### Question 3

```json
{
    "question": "You want to use different models for different agents in a workflow (e.g., a fast model for triage, a powerful model for complex tasks). Which configuration supports this?",
    "options": [
        "Mix OpenAIResponsesModel and OpenAIChatCompletionsModel in the same workflow without checking feature compatibility",
        "Set the model on each Agent instance individually",
        "Only use ModelProvider at the Runner.run level",
        "Use a single model for all agents"
    ],
    "correctAnswer": "Set the model on each Agent instance individually",
    "explanation": "You can assign different models to each agent by setting the model on each Agent instance."
}
```

---

### Question 4

```json
{
    "question": "A user gets a 401 error when using a non-OpenAI model and tracing is enabled. What is the most likely cause?",
    "options": [
        "The model name is not prefixed with 'litellm/'",
        "Traces are uploaded to OpenAI servers and require an OpenAI API key",
        "The model does not support structured outputs",
        "The Responses API is not supported by the provider"
    ],
    "correctAnswer": "Traces are uploaded to OpenAI servers and require an OpenAI API key",
    "explanation": "Tracing uploads traces to OpenAI, so an OpenAI API key is required even for non-OpenAI models unless you disable tracing or use a custom processor."
}
```

---

### Question 5

```json
{
    "question": "Which of the following is a best practice when mixing OpenAIResponsesModel and OpenAIChatCompletionsModel in a workflow?",
    "options": [
        "Mixing is not supported in the SDK",
        "Only use OpenAIChatCompletionsModel for structured outputs",
        "Always use both models together for best results",
        "Ensure all required features are supported by both model shapes"
    ],
    "correctAnswer": "Ensure all required features are supported by both model shapes",
    "explanation": "Mixing model shapes is possible, but you must ensure feature compatibility across models."
}
```

---

### Question 6

```json
{
    "question": "A developer wants to pass extra parameters (e.g., 'service_tier', 'user') to the OpenAI Responses API. How should they do this?",
    "options": [
        "Set them as top-level arguments in Agent",
        "Only pass them via environment variables",
        "Override the model property on the Agent",
        "Use the extra_args parameter in ModelSettings"
    ],
    "correctAnswer": "Use the extra_args parameter in ModelSettings",
    "explanation": "extra_args in ModelSettings lets you pass additional parameters to the API."
}
```

---

### Question 7

```json
{
    "question": "You want to use a model that does not support the Responses API and get 404 errors. What is a recommended solution?",
    "options": [
        "Switch to OpenAIChatCompletionsModel or set_default_openai_api('chat_completions')",
        "Disable tracing",
        "Prefix the model name with 'litellm/'",
        "Use ModelProvider at the Runner.run level"
    ],
    "correctAnswer": "Switch to OpenAIChatCompletionsModel or set_default_openai_api('chat_completions')",
    "explanation": "If the provider doesn't support the Responses API, use Chat Completions or set the default API accordingly."
}
```

---

### Question 8

```json
{
    "question": "A team wants to use structured outputs with their LLM provider, but receives errors about 'response_format.type'. What is the likely cause?",
    "options": [
        "The provider does not support specifying a JSON schema for outputs",
        "Tracing is not enabled",
        "The model name is not prefixed with 'litellm/'",
        "The API key is missing"
    ],
    "correctAnswer": "The provider does not support specifying a JSON schema for outputs",
    "explanation": "Some providers support JSON outputs but not custom schemas, leading to errors with structured outputs."
}
```

---

### Question 9

```json
{
    "question": "Which of the following is NOT a recommended way to use non-OpenAI models in the Agents SDK?",
    "options": [
        "Use LiteLLM integration with the 'litellm/' prefix",
        "Directly subclass OpenAIResponsesModel for every provider",
        "Set a custom OpenAI-compatible client with set_default_openai_client",
        "Use ModelProvider at the Runner.run level"
    ],
    "correctAnswer": "Directly subclass OpenAIResponsesModel for every provider",
    "explanation": "Subclassing OpenAIResponsesModel is not recommended; use LiteLLM, ModelProvider, or set_default_openai_client instead."
}
```

---

### Question 10

```json
{
    "question": "A developer wants to globally disable tracing when using non-OpenAI models. What should they do?",
    "options": [
        "Call set_tracing_disabled(True)",
        "Remove the OPENAI_API_KEY environment variable",
        "Only use OpenAI models",
        "Set the model to 'gpt-3.5-turbo'"
    ],
    "correctAnswer": "Call set_tracing_disabled(True)",
    "explanation": "set_tracing_disabled(True) disables tracing globally, avoiding errors with non-OpenAI models."
}
```

---

### Question 11

```json
{
    "question": "You want to configure a model's temperature and other generation parameters for an agent. What is the recommended approach?",
    "options": [
        "Pass a ModelSettings instance to the agent's model_settings parameter",
        "Set them as top-level arguments in Agent",
        "Override the model property on the Agent",
        "Use extra_args in the Agent constructor"
    ],
    "correctAnswer": "Pass a ModelSettings instance to the agent's model_settings parameter",
    "explanation": "ModelSettings lets you configure temperature and other parameters for the model."
}
```

---

### Question 12

```json
{
    "question": "When mixing models from different providers in a workflow, what should you be especially careful about?",
    "options": [
        "Feature differences such as structured outputs, multimodal input, and tool support",
        "Always using the same model shape for all agents",
        "Only using OpenAI models for all agents",
        "Setting the same API key for all providers"
    ],
    "correctAnswer": "Feature differences such as structured outputs, multimodal input, and tool support",
    "explanation": "Different providers support different features; you must account for these differences to avoid errors."
}
```

---
