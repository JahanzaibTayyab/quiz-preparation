# OpenAI Agents SDK Advanced Quiz

Below are 40+ professional-level questions on advanced usage of the OpenAI Agents SDK, covering tools, handoffs, tracing, context, guardrails, and more.

---

## Questions

### Question 1

```json
{
    "question": "You are building a customer support platform where each user session is handled by a central agent. This agent can delegate billing, refund, and FAQ queries to specialized agents. You want to ensure that when a handoff occurs, only the last two messages from the conversation history are passed to the next agent. Which handoff parameter should you use?",
    "options": [
        "on_handoff",
        "input_type",
        "input_filter",
        "tool_name_override"
    ],
    "correctAnswer": "input_filter",
    "explanation": "The input_filter parameter allows you to control what part of the conversation history is passed to the next agent. See 'Input filters' in handoffs.md."
}
```

---

### Question 2

```json
{
    "question": "A developer wants to let an agent run a shell command on the user's machine. Which built-in tool should they use?",
    "options": [
        "FileSearchTool",
        "WebSearchTool",
        "LocalShellTool",
        "HostedMCPTool"
    ],
    "correctAnswer": "LocalShellTool",
    "explanation": "LocalShellTool runs shell commands on your machine. See 'Hosted tools' in tools.md."
}
```

---

### Question 3

```json
{
    "question": "You want to expose a Python function as a tool, but you need to override its name and description, and disable docstring parsing. Which decorator and parameters should you use?",
    "options": [
        "@function_tool(name_override=..., description_override=..., use_docstring_info=False)",
        "@function_tool(schema_override=..., docstring_parser=None)",
        "@tool_function(override_name=..., override_description=..., docstring_off=True)",
        "@function_tool(name=..., description=..., docstring=False)"
    ],
    "correctAnswer": "@function_tool(name_override=..., description_override=..., use_docstring_info=False)",
    "explanation": "The function_tool decorator supports name_override, description_override, and use_docstring_info. See 'Function tools' in tools.md."
}
```

---

### Question 4

```json
{
    "question": "A financial services company must ensure that no sensitive data from LLM generations or function tool calls is stored in traces. Which configuration should they use?",
    "options": [
        "Set RunConfig.trace_include_sensitive_data to False",
        "Set trace.disabled to True",
        "Set VoicePipelineConfig.trace_include_sensitive_audio_data to False",
        "Set OPENAI_AGENTS_DISABLE_TRACING=1"
    ],
    "correctAnswer": "Set RunConfig.trace_include_sensitive_data to False",
    "explanation": "This disables capturing sensitive LLM and function tool data in traces. See 'Sensitive data' in tracing.md."
}
```

---

### Question 5

```json
{
    "question": "You want to allow the LLM to fetch the latest weather for a location, but only when needed, not in every prompt. What is the best approach?",
    "options": [
        "Expose the weather API as a function tool",
        "Store the weather data in a global variable",
        "Add the weather data to every agent instruction",
        "Pass the weather data in the local context"
    ],
    "correctAnswer": "Expose the weather API as a function tool",
    "explanation": "Function tools allow the LLM to fetch data on demand. See 'Function tools' and 'Agent/LLM context' in tools.md and context.md."
}
```

---

### Question 6

```json
{
    "question": "A developer wants to use a Pydantic model as the argument type for a function tool. What is the main benefit?",
    "options": [
        "The tool can only be used asynchronously",
        "Automatic JSON schema generation for tool arguments",
        "Faster tool execution",
        "The tool will be registered as a hosted tool"
    ],
    "correctAnswer": "Automatic JSON schema generation for tool arguments",
    "explanation": "Pydantic models enable automatic schema extraction for tool arguments. See 'Function tools' in tools.md."
}
```

---

### Question 7

```json
{
    "question": "You want to customize the output of a tool-agent before returning it to the central agent, for example by extracting a JSON payload from the sub-agent's chat history. Which argument should you use?",
    "options": [
        "output_type_override",
        "custom_output_extractor",
        "tool_description_override",
        "on_invoke_tool"
    ],
    "correctAnswer": "custom_output_extractor",
    "explanation": "custom_output_extractor lets you modify the output before returning it. See 'Custom output extraction' in tools.md."
}
```

---

### Question 8

```json
{
    "question": "A developer wants to run a guardrail that checks if the agent's output contains any math. Where should this guardrail be attached?",
    "options": [
        "As a global guardrail",
        "As an output guardrail on the agent",
        "As a lifecycle hook",
        "As an input guardrail on the agent"
    ],
    "correctAnswer": "As an output guardrail on the agent",
    "explanation": "Output guardrails validate the final output, such as checking for math content. See 'Output guardrails' in guardrails.md."
}
```

