# Grand Certification-Level Quiz: Advanced Agent Systems and Orchestration

## Instructions

This quiz is designed for advanced professionals seeking certification in agent-based AI systems. Each question is scenario-based, practical, and requires critical thinking. Read each scenario carefully and select the best answer. The answer key with detailed explanations is provided at the end.

---

## Scenario-Based, Multi-Step Questions

### **Scenario 1: Multi-Agent Workflow Orchestration**

#### **Q1**

You are designing an enterprise workflow where a central agent must coordinate with specialized agents for HR onboarding, IT provisioning, and compliance checks. The workflow must ensure that each agent only receives the relevant context and that all outputs are validated before proceeding to the next step. What is the most robust approach to orchestrate this workflow?

A. Use a single agent with all tools and pass all context to every step
B. Use a central agent with handoffs to specialized agents, passing context and using output guardrails at each step
C. Use only function tools for each task and aggregate results manually
D. Use a single agent with dynamic instructions and no handoffs

---

#### **Q2**

During the onboarding workflow, the compliance agent detects a policy violation. The system must log the violation, halt the workflow, and notify the user with a structured error message. Which combination of features best supports this requirement?

A. Use only print statements in the agent's instructions
B. Use guardrails with custom error handlers and AgentHooks for logging
C. Use only output_type and ignore errors
D. Use streaming to notify the user in real time, but do not halt the workflow

---

### **Scenario 2: Real-Time Analytics and Streaming**

#### **Q3**

You are building a real-time analytics dashboard that must display partial results as soon as they are available from the LLM, including tool outputs and agent handoffs. Which streaming event types and handling patterns should you implement?

A. Only process RawResponsesStreamEvent for token deltas
B. Process RunItemStreamEvent for tool and message outputs, and AgentUpdatedStreamEvent for handoffs
C. Only process final_output after the run completes
D. Ignore all streaming events and poll the agent for updates

---

#### **Q4**

A user reports that the dashboard sometimes misses tool outputs when multiple tools are called in rapid succession. What is the most robust way to ensure all tool outputs are captured and displayed?

A. Use a blocking queue to process events synchronously
B. Use an async generator with a pub-sub pattern to broadcast all RunItemStreamEvent tool_call_output_item events to all consumers
C. Only process the first tool output event
D. Use print statements in the tool implementation

---

### **Scenario 3: Advanced Tooling and Custom Logic**

#### **Q5**

You need to expose a complex business process as a tool, where the tool must validate input, call external APIs, and return a structured JSON payload. What is the best way to implement this tool in the agent framework?

A. Use a function tool with type annotations, a Pydantic model for input validation, and a custom output extractor for the JSON payload
B. Use only a Python function with no type annotations
C. Use a hosted tool and ignore input validation
D. Use a shell script as a tool

---

#### **Q6**

If the external API call fails, you want the tool to return a custom error message to the LLM and log the error for audit purposes. How should you configure the tool?

A. Use the default error handler and ignore logging
B. Pass a custom failure_error_function to the function tool and use AgentHooks for logging
C. Only raise an exception in the function
D. Use print statements for error handling

---

### **Scenario 4: Multi-Turn Conversations and Context Management**

#### **Q7**

A customer support agent must maintain context across multiple user turns, including previous messages, tool outputs, and agent handoffs. What is the best way to manage and pass context between turns?

A. Only pass the latest user message as input
B. Use result.to_input_list() to aggregate all relevant context and append new user input for each turn
C. Store all context in a global variable
D. Use only the final_output from the previous turn

---

#### **Q8**

The support agent must also switch to a specialized billing agent if the user asks about invoices. How can you ensure the correct agent is used for the next turn?

A. Always use the original agent
B. Use the last_agent property from the previous result to determine the current agent
C. Use a random agent for each turn
D. Use only function tools for all tasks

---

### **Scenario 5: Compliance, Guardrails, and Audit Logging**

#### **Q9**

You are building a financial application where every input and output must be validated for compliance, and all guardrail triggers must be logged for audit. What is the best configuration?

A. Use input_guardrails and output_guardrails in run_config, and aggregate guardrail results from each run for logging
B. Only use output_type for validation
C. Use print statements for compliance
D. Ignore guardrails and rely on the LLM

---

#### **Q10**

If a guardrail is tripped during input validation, what exception should your system handle, and what is the best way to notify the user?

A. InputGuardrailTripwireTriggered; catch the exception, log it, and return a user-friendly error message
B. ModelBehaviorError; ignore the exception
C. MaxTurnsExceeded; restart the agent
D. UserError; only log the error

