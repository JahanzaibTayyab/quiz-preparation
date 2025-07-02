# Multi-Agent Orchestration Quiz

Below are 15 professional-level questions on orchestrating multiple agents in the OpenAI Agents SDK, covering LLM-driven and code-driven orchestration, tradeoffs, best practices, and real-world scenarios.

---

## Questions

### Question 1

```json
{
    "question": "You are building a research assistant that can search the web, analyze data, and write reports. You want the agent to autonomously decide which tools and sub-agents to use for each step. Which orchestration pattern best fits this use case?",
    "options": [
        "Manual tool invocation only",
        "Orchestrating via code",
        "Chaining agents in a fixed order",
        "Orchestrating via LLM"
    ],
    "correctAnswer": "Orchestrating via LLM",
    "explanation": "LLM-driven orchestration lets the agent plan and decide which tools and handoffs to use for open-ended tasks."
}
```

---

### Question 2

```json
{
    "question": "Which of the following is a key advantage of orchestrating agents via code rather than via LLM?",
    "options": [
        "Greater flexibility for open-ended tasks",
        "Deterministic and predictable speed, cost, and performance",
        "Requires less monitoring and iteration",
        "Better at handling ambiguous user requests"
    ],
    "correctAnswer": "Deterministic and predictable speed, cost, and performance",
    "explanation": "Code-driven orchestration is more predictable and easier to control for cost and performance."
}
```

---

### Question 3

```json
{
    "question": "A product team wants to chain multiple agents so that the output of one becomes the input of the next (e.g., research → outline → draft → critique). Which orchestration pattern is this?",
    "options": [
        "Manual tool invocation",
        "Orchestrating via code",
        "Parallel agent execution",
        "Orchestrating via LLM"
    ],
    "correctAnswer": "Orchestrating via code",
    "explanation": "Chaining agents by transforming outputs to inputs is a code-driven orchestration pattern."
}
```

---

### Question 4

```json
{
    "question": "You want to run several agents in parallel to speed up processing, as their tasks are independent. Which Python primitive is recommended for this pattern?",
    "options": [
        "threading.Thread",
        "asyncio.gather",
        "multiprocessing.Pool",
        "time.sleep"
    ],
    "correctAnswer": "asyncio.gather",
    "explanation": "asyncio.gather is recommended for running multiple async agents in parallel."
}
```

---

### Question 5

```json
{
    "question": "A developer wants to let the LLM decide which specialized agent to hand off to, based on the user's request. What is a best practice for making this work reliably?",
    "options": [
        "Invest in good prompts that clearly describe available tools and handoffs",
        "Use only code-driven orchestration",
        "Rely on default agent instructions only",
        "Disable all handoffs and use a single agent"
    ],
    "correctAnswer": "Invest in good prompts that clearly describe available tools and handoffs",
    "explanation": "Clear prompts help the LLM make correct decisions about tool and agent usage."
}
```

---

### Question 6

```json
{
    "question": "Which of the following is a tradeoff of LLM-driven orchestration compared to code-driven orchestration?",
    "options": [
        "Cannot use handoffs",
        "Cannot use tools",
        "Less deterministic and potentially higher cost",
        "Cannot run agents in parallel"
    ],
    "correctAnswer": "Less deterministic and potentially higher cost",
    "explanation": "LLM-driven orchestration is flexible but less predictable and may be more expensive."
}
```

---

### Question 7

```json
{
    "question": "You want to improve your LLM-driven agent's performance over time. What is a recommended tactic?",
    "options": [
        "Monitor the app, iterate on prompts, and use evals to train and improve",
        "Disable all tools and handoffs",
        "Rely on static prompts only",
        "Use only code-driven orchestration"
    ],
    "correctAnswer": "Monitor the app, iterate on prompts, and use evals to train and improve",
    "explanation": "Continuous monitoring and prompt iteration are key to improving LLM-driven agents."
}
```

---

### Question 8