---

### Question 9

```json
{
    "question": "You want to ensure that every tool function and lifecycle hook in an agent run receives the same type of context object. What is the main risk if you use different types?",
    "options": [
        "The agent will ignore the context",
        "Type errors or runtime failures",
        "No risk; types are ignored",
        "The LLM will see all context data"
    ],
    "correctAnswer": "Type errors or runtime failures",
    "explanation": "All components must use the same context type for type safety. See 'Local context' in context.md."
}
```

---

### Question 10

```json
{
    "question": "A developer wants to disable tracing for all agent runs in their environment. What is the most efficient approach?",
    "options": [
        "Remove all trace processors",
        "Set the OPENAI_AGENTS_DISABLE_TRACING environment variable",
        "Set RunConfig.tracing_disabled = True for each run",
        "Use set_trace_processors() with an empty list"
    ],
    "correctAnswer": "Set the OPENAI_AGENTS_DISABLE_TRACING environment variable",
    "explanation": "This disables tracing globally. See 'Tracing is enabled by default' in tracing.md."
}
```

---

### Question 11

```json
{
    "question": "You are building a multi-agent workflow where the orchestrator agent uses specialized agents as tools. What is the main advantage of using agents as tools instead of handoffs?",
    "options": [
        "The orchestrator retains control and can call multiple agents in a single workflow",
        "Each agent runs in isolation and cannot share context",
        "Handoffs are required for all agent-to-agent communication",
        "Agents as tools cannot return structured outputs"
    ],
    "correctAnswer": "The orchestrator retains control and can call multiple agents in a single workflow",
    "explanation": "Agents as tools allow orchestration without handing off control. See 'Agents as tools' in tools.md."
}
```

---

### Question 12

```json
{
    "question": "A developer wants to provide a custom error message to the LLM when a function tool fails. Which parameter should they use?",
    "options": [
        "failure_error_function",
        "on_invoke_tool",
        "tool_error_handler",
        "error_message_override"
    ],
    "correctAnswer": "failure_error_function",
    "explanation": "failure_error_function lets you customize error responses for function tools. See 'Handling errors in function tools' in tools.md."
}
```

---

### Question 13

```json
{
    "question": "You want to ensure that only the first agent in a multi-agent chain runs input guardrails. What is the default behavior of the SDK?",
    "options": [
        "Only the first agent's input guardrails are executed",
        "All agents run input guardrails",
        "Input guardrails are disabled by default",
        "Input guardrails run only if max_turns > 1"
    ],
    "correctAnswer": "Only the first agent's input guardrails are executed",
    "explanation": "Input guardrails only run for the first agent. See 'Input guardrails' in guardrails.md."
}
```

---

### Question 14

```json
{
    "question": "A developer wants to add a guardrail that blocks any output containing personally identifiable information (PII). What is the best way to implement this?",
    "options": [
        "Attach an output guardrail that checks for PII patterns in the agent's output",
        "Add a warning in the agent instructions",
        "Use a hosted tool to filter PII",
        "Set output_type to a Pydantic model"
    ],
    "correctAnswer": "Attach an output guardrail that checks for PII patterns in the agent's output",
    "explanation": "Output guardrails can validate and block sensitive output. See 'Output guardrails' in guardrails.md."
}
```

---

### Question 15

```json
{
    "question": "You want to run a custom trace processor that logs traces to an external observability platform in addition to OpenAI's backend. Which method should you use?",
    "options": [
        "add_trace_processor()",
        "set_trace_processors()",
        "replace_trace_exporter()",
        "trace.add_export_destination()"
    ],
    "correctAnswer": "add_trace_processor()",
    "explanation": "add_trace_processor() adds an additional processor, sending traces to multiple destinations. See 'Custom tracing processors' in tracing.md."
}
```

---

### Question 16

```json
{
    "question": "A developer wants to ensure that the LLM can only see data included in the conversation history or prompt. Which of the following is TRUE?",
    "options": [
        "Only data in the conversation history or prompt is visible to the LLM",
        "All local context is automatically visible to the LLM",
        "The LLM can access Python objects in context",
        "Context passed to tools is always sent to the LLM"
    ],
    "correctAnswer": "Only data in the conversation history or prompt is visible to the LLM",
    "explanation": "LLMs only see data in the conversation history or prompt. See 'Agent/LLM context' in context.md."
}
```

---

### Question 17