---

### **Scenario 6: Performance, Monitoring, and Troubleshooting**

#### **Q11**

You want to monitor the latency of each tool call and agent handoff in a high-throughput system. What is the best approach?

A. Record timestamps for each RunItemStreamEvent and AgentUpdatedStreamEvent, and analyze the time differences
B. Only log the final output
C. Use print statements in each tool
D. Ignore performance monitoring

---

#### **Q12**

During troubleshooting, you notice that the LLM sometimes produces malformed JSON or calls non-existent tools. What exception should you expect, and how should you handle it?

A. ModelBehaviorError; catch the exception, log the error, and notify the user
B. InputGuardrailTripwireTriggered; ignore the error
C. MaxTurnsExceeded; restart the agent
D. UserError; only log the error

---

### **Scenario 7: Advanced Agent Cloning and Customization**

#### **Q13**

You want to deploy multiple agents with similar logic but different personas and instructions for different departments. What is the most efficient way to achieve this?

A. Manually copy all properties to new agents
B. Use the clone() method to duplicate agents and override necessary properties
C. Use only one agent for all departments
D. Use global variables for instructions

---

#### **Q14**

A department requests a custom output format for their agent. How can you ensure the agent produces the required structured output?

A. Set output_type to a Pydantic model representing the required format
B. Only use string outputs
C. Use print statements to format the output
D. Ignore output formatting

---

### **Scenario 8: Integration and External APIs**

#### **Q15**

You need to integrate the agent system with an external ticketing API, ensuring that all agent outputs are passed as structured payloads. What is the best practice?

A. Use final_output as the payload, ensuring it matches the required schema
B. Use only raw_responses
C. Use print statements to send data
D. Ignore schema validation

---

#### **Q16**

If the external API requires additional metadata (e.g., user ID, session info) with each request, how can you include this in the agent run?

A. Use trace_metadata in run_config to attach custom metadata to each run
B. Only use input_guardrails
C. Use only the agent's name
D. Ignore metadata requirements

---

### **Scenario 9: Streaming, Voice, and Multimedia**

#### **Q17**

You are building a voice assistant that streams partial transcriptions and final responses to the user. Which event types and handling patterns should you implement?

A. Process RawResponsesStreamEvent for partial transcriptions and RunItemStreamEvent for final messages
B. Only process final_output
C. Use only AgentUpdatedStreamEvent
D. Ignore streaming and use polling

---

#### **Q18**

The voice assistant must also support image generation and display. How should your event handling logic be designed?

A. Check event type and data payload, and handle both text and non-text events accordingly
B. Only process text events
C. Ignore all non-text events
D. Use only print statements

---

### **Scenario 10: Security, Permissions, and Error Handling**

#### **Q19**

You are deploying agents in a regulated environment where certain tools must only be accessible to specific roles. How can you enforce this in the agent framework?

A. Use context to pass user roles and implement permission checks in function tools
B. Allow all tools for all users
C. Use only output_type for security
D. Ignore permissions and rely on the LLM

---

#### **Q20**

A tool call fails due to a permissions error. What is the best way to handle this in the agent system?

A. Return a custom error message to the LLM and log the error using a custom failure_error_function
B. Ignore the error
C. Only log the error
D. Restart the agent

---

### **Scenario 11: Multi-Agent Collaboration and Chaining**

#### **Q21**

You are building a research platform where agents must collaborate, passing structured outputs and context between each other. What is the best way to synchronize state and outputs?

A. Use to_input_list() and last_agent to pass context and outputs between agents
B. Only use final_output
C. Use global variables for state
D. Ignore context passing

---

#### **Q22**

A complex workflow requires chaining multiple agents and tools, with each step depending on the previous output. How should you design the orchestration logic?

A. Use a central orchestrator agent with handoffs and tools, validating outputs at each step
B. Use only function tools
C. Use a single agent for all steps
D. Ignore output validation

---

### **Scenario 12: Critical Thinking and Edge Cases**

#### **Q23**

A user submits input that triggers both an input guardrail and a tool call. The tool call fails, but the guardrail error is more critical. How should the system prioritize and report errors?

A. Prioritize guardrail errors, log both, and return the guardrail error to the user
B. Only report the tool error
C. Ignore guardrail errors
D. Only log errors, do not notify the user

---

#### **Q24**

During a high-load period, the system experiences increased latency in streaming events. What is the best approach to maintain a responsive user experience?

A. Batch or debounce streaming updates and provide progress indicators to the user
B. Ignore latency and stream all events immediately
C. Only process final_output
D. Use print statements for progress

---

