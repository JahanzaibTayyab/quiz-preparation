# Tracing Quiz

Below are 22 professional-level questions on tracing in the OpenAI Agents SDK, covering concepts, implementation, and best practices.

---

## Questions

### Question 1

```json
{
    "question": "A SaaS company is building a customer support agent using the Agents SDK. They want to monitor every LLM generation, tool call, and handoff for debugging and compliance. Which built-in feature best supports this requirement?",
    "options": [
        "Tracing, which collects a comprehensive record of events during agent runs.",
        "Guardrails, which enforce input/output constraints.",
        "Function tool decorators, which log function calls.",
        "Custom span creation, which only tracks LLM generations."
    ],
    "correctAnswer": "Tracing, which collects a comprehensive record of events during agent runs.",
    "explanation": "Tracing collects all relevant events (LLM, tools, handoffs, etc.) as described in 'The Agents SDK includes built-in tracing...' section. Guardrails and decorators are more limited in scope."
}
```

---

### Question 2

```json
{
    "question": "Which environment variable can be set to globally disable tracing in the Agents SDK?",
    "options": [
        "OPENAI_AGENTS_DISABLE_TRACING",
        "AGENTS_DISABLE_ALL",
        "DISABLE_AGENT_TRACING",
        "OPENAI_DISABLE_SDK_TRACING"
    ],
    "correctAnswer": "OPENAI_AGENTS_DISABLE_TRACING",
    "explanation": "The docs state: 'You can globally disable tracing by setting the env var OPENAI_AGENTS_DISABLE_TRACING=1'. Other options are not valid."
}
```

---

### Question 3

```json
{
    "question": "A developer wants to group multiple agent runs under a single trace for a complex workflow. What is the recommended approach?",
    "options": [
        "Wrap the runs in a 'with trace()' context manager.",
        "Set trace_id manually for each run.",
        "Use group_id for each run.",
        "Call trace.start() and trace.finish() around each run."
    ],
    "correctAnswer": "Wrap the runs in a 'with trace()' context manager.",
    "explanation": "The 'Higher level traces' section recommends using 'with trace()' to group multiple runs. Manual start/finish is possible but less recommended."
}
```

---

### Question 4

```json
{
    "question": "Which property of a trace is used to link multiple traces from the same conversation, such as a chat thread?",
    "options": ["group_id", "trace_id", "workflow_name", "parent_id"],
    "correctAnswer": "group_id",
    "explanation": "'group_id' is for linking traces from the same conversation. 'trace_id' is unique per trace, 'workflow_name' is descriptive, 'parent_id' is for spans."
}
```

---

### Question 5

```json
{
    "question": "A financial services company operates under a Zero Data Retention (ZDR) policy. What is the impact on tracing?",
    "options": [
        "Tracing is unavailable.",
        "Tracing is available but limited.",
        "Only custom spans are allowed.",
        "Tracing is enabled by default."
    ],
    "correctAnswer": "Tracing is unavailable.",
    "explanation": "The note in the docs states: 'For organizations operating under a Zero Data Retention (ZDR) policy... tracing is unavailable.'"
}
```

---

### Question 6

```json
{
    "question": "Which of the following is NOT a default span type traced by the SDK?",
    "options": [
        "Database query span",
        "generation_span",
        "function_span",
        "guardrail_span"
    ],
    "correctAnswer": "Database query span",
    "explanation": "'Database query span' is not listed among default spans. The others are explicitly mentioned in 'Default tracing'."
}
```

---

### Question 7

```json
{
    "question": "A developer disables tracing for a single run by setting which configuration?",
    "options": [
        "RunConfig.tracing_disabled = True",
        "trace.disabled = True",
        "OPENAI_AGENTS_DISABLE_TRACING = 1",
        "Runner.disable_tracing = True"
    ],
    "correctAnswer": "RunConfig.tracing_disabled = True",
    "explanation": "Docs: 'You can disable tracing for a single run by setting RunConfig.tracing_disabled to True.' Other options are incorrect or global."
}
```

---

### Question 8

```json
{
    "question": "Scenario: You want to avoid storing sensitive LLM inputs/outputs in traces. Which RunConfig property should you adjust?",
    "options": [
        "trace_include_sensitive_data",
        "trace_sensitive_mode",
        "disable_sensitive_tracing",
        "trace_data_protection"
    ],
    "correctAnswer": "trace_include_sensitive_data",
    "explanation": "Docs: 'You can disable capturing that data via RunConfig.trace_include_sensitive_data.' Other options are not valid properties."
}
```

---

### Question 9

```json
{
    "question": "Which span property links a span to its parent in the trace hierarchy?",
    "options": ["parent_id", "group_id", "trace_id", "workflow_name"],
    "correctAnswer": "parent_id",
    "explanation": "'parent_id' points to the parent span. 'trace_id' links to the trace, 'group_id' is for traces, 'workflow_name' is descriptive."
}
```

---

### Question 10

```json
{
    "question": "A voice agent is configured to avoid storing base64-encoded PCM audio in traces. Which config is responsible?",
    "options": [
        "VoicePipelineConfig.trace_include_sensitive_audio_data",
        "RunConfig.trace_include_sensitive_data",
        "trace.audio_disabled",
        "AudioSpanConfig.sensitive_data"
    ],
    "correctAnswer": "VoicePipelineConfig.trace_include_sensitive_audio_data",
    "explanation": "Docs: 'You can disable capturing this audio data by configuring VoicePipelineConfig.trace_include_sensitive_audio_data.'"
}
```

---

### Question 11