```json
{
    "question": "You want to dynamically generate system prompts based on the current context, such as user role or session data. Which feature supports this?",
    "options": [
        "Dynamic functions for agent instructions",
        "Static string instructions only",
        "Global variables",
        "Direct LLM context injection"
    ],
    "correctAnswer": "Dynamic functions for agent instructions",
    "explanation": "Agent instructions can be dynamic functions that receive context. See 'Agent/LLM context' in context.md."
}
```

---

### Question 18

```json
{
    "question": "A developer wants to use a custom function tool that is not a Python function. What must they provide when creating a FunctionTool object directly?",
    "options": [
        "name, description, params_json_schema, on_invoke_tool",
        "name, docstring, params_json_schema, error_handler",
        "name, description, function_signature, on_error",
        "name, params_json_schema, tool_type, on_invoke"
    ],
    "correctAnswer": "name, description, params_json_schema, on_invoke_tool",
    "explanation": "These are the required parameters for a custom FunctionTool. See 'Custom function tools' in tools.md."
}
```

---

### Question 19

```json
{
    "question": "You want to ensure that a tool function can access both the context and a file path argument. What is the correct function signature?",
    "options": [
        "def tool(ctx: RunContextWrapper[Any], path: str) -> str",
        "def tool(path: str, ctx: RunContextWrapper[Any]) -> str",
        "def tool(path: str) -> str",
        "def tool(ctx: str, path: RunContextWrapper[Any]) -> str"
    ],
    "correctAnswer": "def tool(ctx: RunContextWrapper[Any], path: str) -> str",
    "explanation": "The context must be the first argument if present. See 'Function tools' in tools.md."
}
```

---

### Question 20

