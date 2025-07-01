# Advanced Quiz: Real-World Application of Agents in LLM-Oriented Systems

## Step 1: Real-World Use Cases

1. **Enterprise Workflow Automation**: Designing modular agents to automate complex business processes, integrating with internal tools and APIs.
2. **Customer Service Orchestration**: Building multi-agent systems that triage, delegate, and resolve customer queries using specialized sub-agents and dynamic context.
3. **Compliance and Data Validation**: Implementing guardrails and structured outputs to ensure regulatory compliance and data integrity in sensitive domains.
4. **Personalized Digital Assistants**: Creating agents that adapt instructions and behaviors dynamically based on user context and preferences.
5. **AI-Driven Research and Analysis**: Using agents to extract, structure, and validate information from unstructured data sources for decision support.

---

## Scenario-Based, Multi-Step Questions

### **Scenario 1: Enterprise Workflow Automation**

#### **Q1.1**

You are tasked with automating a multi-step HR onboarding process using agents. The process requires fetching user data, validating compliance documents, and scheduling orientation. You want to ensure each step is handled by a specialized agent, and the main agent delegates tasks as needed. Which configuration best supports this requirement?

A. Use a single agent with all tools and no handoffs.  
B. Use a main agent with specialized agents as handoffs, each handling a specific step.  
C. Use multiple agents, each with identical instructions and tools.  
D. Use a main agent with dynamic instructions but no handoffs.

#### **Q1.2**

During implementation, you notice that after a tool is called, the agent continues to process the output with the LLM, sometimes leading to unnecessary follow-up actions. You want the agent to stop after the first tool call and use its output as the final response. What should you configure?

A. Set `ModelSettings.tool_choice` to `"required"`  
B. Set `Agent.tool_use_behavior` to `"stop_on_first_tool"`  
C. Remove all tools from the agent  
D. Set `ModelSettings.tool_choice` to `"none"`

---

### **Scenario 2: Customer Service Orchestration**

#### **Q2.1**

A customer service triage agent must decide whether to handle a request itself or delegate to a booking or refund agent. The triage agent uses dynamic instructions based on user context. What is the most robust way to provide user-specific data to all agents and tools involved in the run?

A. Pass user data as global variables  
B. Use the context object, passed to `Runner.run()`, accessible by all agents and tools  
C. Hardcode user data in each agent's instructions  
D. Use environment variables for user data

#### **Q2.2**

Suppose the triage agent's dynamic instructions function needs to access both the agent instance and the current context. Which function signature is correct for this use case?

A. `def dynamic_instructions(agent, context): ...`  
B. `def dynamic_instructions(context, agent): ...`  
C. `def dynamic_instructions(user_id): ...`  
D. `def dynamic_instructions(): ...`

---

### **Scenario 3: Compliance and Data Validation**

#### **Q3.1**

You are building an agent for a financial institution that must ensure all user inputs are relevant and compliant before processing. What is the best way to implement this validation in parallel with agent execution?

A. Use guardrails to screen input before agent processing  
B. Add validation logic inside the agent's instructions  
C. Only validate after the agent produces an output  
D. Rely on the LLM to detect non-compliance

#### **Q3.2**

If you want the agent to output structured data (e.g., a validated transaction record), which configuration should you use?

A. Set `output_type` to a Pydantic model representing the record  
B. Set `output_type` to `str`  
C. Use a plain dictionary as output  
D. Only specify the structure in the instructions

---

### **Scenario 4: Personalized Digital Assistants**

#### **Q4.1**

You are developing a digital assistant that adapts its instructions based on the user's subscription status and recent activity. Which approach best supports this requirement?

A. Use static instructions defined at agent creation  
B. Use dynamic instructions as a function of context and agent  
C. Use a different agent for each user  
D. Store user data in a global variable

#### **Q4.2**

If you want to create a new agent with the same configuration as an existing one but with a different persona, what is the most efficient method?

A. Manually copy all properties to a new agent  
B. Use the `clone()` method and override necessary properties  
C. Modify the existing agent in place  
D. Create a subclass of the agent

---

### **Scenario 5: AI-Driven Research and Analysis**

#### **Q5.1**

You are building an agent to extract structured events from unstructured text. To ensure the output is always a valid event object, which agent property should you configure?

A. `output_type`  
B. `tools`  
C. `handoffs`  
D. `hooks`

#### **Q5.2**

During a run, you want to observe and log when the agent starts and finishes processing. What is the best way to achieve this?

A. Subclass `AgentHooks` and override relevant methods  
B. Add print statements to the agent's instructions  
C. Use guardrails for logging  
D. Modify the LLM model settings

---