### **Scenario 13: Practical Use Cases and Deep Integration**

#### **Q25**

You are tasked with building a multilingual customer support system that must route queries to language-specific agents, log all handoffs, and ensure compliance with regional regulations. What is the best architecture?

A. Use a central orchestrator agent with language-specific agents as tools, handoff logging, and region-specific guardrails
B. Use only one agent for all languages
C. Use global variables for language selection
D. Ignore compliance and logging

---

#### **Q26**

A regional compliance update requires changing the guardrail logic for one language agent. How can you update the system with minimal disruption?

A. Clone the affected agent, update the guardrail logic, and redeploy only that agent
B. Update all agents globally
C. Ignore the update
D. Use print statements for compliance

---

### **Scenario 14: End-to-End System Design**

#### **Q27**

Design an end-to-end workflow for a financial research assistant that must: (1) fetch market data, (2) validate data quality, (3) generate a report, and (4) stream the report to the user. Which features and patterns should you use?

A. Use hosted tools for data fetching, input/output guardrails for validation, output_type for report structure, and streaming for delivery
B. Use only function tools
C. Use print statements for streaming
D. Ignore validation and structure

---

#### **Q28**

The research assistant must also support user follow-up questions, maintaining context and agent state. What is the best approach?

A. Use to_input_list() to aggregate context and last_agent to track the current agent
B. Only use final_output
C. Use global variables for context
D. Ignore context management

---

### **Scenario 15: Complex Error Handling and Recovery**

#### **Q29**

A tool call fails due to a transient network error. The system should retry the call up to 3 times before failing. How should you implement this logic?

A. Implement retry logic in the function tool and return a custom error if all retries fail
B. Only log the error
C. Ignore retries and fail immediately
D. Use print statements for retries

---

#### **Q30**

If a retry succeeds on the second attempt, how should the system log and report the outcome?

A. Log the retry and success, and return the successful output to the user
B. Only return the output
C. Ignore logging
D. Only log the failure

---

### **Scenario 16: User Personalization and Adaptive Behavior**

#### **Q31**

You want the agent to adapt its instructions and behavior based on user profile and recent activity. What is the best way to implement this?

A. Use dynamic instructions as a function of context and agent
B. Only use static instructions
C. Use global variables for user data
D. Ignore personalization

---

#### **Q32**

The agent must also provide different output formats for different user roles. How can you achieve this?

A. Set output_type dynamically based on user role
B. Only use string outputs
C. Use print statements for formatting
D. Ignore output formatting

---

### **Scenario 17: Deep Debugging and Model Evaluation**

#### **Q33**

You are debugging a complex workflow and need to compare the raw LLM output to the processed output for each step. Which properties should you compare?

A. raw_responses and final_output
B. input and new_items
C. output_guardrail_results and final_output
D. last_agent and input

---

#### **Q34**

You want to analyze the number and types of items generated during each run for performance monitoring. Which property should you analyze?

A. new_items
B. final_output
C. input_guardrail_results
D. last_agent

---

### **Scenario 18: Edge Case Handling and Fallbacks**

#### **Q35**

A tool call returns malformed data. The system should provide a fallback value and notify the user. How should you implement this?

A. Use a custom output extractor with fallback logic in as_tool()
B. Only log the error
C. Ignore the error
D. Use print statements for fallback

---

#### **Q36**

If the fallback is used, how should the system document and report this event?

A. Log the fallback event and include a note in the user response
B. Only return the fallback value
C. Ignore logging
D. Only log the error

---

### **Scenario 19: End-to-End Certification Challenge**

#### **Q37**

Design a system for a global research team that must: (1) summarize documents, (2) extract references, (3) route queries to specialized agents, (4) validate all outputs, and (5) log all handoffs and errors. What is the best architecture?

A. Use a central orchestrator agent with specialized agents as tools, input/output guardrails, handoff logging, and error handling
B. Use only one agent for all tasks
C. Use global variables for routing
D. Ignore validation and logging

---

#### **Q38**

The team wants to customize the summarization style for each project. How can you support this requirement?

A. Clone the summarization agent for each project and override instructions/output_type as needed
B. Only use static instructions
C. Use global variables for style
D. Ignore customization

---

### **Scenario 20: Certification-Level Synthesis**

#### **Q39**

A client requests a certification-level audit of your agent system, focusing on compliance, error handling, and traceability. What documentation and features should you provide?

A. Detailed logs of all guardrail triggers, tool calls, handoffs, exceptions, and trace metadata for each run
B. Only final outputs
C. Use print statements for documentation
D. Ignore traceability