```json
{
    "question": "A developer wants to disable docstring parsing for a function tool. Which parameter should they set?",
    "options": [
        "use_docstring_info=False",
        "docstring_parser=None",
        "disable_docstring=True",
        "parse_docstring=False"
    ],
    "correctAnswer": "use_docstring_info=False",
    "explanation": "Set use_docstring_info to False to disable docstring parsing. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 21

```json
{
    "question": "You are designing a workflow where an agent must call a tool that fetches sensitive user data. You want to ensure that if the tool fails, the LLM receives a custom error message, but you also want to log the error for auditing. What is the best approach?",
    "options": [
        "Provide a failure_error_function for the tool and log errors inside it",
        "Set use_docstring_info=False and handle errors in the docstring",
        "Attach an output guardrail to the tool",
        "Set the tool as a hosted tool and rely on default error handling"
    ],
    "correctAnswer": "Provide a failure_error_function for the tool and log errors inside it",
    "explanation": "failure_error_function lets you customize the error message and can include logging logic. See 'Handling errors in function tools' in tools.md."
}
```

---

### Question 22

```json
{
    "question": "A team wants to orchestrate a workflow where the LLM can call multiple agents as tools, each with their own specialized instructions and context. What is a key benefit of this approach over using handoffs?",
    "options": [
        "The orchestrator can call multiple agents in a single workflow and aggregate their results",
        "Each agent runs in a separate process, improving performance",
        "Handoffs are required for all agent-to-agent communication",
        "Agents as tools cannot return structured outputs"
    ],
    "correctAnswer": "The orchestrator can call multiple agents in a single workflow and aggregate their results",
    "explanation": "Agents as tools allow orchestration and aggregation, while handoffs transfer control. See 'Agents as tools' in tools.md."
}
```

---

### Question 23

```json
{
    "question": "You want to ensure that a handoff to a specialized agent includes a custom tool name and description for the LLM. Which handoff parameters should you use?",
    "options": [
        "tool_name_override and tool_description_override",
        "input_filter and on_handoff",
        "input_type and failure_error_function",
        "custom_output_extractor and params_json_schema"
    ],
    "correctAnswer": "tool_name_override and tool_description_override",
    "explanation": "These parameters let you customize the tool name and description. See 'Customizing handoffs via the handoff() function' in handoffs.md."
}
```

---

### Question 24

```json
{
    "question": "A developer wants to run a guardrail that checks for policy violations by calling another agent under the hood. What is the best practice for returning the result?",
    "options": [
        "Return a GuardrailFunctionOutput with output_info set to the result and tripwire_triggered set appropriately",
        "Raise an exception directly in the guardrail function",
        "Return only a boolean value",
        "Modify the agent's output directly"
    ],
    "correctAnswer": "Return a GuardrailFunctionOutput with output_info set to the result and tripwire_triggered set appropriately",
    "explanation": "The guardrail function should return a GuardrailFunctionOutput, not raise exceptions or modify output directly. See 'Implementing a guardrail' in guardrails.md."
}
```

---

### Question 25

```json
{
    "question": "You want to ensure that a tool function's argument schema includes detailed descriptions for each parameter. What is the best way to achieve this?",
    "options": [
        "Provide detailed docstrings for the function and enable docstring parsing",
        "Set use_docstring_info=False and manually edit the schema",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Provide detailed docstrings for the function and enable docstring parsing",
    "explanation": "Docstrings are parsed for argument descriptions if enabled. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 26

```json
{
    "question": "A developer wants to ensure that only the last agent in a multi-agent workflow runs output guardrails. What is the default behavior of the SDK?",
    "options": [
        "Only the last agent's output guardrails are executed",
        "All agents run output guardrails",
        "Output guardrails are disabled by default",
        "Output guardrails run only if max_turns > 1"
    ],
    "correctAnswer": "Only the last agent's output guardrails are executed",
    "explanation": "Output guardrails only run for the last agent. See 'Output guardrails' in guardrails.md."
}
```

---

### Question 27

```json
{
    "question": "You want to run a trace that groups multiple Runner.run() calls under a single workflow name. What is the recommended approach?",
    "options": [
        "Wrap the calls in a with trace('workflow_name') context manager",
        "Set trace_id manually for each run",
        "Use group_id for each run",
        "Call trace.start() and trace.finish() around each run"
    ],
    "correctAnswer": "Wrap the calls in a with trace('workflow_name') context manager",
    "explanation": "This groups multiple runs under a single trace. See 'Higher level traces' in tracing.md."
}
```

---

### Question 28

```json
{
    "question": "A developer wants to prevent audio data from being stored in traces for privacy reasons. Which configuration should they use?",
    "options": [
        "Set VoicePipelineConfig.trace_include_sensitive_audio_data to False",
        "Set RunConfig.trace_include_sensitive_data to False",
        "Set OPENAI_AGENTS_DISABLE_TRACING=1",
        "Set trace.disabled to True"
    ],
    "correctAnswer": "Set VoicePipelineConfig.trace_include_sensitive_audio_data to False",
    "explanation": "This disables capturing audio data in traces. See 'Sensitive data' in tracing.md."
}
```

---

### Question 29

```json
{
    "question": "You want to add a handoff that triggers a callback function as soon as the handoff is invoked, for example to log the event or fetch data. Which parameter should you use?",
    "options": [
        "on_handoff",
        "input_filter",
        "tool_name_override",
        "input_type"
    ],
    "correctAnswer": "on_handoff",
    "explanation": "on_handoff is a callback executed when the handoff is invoked. See 'Customizing handoffs via the handoff() function' in handoffs.md."
}
```

---

### Question 30

```json
{
    "question": "A developer wants to ensure that a function tool can be used both synchronously and asynchronously. What is the best practice?",
    "options": [
        "Write the function as async, but allow the SDK to call it synchronously if needed",
        "Write two versions of the function, one sync and one async",
        "Use a hosted tool instead",
        "Set use_docstring_info=False"
    ],
    "correctAnswer": "Write the function as async, but allow the SDK to call it synchronously if needed",
    "explanation": "The SDK can handle async tools in sync workflows. See 'Function tools' in tools.md."
}
```

---

### Question 31

```json
{
    "question": "You want to ensure that a tool function's argument schema supports optional parameters. What is the best way to define this?",
    "options": [
        "Use default values or Optional types in the function signature",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Use default values or Optional types in the function signature",
    "explanation": "Default values and Optional types are reflected in the schema. See 'Function tools' in tools.md."
}
```

---

### Question 32

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports complex nested types. What is the best way to define this?",
    "options": [
        "Use Pydantic models or TypedDicts for nested arguments",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Use Pydantic models or TypedDicts for nested arguments",
    "explanation": "Pydantic models and TypedDicts support complex nested schemas. See 'Function tools' in tools.md."
}
```

---

### Question 33

```json
{
    "question": "You want to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 34

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 35

```json
{
    "question": "You want to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 36

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 37

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 38

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 39

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---

### Question 40

```json
{
    "question": "A developer wants to ensure that a function tool's argument schema supports argument descriptions in Google, Sphinx, or Numpy docstring formats. What should you do?",
    "options": [
        "Write docstrings in one of the supported formats and enable docstring parsing",
        "Set use_docstring_info=False",
        "Override the tool name and description only",
        "Use a hosted tool instead of a function tool"
    ],
    "correctAnswer": "Write docstrings in one of the supported formats and enable docstring parsing",
    "explanation": "The SDK supports Google, Sphinx, and Numpy docstring formats. See 'Automatic argument and docstring parsing' in tools.md."
}
```

---