```json
{
    "question": "Scenario: You want to send traces to both OpenAI and a third-party observability platform. Which method should you use?",
    "options": [
        "add_trace_processor()",
        "set_trace_processors()",
        "replace_trace_exporter()",
        "trace.add_export_destination()"
    ],
    "correctAnswer": "add_trace_processor()",
    "explanation": "'add_trace_processor()' adds an additional processor, sending traces to multiple destinations. 'set_trace_processors()' replaces all processors."
}
```

---

### Question 12

```json
{
    "question": "What is the main difference between 'add_trace_processor()' and 'set_trace_processors()'?",
    "options": [
        "add_trace_processor adds, set_trace_processors replaces all processors.",
        "add_trace_processor disables OpenAI export, set_trace_processors enables it.",
        "add_trace_processor is deprecated.",
        "set_trace_processors only works with custom spans."
    ],
    "correctAnswer": "add_trace_processor adds, set_trace_processors replaces all processors.",
    "explanation": "Docs: 'add_trace_processor()' adds, 'set_trace_processors()' replaces. The other statements are incorrect."
}
```

---

### Question 13

```json
{
    "question": "Which of the following is TRUE about the 'trace()' function?",
    "options": [
        "It can be used as a context manager to automatically start and finish a trace.",
        "It only works for synchronous code.",
        "It must be manually started and finished.",
        "It cannot be nested."
    ],
    "correctAnswer": "It can be used as a context manager to automatically start and finish a trace.",
    "explanation": "Docs: 'use the trace as a context manager... will automatically start and end the trace.' Manual start/finish is optional."
}
```

---

### Question 14

```json
{
    "question": "Scenario: An agent run triggers multiple LLM generations and tool calls. How does the SDK ensure correct span nesting in traces?",
    "options": [
        "By tracking the current span via a Python contextvar.",
        "By using thread-local storage.",
        "By assigning unique trace_ids to each span.",
        "By requiring manual parent_id assignment."
    ],
    "correctAnswer": "By tracking the current span via a Python contextvar.",
    "explanation": "Docs: 'The current trace is tracked via a Python contextvar... works with concurrency automatically.'"
}
```

---

### Question 15

```json
{
    "question": "Which of the following is NOT a property of a trace?",
    "options": ["parent_id", "workflow_name", "trace_id", "group_id"],
    "correctAnswer": "parent_id",
    "explanation": "'parent_id' is a span property, not a trace property. The others are listed under 'Traces and spans'."
}
```

---

### Question 16

```json
{
    "question": "A developer wants to process traces before they are sent to the backend. Which component should they customize?",
    "options": [
        "TraceProcessor",
        "TraceProvider",
        "SpanData",
        "TraceContextVar"
    ],
    "correctAnswer": "TraceProcessor",
    "explanation": "Docs: 'add_trace_processor() lets you add an additional trace processor...' TraceProvider creates traces, SpanData is for span info."
}
```

---

### Question 17

```json
{
    "question": "Scenario: You want to replace the default trace exporter with your own, preventing traces from being sent to OpenAI. What should you do?",
    "options": [
        "Use set_trace_processors() with your custom processor.",
        "Call add_trace_processor() with your exporter.",
        "Set OPENAI_AGENTS_DISABLE_TRACING=1.",
        "Override the trace_id property."
    ],
    "correctAnswer": "Use set_trace_processors() with your custom processor.",
    "explanation": "Docs: 'set_trace_processors() lets you replace the default processors...' This prevents traces from being sent to OpenAI unless you include their exporter."
}
```

---

### Question 18

```json
{
    "question": "Which of the following is a best practice for handling traces in concurrent agent workflows?",
    "options": [
        "Rely on contextvars to manage current trace and span.",
        "Manually pass trace_id to every function.",
        "Avoid using traces in async code.",
        "Use global variables to store trace state."
    ],
    "correctAnswer": "Rely on contextvars to manage current trace and span.",
    "explanation": "Docs: 'The current trace is tracked via a Python contextvar... works with concurrency automatically.' Manual passing/global vars are discouraged."
}
```

---

### Question 19

```json
{
    "question": "Which of the following is NOT a listed external tracing processor integration?",
    "options": [
        "TensorBoard",
        "Weights & Biases",
        "LangSmith",
        "Arize-Phoenix"
    ],
    "correctAnswer": "TensorBoard",
    "explanation": "'TensorBoard' is not listed in the 'External tracing processors list'. The others are present."
}
```

---

### Question 20

```json
{
    "question": "Scenario: You want to track a custom event in your workflow that is not covered by default spans. What should you use?",
    "options": [
        "custom_span()",
        "trace_id",
        "guardrail_span()",
        "function_span()"
    ],
    "correctAnswer": "custom_span()",
    "explanation": "Docs: 'A custom_span() function is available for tracking custom span information.' Other spans are for specific events."
}
```

---

### Question 21

```json
{
    "question": "What is the recommended way to ensure a trace is properly started and finished in your code?",
    "options": [
        "Use the trace() function as a context manager.",
        "Call trace.start() only.",
        "Set trace_id manually.",
        "Use a try/except block around trace() calls."
    ],
    "correctAnswer": "Use the trace() function as a context manager.",
    "explanation": "Docs: 'Recommended: use the trace as a context manager...' This ensures proper start/finish. Manual start/finish is less safe."
}
```

---

### Question 22

```json
{
    "question": "Which of the following best describes a 'span' in the context of tracing?",
    "options": [
        "An operation with a start and end time, nested within a trace.",
        "A unique identifier for a workflow.",
        "A group of related traces.",
        "A configuration for disabling tracing."
    ],
    "correctAnswer": "An operation with a start and end time, nested within a trace.",
    "explanation": "Docs: 'Spans represent operations that have a start and end time.' Other options confuse trace, group, or config concepts."
}
```

---