```json
{
    "question": "A workflow requires an agent to classify a task, then select the next agent based on the classification. Which orchestration pattern is this?",
    "options": [
        "Orchestrating via code with structured outputs",
        "Manual tool invocation",
        "Parallel agent execution",
        "Orchestrating via LLM"
    ],
    "correctAnswer": "Orchestrating via code with structured outputs",
    "explanation": "Structured outputs allow code to make routing decisions based on agent results."
}
```

---

### Question 9

```json
{
    "question": "You want to let an agent critique and improve its own output in a loop until a separate evaluator agent approves it. Which orchestration pattern is this?",
    "options": [
        "LLM-driven orchestration",
        "Manual tool invocation",
        "Code-driven orchestration with feedback loops",
        "Parallel agent execution"
    ],
    "correctAnswer": "Code-driven orchestration with feedback loops",
    "explanation": "Running agents in a loop with evaluators is a code-driven pattern."
}
```

---

### Question 10

```json
{
    "question": "A team wants to use specialized agents for research, writing, and editing, but wants the LLM to decide which agent to use at each step. What is a key best practice for this setup?",
    "options": [
        "Chain agents in a fixed order only",
        "Provide clear instructions and tool descriptions for each agent",
        "Disable all handoffs",
        "Use only code-driven orchestration"
    ],
    "correctAnswer": "Provide clear instructions and tool descriptions for each agent",
    "explanation": "Clear instructions help the LLM make correct decisions in multi-agent workflows."
}
```

---

### Question 11

```json
{
    "question": "Which orchestration pattern is best when you need the agent to autonomously plan, reason, and decide on steps for an open-ended task?",
    "options": [
        "Manual tool invocation",
        "LLM-driven orchestration",
        "Chaining agents in a fixed order",
        "Code-driven orchestration"
    ],
    "correctAnswer": "LLM-driven orchestration",
    "explanation": "LLM-driven orchestration is ideal for open-ended, autonomous planning."
}
```

---

### Question 12

```json
{
    "question": "A developer wants to decompose a complex task into research, outline, draft, and critique steps, each handled by a different agent. What is a recommended code-driven pattern for this?",
    "options": [
        "Chaining agents by transforming outputs to inputs",
        "Parallel agent execution",
        "Manual tool invocation",
        "LLM-driven orchestration"
    ],
    "correctAnswer": "Chaining agents by transforming outputs to inputs",
    "explanation": "Chaining agents is a common code-driven orchestration pattern."
}
```

---

### Question 13

```json
{
    "question": "You want to run multiple agents in parallel for independent tasks. What is a key benefit of this approach?",
    "options": [
        "Greater flexibility for open-ended tasks",
        "Improved speed and efficiency for independent tasks",
        "Better at handling ambiguous user requests",
        "Requires less monitoring and iteration"
    ],
    "correctAnswer": "Improved speed and efficiency for independent tasks",
    "explanation": "Parallel execution speeds up workflows when tasks are independent."
}
```

---

### Question 14

```json
{
    "question": "A product manager wants to use specialized agents for planning, report writing, and critique, but wants to avoid a single general-purpose agent. What is the main advantage of this approach?",
    "options": [
        "Lower cost for all tasks",
        "Specialized agents excel at their specific tasks, improving quality",
        "Easier to monitor and iterate on prompts",
        "Requires less orchestration logic"
    ],
    "correctAnswer": "Specialized agents excel at their specific tasks, improving quality",
    "explanation": "Specialized agents are more effective than a single general-purpose agent for complex workflows."
}
```

---

### Question 15

```json
{
    "question": "Which of the following is a recommended tactic for improving LLM-driven agent workflows over time?",
    "options": [
        "Disable all tools and handoffs",
        "Invest in evals to train and improve agent performance",
        "Use only code-driven orchestration",
        "Rely on static prompts only"
    ],
    "correctAnswer": "Invest in evals to train and improve agent performance",
    "explanation": "Evals help you measure and improve agent performance over time."
}
```

---