### **Scenario 6: Multi-Domain Virtual Assistant for Healthcare**

#### **Q6.1**

You are designing a virtual healthcare assistant that must:

-   Triage patient symptoms
-   Book appointments
-   Provide medication reminders
-   Escalate urgent cases to a human doctor

The assistant must use dynamic instructions based on patient history, enforce strict output types for medical records, and log every escalation event. Which combination of features is most appropriate?

A. Use static instructions, plain string outputs, and no hooks
B. Use dynamic instructions, Pydantic output types, and AgentHooks for logging
C. Use only handoffs and tools, with no structured outputs
D. Use guardrails for logging and static instructions

#### **Q6.2**

A patient's input triggers both a guardrail (for compliance) and a handoff (to the escalation agent). The escalation agent must stop after the first tool call and return the result directly. What configuration ensures this behavior?

A. Set `tool_use_behavior` to `stop_on_first_tool` for the escalation agent
B. Set `tool_choice` to `auto` for the escalation agent
C. Remove all tools from the escalation agent
D. Only use guardrails, not handoffs

---

### **Scenario 7: Regulatory Reporting Automation in Finance**

#### **Q7.1**

You are building an agent system to automate regulatory reporting for a bank. The system must:

-   Aggregate data from multiple sources using tools
-   Validate all data for compliance using guardrails
-   Output structured reports as Pydantic models
-   Clone the reporting agent for different regulatory jurisdictions, each with slightly different instructions

Which approach best meets these requirements?

A. Use a single agent with static instructions and plain text output
B. Use an agent with tools, guardrails, Pydantic output_type, and clone for each jurisdiction with custom instructions
C. Use only tools and handoffs, no output_type or guardrails
D. Use dynamic instructions but no cloning

#### **Q7.2**

During a run, a cloned agent for the EU jurisdiction encounters a data validation error. What is the best way to ensure this error is logged and the run is halted?

A. Use AgentHooks to log the error and raise an exception in the guardrail
B. Ignore the error and continue processing
C. Only log the error in the output
D. Remove guardrails for cloned agents

---

### **Scenario 8: Research Team Collaboration Platform**

#### **Q8.1**

A research platform uses agents to:

-   Summarize documents
-   Extract structured references
-   Route complex queries to specialized sub-agents (handoffs)
-   Enforce that all outputs are validated and logged

A user submits a query that requires both summarization and reference extraction, and the system must ensure the output is a valid structured object. What is the best configuration?

A. Use a single agent with plain string output
B. Use an agent with handoffs, Pydantic output_type, and hooks for logging
C. Use only tools, no handoffs or output_type
D. Use static instructions and no validation

#### **Q8.2**

The platform wants to allow users to customize the agent's behavior for their team, such as changing the summarization style or reference format, without affecting other teams. What is the most scalable approach?

A. Clone the base agent for each team and override instructions/output_type as needed
B. Modify the base agent in place for each team
C. Use global variables to store team preferences
D. Only allow changes via environment variables

---

### **Scenario 9: Autonomous Multi-Agent Scientific Discovery Platform**

#### **Q9.1**

You are building a scientific discovery platform where agents collaborate to:

-   Generate hypotheses from literature
-   Design experiments
-   Validate results using external data sources
-   Log all actions and errors for auditability

The system must support dynamic context sharing between agents, robust error handling, and structured outputs for experiment results. What is the best configuration?

A. Use a single agent with static instructions and plain string output
B. Use multiple agents with dynamic context, Pydantic output_type, AgentHooks for logging, and error propagation between agents
C. Use only tools and no structured outputs or logging
D. Use handoffs but no context sharing or error handling

#### **Q9.2**

During an experiment, the validation agent detects a critical error in the results. What is the most robust way to ensure this error is both logged and causes the experiment run to halt?

A. Use AgentHooks to log the error and raise an exception in the validation agent
B. Only log the error in the output
C. Ignore the error and continue with the next experiment
D. Remove error handling from the validation agent

---

### **Scenario 10: Global Customer Support System with Multilingual and Compliance Requirements**

#### **Q10.1**

You are designing a global customer support system where agents must:

-   Handle queries in multiple languages
-   Enforce region-specific compliance guardrails
-   Escalate complex cases to regional managers
-   Allow for easy updates to instructions and compliance logic per region

What is the most scalable and robust approach?

A. Use a single agent with static instructions and no compliance guardrails
B. Clone the base agent for each region/language, override instructions and guardrails, and use handoffs for escalation
C. Use only tools and no region-specific logic
D. Use global variables for compliance logic

#### **Q10.2**

A compliance violation is detected by the EU agent, but you want to ensure this does not affect agents in other regions. What is the best way to isolate and log such events?

