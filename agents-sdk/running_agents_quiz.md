# Advanced Quiz: Running Agents in Production Systems

## Step 1: Real-World Use Cases

1. **Conversational AI with Multi-Turn Context**: Managing chat threads and follow-up questions in customer support or digital assistants.
2. **Automated Workflow Orchestration**: Running complex, multi-step processes with handoffs, tool calls, and streaming outputs.
3. **Compliance and Audit Logging**: Ensuring traceability, sensitive data handling, and exception management in regulated industries.
4. **Real-Time Data Processing**: Using streaming and event-driven agent runs for live analytics or monitoring.
5. **Robust Error Handling in Production**: Managing exceptions, guardrail triggers, and model errors in mission-critical applications.

---

## Scenario-Based, Multi-Step Questions

### **Scenario 1: Conversational AI with Multi-Turn Context**

#### **Q1.1**

You are building a customer support chatbot that must maintain context across multiple user turns. After the first agent run, you want to ensure the next user message is processed with full context. What is the best way to prepare the input for the next turn?

A. Pass only the latest user message as input to the next run  
B. Use `RunResultBase.to_input_list()` to get the full input history and append the new user message  
C. Start a new agent run with an empty input list  
D. Store all previous outputs in a global variable and pass it to the agent

#### **Q1.2**

If you want to trace the entire conversation, including all agent runs and handoffs, and group them under a single workflow, which configuration should you use?

A. Set `workflow_name` and `group_id` in the `run_config` and use a tracing context  
B. Only set `workflow_name` in the `run_config`  
C. Use default tracing settings  
D. Set `trace_include_sensitive_data` to `True` only

---

### **Scenario 2: Automated Workflow Orchestration**

#### **Q2.1**

You are orchestrating a multi-step workflow where the agent may call tools, perform handoffs, and produce a final output. What is the correct sequence of events in the agent loop?

A. LLM call → tool call → handoff → final output  
B. LLM call → if final output, return; if handoff, update agent and input and rerun; if tool call, run tool, append result, and rerun  
C. Tool call → LLM call → handoff → final output  
D. LLM call → always return final output

#### **Q2.2**

If the agent exceeds the maximum allowed turns during a run, what exception is raised?

A. `AgentsException`  
B. `MaxTurnsExceeded`  
C. `ModelBehaviorError`  
D. `UserError`

---

### **Scenario 3: Compliance and Audit Logging**

#### **Q3.1**

You are running agents in a regulated environment and need to ensure that traces do not include sensitive data. Which `run_config` parameter should you set?

A. `tracing_disabled=True`  
B. `trace_include_sensitive_data=False`  
C. `workflow_name='SensitiveWorkflow'`  
D. `model_settings={'temperature': 0}`

#### **Q3.2**

You want to link traces across multiple related agent runs for a single business process. Which parameter should you use?

A. `trace_id`  
B. `group_id`  
C. `model_provider`  
D. `handoff_input_filter`

---

### **Scenario 4: Real-Time Data Processing**

#### **Q4.1**

You are building a real-time analytics dashboard that must display agent outputs as soon as they are available. Which runner method should you use?

A. `Runner.run()`  
B. `Runner.run_sync()`  
C. `Runner.run_streamed()`  
D. `Runner.run_batch()`

#### **Q4.2**

After a streaming run, how can you access the sequence of streaming events for further processing?

A. Use the `.stream_events()` method on the `RunResultStreaming` object  
B. Use `.final_output` on the `RunResultStreaming` object  
C. Use `.to_input_list()` on the agent  
D. Use `.run_sync()` on the runner

---

### **Scenario 5: Robust Error Handling in Production**

#### **Q5.1**

During a run, the model produces malformed JSON or tries to use a non-existent tool. What exception is raised?

A. `AgentsException`  
B. `MaxTurnsExceeded`  
C. `ModelBehaviorError`  
D. `UserError`

#### **Q5.2**