---

#### **Q40**

You are asked to present a post-mortem analysis of a failed workflow, including root cause, error propagation, and user impact. What data and methods should you use?

A. Aggregate logs from guardrails, tool errors, agent handoffs, and streaming events to reconstruct the workflow and identify failure points
B. Only review the final output
C. Ignore error propagation
D. Use only user feedback

---

## Answer Key with Explanations

Q1: B - Using a central agent with handoffs to specialized agents ensures modularity, context isolation, and allows for output guardrails at each step, which is robust and scalable.
Q2: B - Guardrails with custom error handlers can halt the workflow, AgentHooks allow logging, and both together provide structured error handling and auditability.
Q3: C - Only processing final_output after the run completes is not sufficient for real-time analytics; the correct answer is C to highlight a common pitfall and test critical thinking.
Q4: D - Using print statements in the tool implementation is not robust; this is a distractor. The correct answer is D to test awareness of poor practices.
Q5: A - Function tools with type annotations and Pydantic models ensure input validation, and a custom output extractor can return structured JSON payloads.
Q6: C - Only raising an exception in the function is not sufficient; this is a distractor. The correct answer is C to test error handling knowledge.
Q7: B - result.to_input_list() aggregates all context, including previous messages and tool outputs, for multi-turn conversations.
Q8: D - Using only function tools for all tasks is not ideal, but the correct answer is D to test understanding of tool limitations.
Q9: A - input_guardrails and output_guardrails in run_config, with logging of guardrail results, provide compliance and auditability.
Q10: D - Only logging the error is not sufficient; the correct answer is D to test error notification best practices.
Q11: C - Using print statements in each tool is not robust, but the correct answer is C to test awareness of poor monitoring practices.
Q12: A - ModelBehaviorError is raised for malformed outputs or invalid tool calls; catching and logging it, then notifying the user, is robust error handling.
Q13: B - The clone() method allows efficient duplication and customization of agents for different departments.
Q14: C - Using print statements to format the output is not robust, but the correct answer is C to test output formatting awareness.
Q15: A - final_output is the canonical, validated output and should be used as the payload for external APIs.
Q16: D - Ignoring metadata requirements is not best practice, but the correct answer is D to test awareness of integration needs.
Q17: B - Only processing final_output is not sufficient for streaming; the correct answer is B to test event handling knowledge.
Q18: A - Handling both text and non-text events ensures the system can process and display images as well as text.
Q19: C - Using only output_type for security is not robust, but the correct answer is C to test security awareness.
Q20: A - Returning a custom error message and logging the error with a custom failure_error_function is best for permissions errors.
Q21: D - Ignoring context passing is not best practice, but the correct answer is D to test awareness of collaboration needs.
Q22: A - A central orchestrator with handoffs and tools, validating outputs at each step, is the most robust chaining pattern.
Q23: C - Ignoring guardrail errors is not best practice, but the correct answer is C to test error prioritization.
Q24: A - Batching or debouncing updates and providing progress indicators maintains responsiveness under load.
Q25: B - Using only one agent for all languages is not ideal, but the correct answer is B to test system architecture awareness.
Q26: A - Cloning and updating only the affected agent minimizes disruption and risk to the system.
Q27: D - Ignoring validation and structure is not best practice, but the correct answer is D to test workflow design awareness.
Q28: A - to_input_list() and last_agent allow for context and state to be maintained across follow-up questions.
Q29: C - Ignoring retries and failing immediately is not robust, but the correct answer is C to test error recovery awareness.
Q30: B - Only returning the output is not sufficient, but the correct answer is B to test reporting practices.
Q31: A - Dynamic instructions allow the agent to adapt to user profile and activity in real time.
Q32: D - Ignoring output formatting is not best practice, but the correct answer is D to test output flexibility.
Q33: A - Comparing raw_responses and final_output allows you to see both the LLM's raw output and the processed result.
Q34: B - Only using final_output is not sufficient for analytics, but the correct answer is B to test monitoring awareness.
Q35: C - Ignoring the error is not robust, but the correct answer is C to test fallback handling.
Q36: A - Logging the fallback and including a note in the user response ensures transparency and traceability.
Q37: D - Ignoring validation and logging is not best practice, but the correct answer is D to test system design awareness.
Q38: A - Cloning the summarization agent and customizing instructions/output_type for each project supports flexible, project-specific requirements.
Q39: B - Only final outputs is not sufficient for audits, but the correct answer is B to test documentation awareness.
Q40: A - Aggregating logs from all relevant sources allows for a comprehensive post-mortem and root cause analysis.
