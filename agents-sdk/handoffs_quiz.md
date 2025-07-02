# OpenAI Agents Python SDK — Handoffs: Professional Quiz

Below are 22 professional-level questions on the Handoffs feature of the OpenAI Agents Python SDK. Each question is presented as a separate JSON object for clarity. Only one answer is correct per question.

---

**Instructions:**

-   Read each question carefully.
-   Each code block contains a single question object with options, correct answer, and explanation.
-   Scenario-based and concept questions are included.

---

```json
{
    "question": "A fintech company uses OpenAI Agents Python SDK to route customer queries. The Triage agent hands off refund requests to a Refund agent using the handoff() function. What is the default tool name exposed to the LLM for this handoff?",
    "options": [
        "transfer_to_refund_agent",
        "handoff_refund",
        "refund_tool",
        "delegate_to_refund"
    ],
    "correctAnswer": "transfer_to_refund_agent",
    "explanation": "By default, Handoff.default_tool_name() generates 'transfer_to_<agent_name>' (docs: 'Creating a handoff'). Others are not the default naming convention."
}
```

```json
{
    "question": "You want to ensure that when a handoff occurs, the new agent does NOT see any previous tool calls in the conversation history. Which built-in helper should you use?",
    "options": [
        "handoff_filters.remove_all_tools",
        "handoff_filters.strip_history",
        "handoff_filters.clear_context",
        "handoff_filters.remove_agent_messages"
    ],
    "correctAnswer": "handoff_filters.remove_all_tools",
    "explanation": "remove_all_tools removes all tool calls from history (docs: 'Input filters'). Others are not valid or do not exist."
}
```

```json
{
    "question": "A support workflow involves a Triage agent that delegates to Billing and Refund agents. The product owner wants to customize the tool description for the handoff to the Refund agent. Which parameter should be set in the handoff() function?",
    "options": [
        "tool_description_override",
        "tool_name_override",
        "description",
        "handoff_description"
    ],
    "correctAnswer": "tool_description_override",
    "explanation": "tool_description_override customizes the tool description (docs: 'Customizing handoffs via the handoff() function'). Others are incorrect or not valid parameters."
}
```

```json
{
    "question": "A developer wants to execute custom logic (e.g., logging, data fetch) immediately when a handoff is invoked. Which handoff() parameter enables this?",
    "options": [
        "on_handoff",
        "pre_handoff",
        "handoff_callback",
        "before_transfer"
    ],
    "correctAnswer": "on_handoff",
    "explanation": "on_handoff is the callback for custom logic on handoff (docs: 'Customizing handoffs via the handoff() function'). Others are not valid parameters."
}
```

```json
{
    "question": "The Escalation agent should only be called if the LLM provides a reason for escalation. How can you enforce this using the handoff() API?",
    "options": [
        "Set input_type to a Pydantic model with a 'reason' field",
        "Set input_filter to require 'reason'",
        "Use tool_description_override to request a reason",
        "Set on_handoff to check for 'reason'"
    ],
    "correctAnswer": "Set input_type to a Pydantic model with a 'reason' field",
    "explanation": "input_type enforces structured input (docs: 'Handoff inputs'). Others do not enforce input schema at the API level."
}
```

```json
{
    "question": "Which of the following best describes the purpose of the input_filter parameter in a handoff?",
    "options": [
        "It transforms or restricts the conversation history passed to the next agent",
        "It validates the LLM's input for the handoff",
        "It changes the tool name for the handoff",
        "It disables the handoff tool dynamically"
    ],
    "correctAnswer": "It transforms or restricts the conversation history passed to the next agent",
    "explanation": "input_filter modifies the input/history for the next agent (docs: 'Input filters'). Others are unrelated to input_filter."
}
```

```json
{
    "question": "A company wants to dynamically enable or disable a handoff tool based on user authentication status. Which approach is most appropriate?",
    "options": [
        "Wrap the handoff in logic that conditionally includes it in the agent's handoffs list",
        "Set input_type to None",
        "Override the tool description to indicate disabled",
        "Use remove_all_tools filter"
    ],
    "correctAnswer": "Wrap the handoff in logic that conditionally includes it in the agent's handoffs list",
    "explanation": "Dynamic inclusion/exclusion is done by controlling the handoffs list (docs: 'Creating a handoff'). Others do not affect tool availability."
}
```

