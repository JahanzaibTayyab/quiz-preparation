# Guardrails Quiz

Below are 18 professional-level questions on guardrails in the OpenAI Agents SDK, covering concepts, implementation, and best practices.

---

## Questions

### Question 1

```json
{
    "question": "What is the primary purpose of guardrails in the OpenAI Agents SDK?",
    "options": [
        "To speed up LLM responses.",
        "To run checks and validations of user input or agent output in parallel to agents.",
        "To serialize agent output.",
        "To replace agent instructions."
    ],
    "correctAnswer": "To run checks and validations of user input or agent output in parallel to agents.",
    "explanation": "Guardrails run in parallel to agents to validate input/output, as described in the introduction."
}
```

---

### Question 2

```json
{
    "question": "Which of the following best describes an input guardrail?",
    "options": [
        "It only runs after all agents have finished.",
        "It runs on the initial user input before the agent processes it.",
        "It modifies the agent's instructions.",
        "It runs on the final agent output."
    ],
    "correctAnswer": "It runs on the initial user input before the agent processes it.",
    "explanation": "Input guardrails validate the initial user input, as described in the 'Input guardrails' section."
}
```

---

### Question 3

```json
{
    "question": "Which exception is raised if an input guardrail's tripwire is triggered?",
    "options": [
        "InputGuardrailResultException",
        "InputGuardrailTripwireTriggered",
        "GuardrailFunctionOutputException",
        "OutputGuardrailTripwireTriggered"
    ],
    "correctAnswer": "InputGuardrailTripwireTriggered",
    "explanation": "Docs: 'If true, an InputGuardrailTripwireTriggered exception is raised...'"
}
```

---

### Question 4

```json
{
    "question": "A company wants to prevent users from submitting math homework questions to an expensive LLM agent. What is the most cost-effective way to implement this?",
    "options": [
        "Add a warning in the agent instructions.",
        "Use a fast/cheap model as an input guardrail to detect and block such questions before the main agent runs.",
        "Disable the agent for all math-related queries.",
        "Rely on output guardrails only."
    ],
    "correctAnswer": "Use a fast/cheap model as an input guardrail to detect and block such questions before the main agent runs.",
    "explanation": "Input guardrails can block malicious or unwanted input before the expensive agent runs, saving cost."
}
```

---

### Question 5

```json
{
    "question": "Which of the following is TRUE about output guardrails?",
    "options": [
        "They only run if the agent is the first agent.",
        "They run on the final agent output and can raise OutputGuardrailTripwireTriggered.",
        "They modify the agent's instructions.",
        "They run before the agent receives input."
    ],
    "correctAnswer": "They run on the final agent output and can raise OutputGuardrailTripwireTriggered.",
    "explanation": "Output guardrails validate the final output and can raise the specified exception."
}
```

---

### Question 6

```json
{
    "question": "What is a tripwire in the context of guardrails?",
    "options": [
        "A way to speed up guardrail checks.",
        "A signal that immediately raises an exception and halts agent execution if a guardrail fails.",
        "A type of agent output.",
        "A method for serializing input."
    ],
    "correctAnswer": "A signal that immediately raises an exception and halts agent execution if a guardrail fails.",
    "explanation": "Docs: 'the Guardrail can signal this with a tripwire... immediately raise ... and halt the Agent execution.'"
}
```

---

### Question 7

```json
{
    "question": "Which of the following is NOT a step in the input guardrail process?",
    "options": [
        "The guardrail modifies the agent's instructions.",
        "The guardrail receives the same input passed to the agent.",
        "We check if .tripwire_triggered is true.",
        "The guardrail function runs to produce a GuardrailFunctionOutput."
    ],
    "correctAnswer": "The guardrail modifies the agent's instructions.",
    "explanation": "Input guardrails do not modify agent instructions; they validate input and may raise exceptions."
}
```

---

### Question 8

```json
{
    "question": "Why are guardrails typically defined on the agent rather than passed to Runner.run?",
    "options": [
        "Because guardrails are only for output.",
        "Because guardrails must be global.",
        "Because guardrails tend to be related to the actual Agent, and colocating the code improves readability.",
        "Because Runner.run does not support guardrails."
    ],
    "correctAnswer": "Because guardrails tend to be related to the actual Agent, and colocating the code improves readability.",
    "explanation": "Docs: 'colocating the code is useful for readability.' Guardrails are agent-specific."
}
```

---

### Question 9

```json
{
    "question": "Which of the following is required in a guardrail function?",
    "options": [
        "It must call the LLM directly.",
        "It must return a GuardrailFunctionOutput object.",
        "It must raise an exception directly.",
        "It must modify the agent's output."
    ],
    "correctAnswer": "It must return a GuardrailFunctionOutput object.",
    "explanation": "Docs: 'returns a GuardrailFunctionOutput'. Raising exceptions is handled by the framework."
}
```