A guardrail is tripped during input validation. What exception is raised?

A. `InputGuardrailTripwireTriggered`  
B. `OutputGuardrailTripwireTriggered`  
C. `ModelBehaviorError`  
D. `AgentsException`

---

### **Scenario 6: Advanced Workflow and Exception Management**

#### **Q6.1**

You are running a workflow where the agent must use a specific model and override all agent-level model settings for this run. Which `run_config` parameters should you set?

A. Only `model`  
B. `model` and `model_settings`  
C. Only `model_settings`  
D. `model_provider` and `trace_id`

#### **Q6.2**

You want to apply a global input filter to all handoffs in a workflow, unless a handoff already has its own filter. Which parameter do you use?

A. `handoff_input_filter`  
B. `input_guardrails`  
C. `output_guardrails`  
D. `trace_metadata`

---

### **Scenario 7: Streaming, Tracing, and Sensitive Data**

#### **Q7.1**

You are running a streamed agent session and want to ensure that traces include workflow and group information, but exclude sensitive data. Which combination of parameters should you set?

A. `workflow_name`, `group_id`, and `trace_include_sensitive_data=False`  
B. `workflow_name` and `trace_include_sensitive_data=True`  
C. `group_id` and `tracing_disabled=True`  
D. `trace_metadata` and `model_provider`

#### **Q7.2**

You want to add custom metadata to all traces for a run, such as user ID or session info. Which parameter do you use?

A. `trace_metadata`  
B. `workflow_name`  
C. `model_settings`  
D. `input_guardrails`

---

## Answer Key with Explanations

**Q1.1**  
Correct Answer: B  
Explanation: Use `RunResultBase.to_input_list()` to get the full input history and append the new user message, ensuring context is preserved across turns. A and C lose context; D is not the recommended pattern.

**Q1.2**  
Correct Answer: A  
Explanation: Setting both `workflow_name` and `group_id` in `run_config` and using a tracing context groups all related traces under a single workflow. B only partially groups; C and D do not provide full trace grouping.

**Q2.1**  
Correct Answer: B  
Explanation: The agent loop is: LLM call → if final output, return; if handoff, update agent and input and rerun; if tool call, run tool, append result, and rerun. This matches the described loop in the docs.

**Q2.2**  
Correct Answer: B  
Explanation: `MaxTurnsExceeded` is raised when the agent exceeds the allowed number of turns.

**Q3.1**  
Correct Answer: B  
Explanation: Setting `trace_include_sensitive_data=False` ensures sensitive data is not included in traces. A disables tracing entirely, which is not the goal.

**Q3.2**  
Correct Answer: B  
Explanation: `group_id` links traces across multiple runs for a single business process. `trace_id` is for a single run.

**Q4.1**  
Correct Answer: C  
Explanation: `Runner.run_streamed()` is used for streaming outputs as they are available.

**Q4.2**  
Correct Answer: A  
Explanation: `.stream_events()` on the `RunResultStreaming` object provides the sequence of streaming events.

**Q5.1**  
Correct Answer: C  
Explanation: `ModelBehaviorError` is raised for malformed outputs or non-existent tool calls.

**Q5.2**  
Correct Answer: A  
Explanation: `InputGuardrailTripwireTriggered` is raised when an input guardrail is tripped.

**Q6.1**  
Correct Answer: B  
Explanation: Both `model` and `model_settings` in `run_config` allow you to override agent-level settings for the run.

**Q6.2**  
Correct Answer: A  
Explanation: `handoff_input_filter` applies a global input filter to all handoffs unless a handoff already has its own filter.

**Q7.1**  
Correct Answer: A  
Explanation: Setting `workflow_name`, `group_id`, and `trace_include_sensitive_data=False` ensures traces are grouped and sensitive data is excluded.

**Q7.2**  
Correct Answer: A  
Explanation: `trace_metadata` allows you to add custom metadata to all traces for a run.

---

# End of Quiz