```json
{
    "question": "Which of the following is NOT a valid use of the handoff() function?",
    "options": [
        "Specifying a custom tool name",
        "Providing a callback for handoff invocation",
        "Filtering input history",
        "Directly executing the next agent's logic"
    ],
    "correctAnswer": "Directly executing the next agent's logic",
    "explanation": "handoff() configures delegation, not direct execution (docs: 'Customizing handoffs via the handoff() function'). Others are valid uses."
}
```

```json
{
    "question": "A developer wants to ensure that the LLM is aware of handoff capabilities in the agent's prompt. What is the recommended way to do this?",
    "options": [
        "Include agents.extensions.handoff_prompt.RECOMMENDED_PROMPT_PREFIX in the instructions",
        "Set tool_description_override to a long explanation",
        "Add a comment in the agent code",
        "Use input_filter to inject prompt text"
    ],
    "correctAnswer": "Include agents.extensions.handoff_prompt.RECOMMENDED_PROMPT_PREFIX in the instructions",
    "explanation": "RECOMMENDED_PROMPT_PREFIX is designed for this (docs: 'Recommended prompts'). Others do not affect the LLM's prompt."
}
```

```json
{
    "question": "Which statement about streaming behavior during a handoff is correct?",
    "options": [
        "Streaming continues seamlessly if both agents support it",
        "Streaming is always interrupted during handoff",
        "Streaming is not supported with handoffs",
        "Streaming only works if input_type is None"
    ],
    "correctAnswer": "Streaming continues seamlessly if both agents support it",
    "explanation": "Streaming can continue if both agents are compatible (docs: general SDK streaming behavior). Others are incorrect."
}
```

```json
{
    "question": "The LLM is instructed to provide a reason for escalation, but sometimes omits it. What is the best way to enforce this requirement?",
    "options": [
        "Define input_type as a Pydantic model with required fields",
        "Add a note in tool_description_override",
        "Use input_filter to reject missing reasons",
        "Set on_handoff to print a warning"
    ],
    "correctAnswer": "Define input_type as a Pydantic model with required fields",
    "explanation": "input_type enforces required fields at the API level (docs: 'Handoff inputs'). Others are less robust or not enforced."
}
```

```json
{
    "question": "Which of the following is a best practice when designing handoff flows between agents?",
    "options": [
        "Clearly document handoff points and expected inputs",
        "Always use untyped handoffs for flexibility",
        "Avoid using input filters",
        "Disable streaming for all handoffs"
    ],
    "correctAnswer": "Clearly document handoff points and expected inputs",
    "explanation": "Documentation ensures maintainability and clarity (docs: 'Recommended prompts'). Others are not best practices."
}
```

```json
{
    "question": "A developer wants to override both the tool name and description for a handoff. Which parameters should they use?",
    "options": [
        "tool_name_override and tool_description_override",
        "input_type and input_filter",
        "on_handoff and input_type",
        "tool_name and tool_description"
    ],
    "correctAnswer": "tool_name_override and tool_description_override",
    "explanation": "These parameters allow overriding name and description (docs: 'Customizing handoffs via the handoff() function'). Others are incorrect."
}
```

```json
{
    "question": "Which object type is used to represent structured input for a handoff?",
    "options": [
        "A Pydantic BaseModel",
        "A Python dict",
        "A string",
        "A list of tuples"
    ],
    "correctAnswer": "A Pydantic BaseModel",
    "explanation": "Pydantic models are used for typed handoff input (docs: 'Handoff inputs'). Others are not supported for input_type."
}
```

```json
{
    "question": "You want to log every time a handoff occurs, including the input data provided by the LLM. Where should you implement this logic?",
    "options": [
        "In the on_handoff callback",
        "In the input_filter function",
        "In the agent's instructions",
        "In the tool_description_override"
    ],
    "correctAnswer": "In the on_handoff callback",
    "explanation": "on_handoff is designed for custom logic on handoff (docs: 'Customizing handoffs via the handoff() function'). Others are not for execution logic."
}
```