A. Use cloned agents per region, each with its own guardrails and AgentHooks for logging
B. Use a single agent and log all violations globally
C. Ignore violations in non-EU regions
D. Remove guardrails from non-EU agents

---

# Answer Key with Explanations

**Q1.1**  
Correct Answer: B  
Explanation: B is correct because handoffs allow the main agent to delegate tasks to specialized sub-agents, each optimized for a specific step (fetching data, validating documents, scheduling). A and D lack modularity and delegation. C duplicates effort and lacks orchestration.

**Q1.2**  
Correct Answer: B  
Explanation: B is correct; setting `tool_use_behavior` to `"stop_on_first_tool"` ensures the agent stops after the first tool call. A only forces tool use but does not stop further processing. C disables tool use entirely. D prevents tool use, which is not the goal.

**Q2.1**  
Correct Answer: B  
Explanation: B is correct; the context object is designed for dependency injection and is accessible throughout the agent run. A and D are not scalable or secure. C is inflexible and not dynamic.

**Q2.2**  
Correct Answer: B  
Explanation: B is correct; the function receives the context (as `RunContextWrapper[UserContext]`) and the agent instance, in that order. A has the wrong parameter order. C and D lack required parameters.

**Q3.1**  
Correct Answer: A  
Explanation: A is correct; guardrails run checks/validations in parallel to agent execution, ensuring compliance before processing. B and D are unreliable. C is too late for input validation.

**Q3.2**  
Correct Answer: A  
Explanation: A is correct; setting `output_type` to a Pydantic model enables structured outputs and validation. B and C do not enforce structure. D is insufficient for structured output enforcement.

**Q4.1**  
Correct Answer: B  
Explanation: B is correct; dynamic instructions allow the agent to adapt prompts based on context and agent state. A and D lack flexibility. C is inefficient and unscalable.

**Q4.2**  
Correct Answer: B  
Explanation: B is correct; `clone()` allows you to duplicate and modify only the desired properties. A is error-prone. C changes the original agent, which may not be desired. D is unnecessary for simple property changes.

**Q5.1**  
Correct Answer: A  
Explanation: A is correct; `output_type` enforces structured output, such as a Pydantic model. B, C, and D do not control output structure.

**Q5.2**  
Correct Answer: A  
Explanation: A is correct; `AgentHooks` allows you to observe lifecycle events. B is not robust. C is for validation, not logging. D does not provide lifecycle hooks.

**Q6.1**  
Correct Answer: B  
Explanation: B is correct; dynamic instructions allow the agent to adapt to patient history, Pydantic output types enforce structured medical records, and AgentHooks enable logging of escalation events. A, C, and D lack one or more required features.

**Q6.2**  
Correct Answer: A  
Explanation: A is correct; setting `tool_use_behavior` to `stop_on_first_tool` ensures the escalation agent stops after the first tool call and returns the result directly. B does not enforce stopping. C disables tool use. D omits handoffs, which are required.

**Q7.1**  
Correct Answer: B  
Explanation: B is correct; this approach uses tools for aggregation, guardrails for validation, Pydantic output_type for structured reports, and cloning for jurisdiction-specific customization. A, C, and D lack one or more required features.

**Q7.2**  
Correct Answer: A  
Explanation: A is correct; AgentHooks can log the error, and raising an exception in the guardrail halts the run. B ignores the error, C only logs without halting, and D removes necessary validation.

**Q8.1**  
Correct Answer: B  
Explanation: B is correct; handoffs allow routing, Pydantic output_type enforces structure, and hooks enable logging. A, C, and D lack one or more required features.

**Q8.2**  
Correct Answer: A  
Explanation: A is correct; cloning the base agent for each team allows scalable, isolated customization. B is not scalable, C and D are not robust or maintainable.

**Q9.1**  
Correct Answer: B  
Explanation: B is correct; using multiple agents with dynamic context, structured outputs, AgentHooks for logging, and error propagation supports collaboration, auditability, and robust error handling. A, C, and D lack one or more required features.

**Q9.2**  
Correct Answer: A  
Explanation: A is correct; AgentHooks can log the error, and raising an exception in the validation agent halts the experiment run. B only logs without halting, C ignores the error, and D removes error handling.

**Q10.1**  
Correct Answer: B  
Explanation: B is correct; cloning the base agent for each region/language allows for isolated customization, region-specific guardrails, and escalation logic. A, C, and D lack one or more required features.

**Q10.2**  
Correct Answer: A  
Explanation: A is correct; using cloned agents per region with their own guardrails and AgentHooks ensures violations are isolated and logged per region. B logs globally (not isolated), C ignores violations, and D removes necessary compliance checks.

---

# End of Quiz