---

### Question 10

```json
{
    "question": "A developer implements an input guardrail that always returns tripwire_triggered = false. What is the effect?",
    "options": [
        "The guardrail will never block any input, and the agent will always run.",
        "The agent will always raise InputGuardrailTripwireTriggered.",
        "The agent will not run at all.",
        "The guardrail will block all input."
    ],
    "correctAnswer": "The guardrail will never block any input, and the agent will always run.",
    "explanation": "If tripwire_triggered is never true, the guardrail never blocks input."
}
```

---

### Question 11

```json
{
    "question": "Which output property of GuardrailFunctionOutput determines if a tripwire is triggered?",
    "options": [
        "output_info",
        "tripwire_triggered",
        "result.final_output",
        "output_type"
    ],
    "correctAnswer": "tripwire_triggered",
    "explanation": "Docs: 'we check if .tripwire_triggered is true.' This property determines if the exception is raised."
}
```

---

### Question 12

```json
{
    "question": "A team wants to add a guardrail that checks if the agent's output contains any math. Where should this guardrail be attached?",
    "options": [
        "As an input guardrail on the agent.",
        "As a global guardrail.",
        "As an output guardrail on the agent.",
        "As a lifecycle hook."
    ],
    "correctAnswer": "As an output guardrail on the agent.",
    "explanation": "Output guardrails validate the final output, such as checking for math content."
}
```

---

### Question 13

```json
{
    "question": "Which of the following is TRUE about tripwires in guardrails?",
    "options": [
        "They only log a warning.",
        "They immediately halt agent execution when triggered.",
        "They modify the agent's instructions.",
        "They are only available for input guardrails."
    ],
    "correctAnswer": "They immediately halt agent execution when triggered.",
    "explanation": "Tripwires raise exceptions and halt execution, as described in the 'Tripwires' section."
}
```

---

### Question 14

```json
{
    "question": "A developer wants to include extra information in the guardrail result for debugging. Where should this information be placed?",
    "options": [
        "In the output_info field of GuardrailFunctionOutput.",
        "In the exception message.",
        "In the agent's instructions.",
        "In the tripwire_triggered field."
    ],
    "correctAnswer": "In the output_info field of GuardrailFunctionOutput.",
    "explanation": "Docs: 'We can include extra information in the guardrail result.' This is placed in output_info."
}
```

---

### Question 15

```json
{
    "question": "A customer support agent uses both input and output guardrails. If the input guardrail triggers, what happens?",
    "options": [
        "The agent run is halted before the main agent logic executes.",
        "The agent's instructions are modified.",
        "The output guardrail is still checked.",
        "The agent continues as normal."
    ],
    "correctAnswer": "The agent run is halted before the main agent logic executes.",
    "explanation": "Input guardrails can block execution before the agent runs, saving resources."
}
```

---

### Question 16

```json
{
    "question": "A developer implements a guardrail function that calls another agent under the hood to check for policy violations. What is a best practice for returning the result?",
    "options": [
        "Return a GuardrailFunctionOutput with output_info set to the result and tripwire_triggered set appropriately.",
        "Modify the agent's output directly.",
        "Return only a boolean value.",
        "Raise an exception directly in the guardrail function."
    ],
    "correctAnswer": "Return a GuardrailFunctionOutput with output_info set to the result and tripwire_triggered set appropriately.",
    "explanation": "The guardrail function should return a GuardrailFunctionOutput, not raise exceptions or modify output directly."
}
```

---

### Question 17

```json
{
    "question": "A company wants to use different guardrails for different agents in a multi-agent workflow. What is the recommended approach?",
    "options": [
        "Attach guardrails to each agent individually, colocating the code for readability.",
        "Use only output guardrails.",
        "Pass guardrails to Runner.run for each call.",
        "Define all guardrails globally and share them across agents."
    ],
    "correctAnswer": "Attach guardrails to each agent individually, colocating the code for readability.",
    "explanation": "Docs: 'colocating the code is useful for readability.' Guardrails are agent-specific."
}
```

---

### Question 18

```json
{
    "question": "A developer notices that their output guardrail is not being triggered even when the agent output should fail the check. What is the most likely cause?",
    "options": [
        "The guardrail function is not correctly setting tripwire_triggered to true when the condition is met.",
        "The agent is not using any guardrails.",
        "The guardrail is attached as an input guardrail instead of output.",
        "The agent's output_type is not set."
    ],
    "correctAnswer": "The guardrail function is not correctly setting tripwire_triggered to true when the condition is met.",
    "explanation": "If tripwire_triggered is not set to true, the guardrail will not trigger even if the condition is met."
}
```

---