```json
{
    "question": "Which of the following is true about using an Agent directly versus using handoff() in the handoffs list?",
    "options": [
        "Both are valid; handoff() allows more customization",
        "Only handoff() is valid",
        "Agent directly disables input filtering",
        "Agent directly always disables streaming"
    ],
    "correctAnswer": "Both are valid; handoff() allows more customization",
    "explanation": "You can use either, but handoff() provides more options (docs: 'Basic Usage'). Others are incorrect."
}
```

```json
{
    "question": "The FAQ agent should only see the last user message, not the full conversation, when handed off. How can you achieve this?",
    "options": [
        "Provide an input_filter that trims the history",
        "Set input_type to only accept the last message",
        "Override the tool name",
        "Use on_handoff to delete history"
    ],
    "correctAnswer": "Provide an input_filter that trims the history",
    "explanation": "input_filter can modify the history (docs: 'Input filters'). Others do not affect the conversation history."
}
```

```json
{
    "question": "Which of the following is a common error when implementing handoffs?",
    "options": [
        "Forgetting to specify input_type when structured input is required",
        "Using tool_name_override for input validation",
        "Setting on_handoff to a string",
        "Passing a list to tool_description_override"
    ],
    "correctAnswer": "Forgetting to specify input_type when structured input is required",
    "explanation": "input_type is needed for structured input (docs: 'Handoff inputs'). Others are API misuse or not possible."
}
```

```json
{
    "question": "You want to prevent the LLM from invoking a handoff tool unless a certain condition is met at runtime. What is the best approach?",
    "options": [
        "Dynamically include/exclude the handoff in the agent's handoffs list",
        "Set input_type to None",
        "Use input_filter to block calls",
        "Override the tool description to say 'disabled'"
    ],
    "correctAnswer": "Dynamically include/exclude the handoff in the agent's handoffs list",
    "explanation": "Dynamic logic is best handled by controlling the handoffs list (docs: 'Creating a handoff'). Others do not prevent invocation."
}
```

```json
{
    "question": "Which helper can you use to automatically add recommended handoff instructions to an agent's prompt?",
    "options": [
        "agents.extensions.handoff_prompt.prompt_with_handoff_instructions",
        "handoff_filters.add_prompt",
        "handoff_prompt.RECOMMENDED_PROMPT_PREFIX",
        "handoff_prompt.inject_instructions"
    ],
    "correctAnswer": "agents.extensions.handoff_prompt.prompt_with_handoff_instructions",
    "explanation": "This helper adds recommended instructions (docs: 'Recommended prompts'). Others are not valid or are constants."
}
```

```json
{
    "question": "The LLM is not invoking the correct handoff tool because the tool name is ambiguous. What is the best way to resolve this?",
    "options": [
        "Set tool_name_override to a unique, descriptive name",
        "Change input_type",
        "Use input_filter to rename the tool",
        "Set on_handoff to print the tool name"
    ],
    "correctAnswer": "Set tool_name_override to a unique, descriptive name",
    "explanation": "tool_name_override customizes the tool name (docs: 'Customizing handoffs via the handoff() function'). Others do not affect tool naming."
}
```

```json
{
    "question": "Which of the following is NOT a benefit of using typed handoffs (with input_type)?",
    "options": [
        "Enforces structured input from the LLM",
        "Improves validation and error handling",
        "Allows arbitrary Python code execution",
        "Clarifies expected data for the next agent"
    ],
    "correctAnswer": "Allows arbitrary Python code execution",
    "explanation": "input_type enforces structure, not code execution (docs: 'Handoff inputs'). Others are true benefits."
}
```

```json
{
    "question": "You want to remove all previous tool calls and only pass the last user message to the next agent during a handoff. Which approach is best?",
    "options": [
        "Chain handoff_filters.remove_all_tools with a custom input_filter",
        "Set input_type to str",
        "Override the tool description",
        "Use on_handoff to clear history"
    ],
    "correctAnswer": "Chain handoff_filters.remove_all_tools with a custom input_filter",
    "explanation": "You can compose filters for custom behavior (docs: 'Input filters'). Others do not achieve both requirements."
}
```
