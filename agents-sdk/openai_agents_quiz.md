# OpenAI Agents SDK Quiz

A comprehensive quiz covering the OpenAI Agents Python SDK concepts, features, and best practices.

**Total Questions:** 47  
**Time Limit:** 60 minutes  
**Passing Score:** 70%

---

## Question 1

**Category:** Output Schema | **Difficulty:** Intermediate

By default, if you set `output_types=BarModel` (a Pydantic model) and do not specify `output_schema_strict`, the SDK will generate a strict JSON schema.

-   [ ] True
-   [x] False
-   [ ] Only if you used StrictInt or StrictStr in BarModel
-   [ ] Only if you passed convert_schemas_to_strict=True to the Agent

**Explanation:** By default, the SDK does NOT generate strict JSON schemas. You need to explicitly set output_schema_strict=True or use convert_schemas_to_strict=True to get strict schemas.

---

## Question 2

**Category:** Error Handling | **Difficulty:** Intermediate

Which exception is raised when an LLM output fails to match the declared output_type schema at runtime?

-   [ ] UserError
-   [x] ModelBehaviorError
-   [ ] MaxTunesExceeded
-   [ ] InvalidSchemaError

**Explanation:** ModelBehaviorError is raised when the LLM's output doesn't match the expected schema, indicating the model didn't follow the specified output format.

---

## Question 3

**Category:** Security & Best Practices | **Difficulty:** Advanced

Your OpenAI-based financial assistant will handle highly sensitive financial information. According to prompt engineering best practices, what should you synthesize and provide to the developer?

-   [ ] A full list of supported financial tasks and detailed schemas for each one
-   [x] A careful persona, with specific safety instructions, such as: "You are a secure financial assistant. Never expose account numbers. Always redact sensitive banking information."
-   [ ] A low temperature setting (e.g. 0.1) in ModelSettings to make responses consistent
-   [ ] A planning checkpoint that instructs the agent to reflect before using any tool

**Explanation:** For sensitive financial information, explicit safety instructions in the persona are crucial to prevent data exposure and ensure proper handling of sensitive data.

---

## Question 4

**Category:** Pydantic & Type Hints | **Difficulty:** Beginner

One of Pydantic's standout features is that it uses Python type hints for data validation and schema definition. Why is this advantageous?

-   [x] They allow seamless validation, integrate with IDEs and static type-checkers like Mypy or Pyright.
-   [ ] Type hints are optional and don't affect validation.
-   [ ] Type hints allow storing runtime values inside models.
-   [ ] Type hints ensure Pydantic will bypass all validation if annotations match.

**Explanation:** Python type hints provide seamless integration with development tools, enabling better IDE support, static analysis, and validation while maintaining clean, readable code.

---

## Question 5

**Category:** Dynamic Instructions | **Difficulty:** Advanced

Given the following context dataclass:

```python
@dataclass
class ChatCtx:
    name: str
    last_msg: str
```

Which approach correctly sets up the agent with dynamic instructions using type hints?

-   [ ] Agent([ChatCtx](name="Chat", instructions="Hello, {name}, how can I help?")
-   [x] Agent([ChatCtx](name="Chat", instructions=lambda ctx, ag: f"Hi {ctx.context.name}, your last message: {ctx.context.last_msg}")
-   [ ] def dyn(ctx: RunContextWrapper[ChatCtx], ag: Agent): return f"Name: {ctx.context.name}"; Agent([ChatCtx](name="Chat", instructions=dyn))
-   [ ] Agent([ChatCtx](name="Chat", instructions=ChatCtx))

**Explanation:** The lambda function approach correctly uses the context parameter to access the dataclass fields and dynamically generate instructions based on the runtime context.

---

## Question 6

**Category:** Model Settings | **Difficulty:** Intermediate

What is the effect of using high temperature (e.g. 1.2) with low top_k (e.g. 5) and low top_p (e.g. 0.3)?

-   [x] Output will be highly unpredictable and full of odd word choices
-   [ ] Very stable but limited—choosing from only a few top tokens
-   [ ] Balanced mix of randomness within a small set of top picks
-   [ ] Identical outputs every time with no creativity

**Explanation:** High temperature increases randomness, while low top_k and top_p restrict token selection to a small set, resulting in unpredictable but potentially odd word choices.

---

## Question 7

**Category:** Output Types | **Difficulty:** Intermediate

Which of the following correctly describes what happens if you pass a dataclass `PurchaseInfo` as `output_type` to an agent?

-   [ ] The SDK requires you to manually write a JSON schema.
-   [x] The SDK auto-generates a strict JSON schema and converts the final JSON into a PurchaseInfo instance.
-   [ ] The SDK ignores the dataclass and returns raw JSON.
-   [ ] The SDK only supports Pydantic models, not dataclasses.

**Explanation:** The SDK automatically generates a JSON schema from the dataclass and converts the LLM's JSON output back into a PurchaseInfo instance.

---

## Question 8

**Category:** Markdown | **Difficulty:** Beginner

Which of the following correctly uses Markdown to make an image clickable (links to a URL) and displays a tooltip title when hovered?

-   [ ] ![IAm old rock in the desert](/assets/images/shiprock.jpg)[(https://flickr.com)](https://flickr.com)
-   [x] [![IAm old rock in the desert](/assets/images/shiprock.jpg)](https://flickr.com)
-   [ ] ![IAm old rock in the desert](/assets/images/shiprock.jpg "Shiprock, New Mexico by Beau Rogers")(https://flickr.com)
-   [ ] [![IAm old rock in the desert](/assets/images/shiprock.jpg)](https://flickr.com "Shiprock, New Mexico by Beau Rogers")

**Explanation:** The correct Markdown syntax for a clickable image is [![alt text](image_url)](link_url). The tooltip syntax shown in option 4 is not standard Markdown.

---

## Question 9

**Category:** Hooks & Lifecycle | **Difficulty:** Intermediate

If you want to log whenever your agent starts or finishes using a tool, where should you attach your AgentHooks?

-   [x] Create an AgentHooks instance and pass it into RunHooks when running the agent.
-   [ ] Assign your custom AgentHooks to the hooks attribute of the Agent before running it.
-   [ ] Modify the RunHooks class to include your AgentHooks methods.
-   [ ] Use the RunContextWrapper to register your AgentHooks during execution.

**Explanation:** AgentHooks should be passed into RunHooks when running the agent, allowing you to hook into specific agent lifecycle events.

---

## Question 10

**Category:** Tracing | **Difficulty:** Intermediate

In the OpenAI Agents SDK, which statement accurately reflects the relationship between Traces and Spans?

-   [ ] A Trace represents a single operation like an LLM generation, and each Span corresponds to different agent runs.
-   [x] A Trace is a sequence of Spans, where each Span logs an event such as tool calls, LLM generations, or handoffs during a single workflow.
-   [ ] Spans are only used for tool calls, while Traces only track guardrail checks.
-   [ ] Traces and Spans are interchangeable; both record identical events in agent execution.

**Explanation:** A Trace contains multiple Spans, where each Span represents a specific event or operation within the workflow execution.

---

## Question 11

**Category:** Output Validation | **Difficulty:** Intermediate

Which combination of attributes controls how an agent's final LLM output is validated and parsed?

-   [x] output_type, agent_output_schema, output_parser
-   [ ] tools, handoffs, model
-   [ ] instructions, name, temperature
-   [ ] convert_schemas_to_strict, tools, parse_mode

**Explanation:** The output_type, agent_output_schema, and output_parser attributes work together to control how the agent's final output is validated and parsed.

---

## Question 12

**Category:** Error Handling & Resilience | **Difficulty:** Advanced

Your financial trading agent system processes real-time market data through multiple tools. During market volatility, you observe that tool execution latencies spike unpredictably (50ms – 5000ms). Some tools become temporarily unavailable, others return stale data. The system must continue operating with degraded data rather than failing completely. Which exception handling strategy maintains trading capability during infrastructure stress?

-   [x] Implement timeout-based tool selection with fallback chains, graceful degradation to cached/stale data with age indicators.
-   [ ] Always use the fastest responding tool regardless of data quality
-   [ ] Stop all trading when any tool shows increased latency
-   [ ] Cache all responses and never call external tools during volatility

**Explanation:** Graceful degradation with fallback chains and timeout-based selection ensures the system continues operating with the best available data during infrastructure stress.

---

## Question 13

**Category:** Agent Lifecycle | **Difficulty:** Intermediate

You create a weather agent with a single tool and turn limits:

```python
@register_tool
def weather(city: str) -> str:
    return f"Weather in {city}: 25°C, sunny"

agent = Agent(
    name="Weather Assistant",
    tools=[weather],
    instructions="You are a helpful weather assistant. Use the weather tool when users ask for weather information.",
    max_turns=1,
)

result = agent.run("Hello, what can you do?", max_turns=1)
```

What will be the output of this code and why?

-   [ ] The agent will raise a MaxTurnsException and stop responding.
-   [x] The agent successfully responds with: 'I'm a weather assistant. This is an agent loop (needs 2 LLM calls: one to analyze the request and call tools, another to process tool result and reply).'
-   [ ] max_turns=1 only applies to tool calls, not to regular conversational responses.
-   [ ] The weather tool was called and we will get the direct tool call result 'Weather in Karachi: 25°C, sunny'.

**Explanation:** The agent can respond without using tools, requiring only 1 LLM call which fits within max_turns=1. The agent will explain its capabilities without calling the weather tool.

---

## Question 14

**Category:** Model Settings | **Difficulty:** Intermediate

What is the purpose of the `resolve()` method within ModelSettings?

-   [x] Combines default settings with overrides and returns a new settings instance.
-   [ ] Immediately sends settings to the LLM API.
-   [ ] Validates if all required settings are non-null.
-   [ ] Deletes unset fields and returns the same object.

**Explanation:** The resolve() method merges default settings with any overrides and returns a new ModelSettings instance with the combined configuration.

---

## Question 15

**Category:** Error Handling | **Difficulty:** Advanced

You're building a financial analysis tool that needs to process multiple stocks. A junior developer implements this:

```python
@function_tool
def analyze_portfolio(symbols: List[str]) -> dict:
    results = {}
    for symbol in symbols:
        try:
            data = get_stock_data(symbol)  # May fail for invalid symbols
            analysis = perform_analysis(data)
            results[symbol] = analysis
        except Exception as e:
            results[symbol] = f"Error: {str(e)}"
    return results
```

The agent receives mixed results with some symbols having analysis data and others having error strings. It then tries to perform calculations on the error strings. What's the more sophisticated approach to handle this mixed success/failure scenario?

-   [ ] Return only successful results and ignore failed ones
-   [x] Use a structured result format with success/failure indicators and separate error details
-   [ ] Raise an exception if any symbol fails to maintain data consistency
-   [ ] Log errors and return empty results for failed symbols

**Explanation:** A structured result format with explicit success/failure indicators allows the agent to properly handle mixed results and avoid processing error strings as data.

---

## Question 16

**Category:** Async/Sync Integration | **Difficulty:** Intermediate

Suppose you have a synchronous Python function `analyze_portfolio(data: dict) -> str` that processes financial data, but your OpenAI Agents SDK workflow is fully asynchronous. What's the best practice for exposing this synchronous function as a tool in your async-first agent?

-   [x] Just decorate it with @function_tool; the SDK will automatically handle running it, so your async event loop isn't blocked.
-   [ ] Manually wrap analyze_portfolio inside an async def that calls await asyncio.to_thread(...), then decorate the wrapper with @function_tool.
-   [ ] Rewrite the entire function to be async; the SDK doesn't support synchronous functions at all.
-   [ ] Use a special @sync_function_tool decorator that OpenAI provides for synchronous functions.

**Explanation:** The SDK automatically handles synchronous functions by running them in a thread pool, preventing blocking of the async event loop.

---

## Question 17

**Category:** Tool Design | **Difficulty:** Intermediate

Your system has tools that call external APIs with different authentication methods. A developer implements this pattern:

```python
@function_tool
def call_api_a(data: str) -> str:
    headers = {"Authorization": f"Bearer {API_A_TOKEN}"}
    return requests.post("https://api/a/.com", json=data, headers=headers).text

@function_tool
def call_api_b(data: str) -> str:
    headers = {"Authorization": f"Bearer {API_B_TOKEN}"}
    return requests.post("https://api/b/.com", json=data, headers=headers).text
```

The agent sometimes gets confused about which API to use for different types of data. Beyond better instructions, what's the fundamental design issue?

-   [ ] API tokens should be passed as parameters instead of being hardcoded
-   [x] Tools are too similar; the LLM can't distinguish between them without data-type-specific tool names and clear functional differences
-   [ ] Should use a single generic api_call tool with API type as parameter
-   [ ] Each tool needs different parameter schemas to help the LLM choose

**Explanation:** The tools have identical signatures and similar names, making it difficult for the LLM to choose the appropriate tool. Clear functional differences and specific tool names would help.

---

## Question 18

**Category:** Handoffs | **Difficulty:** Intermediate

You want your target agent to only receive the last 2 messages from history when a handoff occurs. Which handoff parameter helps with that?

-   [ ] tool_name_override
-   [ ] tool_description_override
-   [x] input_filter
-   [ ] on_handoff

**Explanation:** The input_filter parameter allows you to modify the input data passed to the target agent, including filtering message history.

---

## Question 19

**Category:** Dynamic Instructions | **Difficulty:** Advanced

Suppose you have a support agent that needs to tailor its guidance based on whether a user is a premium subscriber or basic user:

```python
@dataclass
class UserContext:
    user_id: str
    is_premium: bool

def premium_instructions(context: RunContextWrapper[UserContext], agent: Agent):
    if context.context.is_premium:
        return "You are a support agent prioritizing and fast-tracking premium user issues."
    else:
        return "You are a support agent helping a basic user with general support."

agent = Agent(
    name="SupportAgent",
    instructions=...,  # <---
    tools=[...],
)
```

How should you configure instructions so it dynamically updates based on the user's subscription status at runtime?

-   [ ] Pass a template string like instructions='You are a support agent. User type: {is_premium}' and the SDK will auto-fill {is_premium} from context.
-   [ ] Subclass Agent and override a protected method like \_get_dynamic_instructions(self, context).
-   [x] Provide the function premium_instructions directly to the instructions argument—since it accepts (context, agent) and returns the proper string.
-   [ ] Dynamic instructions aren't supported; instructions must be a fixed string at agent creation.

**Explanation:** The instructions parameter accepts a function that takes (context, agent) and returns a string, allowing for dynamic instruction generation based on runtime context.

---

## Question 20

**Category:** Hooks & Lifecycle | **Difficulty:** Intermediate

What is the primary purpose of RunHooks in the Agents SDK?

-   [ ] To validate the final output of an agent
-   [x] To provide callbacks that fire during any agent run across handoffs
-   [ ] To modify the agent's instructions on the fly
-   [ ] To automatically generate JSON schemas from Pydantic models

**Explanation:** RunHooks provide callbacks that fire during agent execution, allowing you to hook into various lifecycle events across the entire run, including handoffs.

---

## Question 21

**Category:** Multi-Agent Systems | **Difficulty:** Advanced

You're developing a multi-agent supply chain assistant with: InventoryAgent: monitors stock levels and forecasts shortages. OrderAgent: handles ordering, shipment, and vendor interactions. What's the best way to utilize the handoffs primitive?

-   [ ] Each agent runs on its own; a central script manually pipes data between them based on alerts.
-   [ ] InventoryAgent directly imports and calls OrderAgent's methods as a library.
-   [x] When InventoryAgent detects a stock shortage needing replenishment, it uses a handoff to transfer control, along with context, to OrderAgent to manage the ordering process.
-   [ ] Use handoffs randomly to balance load across agents when requests pile up.

**Explanation:** Handoffs allow seamless transfer of control and context between agents, enabling the InventoryAgent to hand off to OrderAgent when specific conditions are met.

---

## Question 22

**Category:** Prompt Engineering | **Difficulty:** Beginner

You want your LLM to solve a tricky puzzle and explain its reasoning. Which system message best applies Chain of Thought prompting?

-   [ ] Give only the final answer—no explanation.
-   [x] Please think step-by-step, show your reasoning, then give the final answer.
-   [ ] Use high temperature to explore many possibilities randomly.
-   [ ] Internally reflect, then output the best answer without showing thought steps.

**Explanation:** Chain of Thought prompting explicitly asks the model to show its reasoning process step-by-step before providing the final answer.

---

## Question 23

**Category:** Tools | **Difficulty:** Beginner

Which of the following is a valid item in the tools list when initializing an agent?

-   [ ] A plain Python function (without a decorator).
-   [x] A FunctionTool object created via @function_tool.
-   [ ] A raw dictionary representing a tool schema (not wrapped).
-   [ ] A plain class instance without tool wrapping.

**Explanation:** FunctionTool objects created with the @function_tool decorator are valid items in the tools list for agent initialization.

---

## Question 24

**Category:** Agent Lifecycle | **Difficulty:** Advanced

You create a weather agent with a single tool and turn limits:

```python
@function_tool
def get_weather(city: str) -> str:
    # Simulates weather API call
    return f"Weather in {city}: 25°C, sunny"

agent = Agent(
    name="Weather Assistant",
    instructions="You are a helpful weather assistant. Use the weather tool when users ask for weather information.",
    tools=[get_weather],
    tool_use_behavior="stop_on_first_tool"
)

# Test with max_turns=1
result = Runner.run_sync(agent, "What is the weather in Karachi?", max_turns=1)
print(result.final_output)
```

What will be the output of this code and why?

-   [ ] The agent raises a MaxTurnsException and fails to provide any response. This is as agent loop needs 2 LLM calls: one to analyze the request and call tools, another to process tool results and respond
-   [ ] The agent successfully responds with: "I'm a weather assistant! This is a direct response without using tools, requiring only 1 LLM call which fits within max_turns=1"
-   [ ] max_turns=1 only applies to tool calls, not to regular conversational responses
-   [x] The weather tool was called and we will get the direct tool call result 'Weather in Karachi: 25°C, sunny'.

**Explanation:** With tool_use_behavior="stop_on_first_tool", the agent will call the weather tool and directly return the tool output without further LLM processing, avoiding the 2-LLM-call requirement.

---

## Question 25

**Category:** Model Settings | **Difficulty:** Intermediate

When using a low temperature (e.g. 0.3), a moderate top_k (e.g. 50), and a high top_p (e.g. 0.95), what kind of output is most likely?

-   [ ] Very random, with lots of strange word choices
-   [x] Creative and varied, but still coherent
-   [ ] Extremely focused and repetitive
-   [ ] Completely deterministic with no variety

**Explanation:** Low temperature provides focus, moderate top_k provides variety within reasonable bounds, and high top_p allows for creative but coherent output.

---

## Question 26

**Category:** Dynamic Instructions | **Difficulty:** Intermediate

You want the agent to greet each user by name dynamically based on the context. Which behavior illustrates the correct use of instructions?

-   [ ] Passing 'Hello {name}!' directly—expecting the SDK to auto-substitute {name}.
-   [x] Defining a function greet(ctx, agent) -> str and passing it to instructions.
-   [ ] Manually building the Agent inside Runner.run(...), reconstructing instructions each time.
-   [ ] Using a class method override to compute instructions.

**Explanation:** Defining a function that takes context and agent parameters and passing it to instructions is the correct way to implement dynamic instructions.

---

## Question 27

**Category:** Agent Lifecycle | **Difficulty:** Advanced

You create a weather agent with a single tool and turn limits:

```python
@function_tool
def get_weather(city: str) -> str:
    # Simulates weather API call
    return f"Weather in {city}: 25°C, sunny"

agent = Agent(
    name="Weather Assistant",
    instructions="You are a helpful weather assistant. Use the weather tool when users ask for weather information.",
    tools=[get_weather]
)

# Test with max_turns=1
result = Runner.run_sync(agent, "What is the weather in Karachi?", max_turns=1)
print(result.final_output)
```

What will be the output of this code and why?

-   [x] The agent raises a MaxTurnsException and fails to provide any response. This is as agent loop needs 2 LLM calls: one to analyze the request and call tools, another to process tool results and respond
-   [ ] The agent successfully responds with: "I'm a weather assistant! This is a direct response without using tools, requiring only 1 LLM call which fits within max_turns=1"
-   [ ] max_turns=1 only applies to tool calls, not to regular conversational responses
-   [ ] The weather tool was called and we will get the direct tool call result 'Weather in Karachi: 25°C, sunny'.

**Explanation:** The agent will try to use the weather tool, which requires 2 LLM calls (one to decide to use tool, one to process result), exceeding max_turns=1 and causing a MaxTurnsException.

---

## Question 28

**Category:** Error Handling | **Difficulty:** Beginner

If an agent exceeds its allowed number of turns (including tool invocations), which exception is raised?

-   [ ] ModelBehaviorError
-   [ ] UserError
-   [ ] AgentsException
-   [x] MaxTurnsExceeded

**Explanation:** MaxTurnsExceeded is the specific exception raised when an agent exceeds its maximum allowed turns.

---

## Question 29

**Category:** Markdown | **Difficulty:** Beginner

Given this Markdown:

```
10. First item
11. Second item
13. Third item
20. Fourth item
```

What will be the rendered output?

-   [x] 10. First item 11. Second item 13. Third item 20. Fourth item
-   [ ] -   First item
        -   Second item
        -   Third item
        -   Fourth item
-   [ ] 10. First item 11. Second item 12. Third item 13. Fourth item
-   [ ] show render error

**Explanation:** Markdown preserves the original numbering as written, it doesn't automatically renumber or convert to bullet points.

---

## Question 30

**Category:** Agent Configuration | **Difficulty:** Beginner

When you call the Agent constructor in the OpenAI Agents Python SDK, which parameter is required?

-   [ ] instructions
-   [ ] name
-   [ ] model and model_settings
-   [x] No parameters are required

**Explanation:** All parameters in the Agent constructor are optional; the SDK provides sensible defaults for all parameters.

---

## Question 31

**Category:** Guardrails | **Difficulty:** Intermediate

In a banking chatbot, you want to ensure that before any transaction request is processed, the system verifies that the amount provided is a positive number and doesn't exceed the user's daily transfer limit. Which scenario best demonstrates the essential use of an input guardrail?

-   [ ] Ensuring the chatbot's output is polite and well-mannered before displaying it to the user.
-   [ ] Blocking the chatbot from connecting to unauthorized external banking APIs during execution.
-   [x] Validating that the requested transfer amount is a valid positive integer and below the allowed daily maximum before the agent attempts the transaction.
-   [ ] Shortening overly long user messages to conserve tokens before the agent processes them.

**Explanation:** Input guardrails validate and sanitize user input before the agent processes it, ensuring data quality and security constraints are met.

---

## Question 32

**Category:** Tools | **Difficulty:** Beginner

Which of the following statements about the @function_tool decorator in the OpenAI Agents SDK is correct?

-   [x] You must use @function_tool on every function that an agent can access as a tool.
-   [ ] The decorator @function_tool cannot be applied to asynchronous (async) functions.
-   [ ] Every tool function must include a docstring, or it won't be registered.
-   [ ] Using @function_tool automatically generates an OpenAPI spec for the function.

**Explanation:** The @function_tool decorator is required to register functions as tools that agents can access and use.

---

## Question 33

**Category:** Streaming | **Difficulty:** Intermediate

Which return type does Runner.run_streamed(...) provide?

-   [ ] RunResult
-   [x] AsyncGenerator[str]
-   [ ] StreamingClientResponse
-   [ ] RunResultStreaming

**Explanation:** Runner.run_streamed() returns an AsyncGenerator[str] that yields streaming events as they occur.

---

## Question 34

**Category:** Tracing | **Difficulty:** Intermediate

You want two separate Runner.run() calls to be part of the same trace session named 'JokeWorkflow'. How should you configure this?

-   [x] Wrap both Runner.run(...) invocations inside a with trace('JokeWorkflow'): block.
-   [ ] Pass trace='JokeWorkflow' into both run() calls individually.
-   [ ] Use the group_id parameter in Runner.run(...) to label both runs identically.
-   [ ] Manually merge trace files after both runs complete.

**Explanation:** Using a context manager with trace('JokeWorkflow') ensures both runs are part of the same trace session.

---

## Question 35

**Category:** Guardrails | **Difficulty:** Intermediate

What happens when a guardrail tripwire is triggered?

-   [ ] The agent logs a warning but continues processing
-   [x] A GuardrailTripwireTriggered exception is raised, stopping agent execution
-   [ ] The agent automatically retries the same prompt
-   [ ] The next agent in the workflow takes over

**Explanation:** When a guardrail tripwire is triggered, a GuardrailTripwireTriggered exception is raised, which stops the agent's execution.

---

## Question 36

**Category:** Multi-Agent Systems | **Difficulty:** Advanced

You have an orchestrator agent that uses 5 specialist agents as tools. During execution, one specialist agent (translation_agent) encounters a temporary API rate limit and fails. The orchestrator's instructions include "If any translation fails, try an alternative approach." What happens to the orchestrator's execution context and the remaining specialist agents?

-   [ ] The orchestrator immediately fails with the specialist's exception, and all pending tool calls are cancelled
-   [x] The orchestrator receives the exception as tool output, can handle it in its reasoning, and continues with other specialists
-   [ ] The failed specialist automatically retries 3 times before the orchestrator sees the failure
-   [ ] All specialist agents share the same execution context, so the failure affects all of them

**Explanation:** The orchestrator receives the exception as tool output and can handle it according to its instructions, continuing with other specialists.

---

## Question 37

**Category:** Agent Configuration | **Difficulty:** Intermediate

What happens when instructions say "always use tools" but tool_choice="none"?

-   [ ] The agent raises a ConfigurationError during initialization due to conflicting settings
-   [ ] The instructions override tool_choice, and the agent uses tools despite the setting
-   [x] tool_choice="none" takes precedence; the agent cannot use tools and responds with training data only
-   [ ] tool_choice="none" takes precedence; the agent decides which tools to use and respond.

**Explanation:** tool_choice="none" takes precedence over instructions, preventing the agent from using any tools.

---

## Question 38

**Category:** Error Handling | **Difficulty:** Intermediate

What happens when the tool raises ValueError?

-   [ ] The agent execution stops with an unhandled ValueError, terminating the conversation
-   [x] The agent receives the error message as tool output and can retry based on its instructions
-   [ ] The SDK automatically retries the tool call 3 times before failing
-   [ ] The tool call is skipped and the agent responds without using any tools

**Explanation:** Tool exceptions are captured and passed to the agent as tool output, allowing the agent to handle the error according to its instructions.

---

## Question 39

**Category:** Runner Methods | **Difficulty:** Intermediate

What is the practical difference between Runner.run() and Runner.run_sync()?

-   [ ] run_sync is asynchronous and returns immediately, while run blocks until the agent finishes.
-   [x] run is async and must be awaited, whereas run_sync blocks execution and should only be used when no event loop is running.
-   [ ] They behave identically; run_sync just wraps run_streamed() under the hood.
-   [ ] run returns streaming events incrementally; run_sync returns the final result only.

**Explanation:** run() is async and must be awaited, while run_sync() is synchronous and blocks until completion, suitable for use outside of async contexts.

---

## Question 40

**Category:** Streaming | **Difficulty:** Intermediate

Which scenario best fits the use of Runner.run_streamed()?

-   [ ] You want to block until completion and collect a final output object.
-   [x] You need live, partial output updates as the agent processes input, like typing a chat response in real-time.
-   [ ] You only plan to use synchronous code and don't need real-time updates.
-   [ ] You want to execute multiple agents simultaneously in parallel.

**Explanation:** run_streamed() is ideal for scenarios where you need real-time updates as the agent processes input, providing a streaming experience.

---

## Question 41

**Category:** Dynamic Instructions | **Difficulty:** Intermediate

You want your support agent to include the current date and user name dynamically in its system prompt. Which of the following is the correct way to configure instructions?

-   [ ] instructions = 'Today's date is {date}, user is {name}'
-   [x] def dynamic_instr(ctx: RunContextWrapper, agent: Agent) -> str: return f'Today: {ctx.context.current_date}, User: {ctx.context.name}' agent = Agent(..., instructions=dynamic_instr)
-   [ ] instructions = lambda ctx: f'Today: {datetime.now()}, User: {ctx.context.name}' agent = Agent(..., instructions=instructions)
-   [ ] agent.instructions=dynamic_instr

**Explanation:** Defining a function that takes context and agent parameters and passing it to instructions is the correct way to implement dynamic instructions.

---

## Question 42

**Category:** SDK Philosophy | **Difficulty:** Beginner

The OpenAI Agents SDK is described as 'Python-first.' What does this mean?

-   [ ] It only runs on CPython and cannot run on PyPy or MicroPython.
-   [ ] It only supports OpenAI models, not local or external models.
-   [ ] It limits users to sync Python code, disallowing async workflows.
-   [x] It requires Python syntax to define agents, tools, and orchestration—with no new DSL.

**Explanation:** Python-first means the SDK uses native Python syntax and constructs to define agents, tools, and orchestration without requiring a separate domain-specific language.

---

## Question 43

**Category:** Handoffs | **Difficulty:** Intermediate

You want to trigger a logging operation whenever a handoff to AuditAgent occurs. Which setup leverages the on_handoff callback correctly?

-   [ ] handoffs=[handoff(agent=AuditAgent, tool_name_override='to_audit')]
-   [x] handoffs=[handoff(agent=AuditAgent, on_handoff=log_callback)]
-   [ ] handoffs=[AuditAgent] # Run log_callback() inside AuditAgent later
-   [ ] AuditAgent.on_handoff = log_callback

**Explanation:** The on_handoff parameter in the handoff function allows you to specify a callback function that will be executed when the handoff occurs.

---

## Question 44

**Category:** Guardrails | **Difficulty:** Beginner

When is an input guardrail function logically applied in relation to the agent's processing of user input?

-   [ ] After the agent produces output
-   [x] Before the agent processes the user's input
-   [ ] Only when a tool call is made
-   [ ] During agent initialization

**Explanation:** Input guardrails are applied before the agent processes the user's input, allowing for validation and sanitization of incoming data.

---

## Question 45

**Category:** Handoffs | **Difficulty:** Advanced

The system falls unpredictably in production. What's the subtle but critical issue with this handoff pattern?

-   [x] Handoffs should use the Handoff class, not return agent objects directly
-   [ ] The data parameter should be a complex object, not a string
-   [ ] Each agent needs identical tool sets for handoffs to work
-   [ ] Agents can't handoff to each other without a coordinator agent

**Explanation:** Handoffs should use the proper Handoff class constructor rather than returning agent objects directly, which can cause unpredictable behavior.

---

## Question 46

**Category:** Prompt Engineering | **Difficulty:** Advanced

For a complex planning task requiring exploration of multiple solutions, how should your system prompt implement Tree of Thoughts?

-   [ ] Instruct: "Think step-by-step once, then answer."
-   [ ] Use high temperature to make the LLM think widely in one shot.
-   [ ] Rely on internal model capabilities without explicit branching instructions.
-   [x] Instruct: "Generate multiple reasoning branches, evaluate each, prune low-quality paths, then select and continue the best one until solution."

**Explanation:** Tree of Thoughts explicitly instructs the model to generate multiple reasoning branches, evaluate them, and iteratively refine the best path.

---

## Question 47

**Category:** Guardrails | **Difficulty:** Intermediate

Only the first agent's input guardrails are executed; downstream agents in a multi-agent chain do not re-run input guardrails.

-   [ ] True
-   [x] False
-   [ ] Only if guardrails_disabled=True
-   [ ] Only if max_turns > 1

**Explanation:** Each agent in a multi-agent chain runs its own input guardrails independently, ensuring proper validation at each step.

---

## Answer Key

1. False
2. ModelBehaviorError
3. A careful persona, with specific safety instructions, such as: "You are a secure financial assistant. Never expose account numbers. Always redact sensitive banking information."
4. They allow seamless validation, integrate with IDEs and static type-checkers like Mypy or Pyright.
5. Agent([ChatCtx](name="Chat", instructions=lambda ctx, ag: f"Hi {ctx.context.name}, your last message: {ctx.context.last_msg}")
6. Output will be highly unpredictable and full of odd word choices
7. The SDK auto-generates a strict JSON schema and converts the final JSON into a PurchaseInfo instance.
8. [![IAm old rock in the desert](/assets/images/shiprock.jpg)](https://flickr.com)
9. Create an AgentHooks instance and pass it into RunHooks when running the agent.
10. A Trace is a sequence of Spans, where each Span logs an event such as tool calls, LLM generations, or handoffs during a single workflow.
11. output_type, agent_output_schema, output_parser
12. Implement timeout-based tool selection with fallback chains, graceful degradation to cached/stale data with age indicators.
13. The agent successfully responds with: 'I'm a weather assistant. This is an agent loop (needs 2 LLM calls: one to analyze the request and call tools, another to process tool result and reply).'
14. Combines default settings with overrides and returns a new settings instance.
15. Use a structured result format with success/failure indicators and separate error details
16. Just decorate it with @function_tool; the SDK will automatically handle running it, so your async event loop isn't blocked.
17. Tools are too similar; the LLM can't distinguish between them without data-type-specific tool names and clear functional differences
18. input_filter
19. Provide the function premium_instructions directly to the instructions argument—since it accepts (context, agent) and returns the proper string.
20. To provide callbacks that fire during any agent run across handoffs
21. When InventoryAgent detects a stock shortage needing replenishment, it uses a handoff to transfer control, along with context, to OrderAgent to manage the ordering process.
22. Please think step-by-step, show your reasoning, then give the final answer.
23. A FunctionTool object created via @function_tool.
24. The weather tool was called and we will get the direct tool call result 'Weather in Karachi: 25°C, sunny'.
25. Creative and varied, but still coherent
26. Defining a function greet(ctx, agent) -> str and passing it to instructions.
27. The agent raises a MaxTurnsException and fails to provide any response. This is as agent loop needs 2 LLM calls: one to analyze the request and call tools, another to process tool results and respond
28. MaxTurnsExceeded
29. 10. First item
    11. Second item
    12. Third item
    13. Fourth item
30. No parameters are required
31. Validating that the requested transfer amount is a valid positive integer and below the allowed daily maximum before the agent attempts the transaction.
32. You must use @function_tool on every function that an agent can access as a tool.
33. AsyncGenerator[str]
34. Wrap both Runner.run(...) invocations inside a with trace('JokeWorkflow'): block.
35. A GuardrailTripwireTriggered exception is raised, stopping agent execution
36. The orchestrator receives the exception as tool output, can handle it in its reasoning, and continues with other specialists
37. tool_choice="none" takes precedence; the agent cannot use tools and responds with training data only
38. The agent receives the error message as tool output and can retry based on its instructions
39. run is async and must be awaited, whereas run_sync blocks execution and should only be used when no event loop is running.
40. You need live, partial output updates as the agent processes input, like typing a chat response in real-time.
41. def dynamic_instr(ctx: RunContextWrapper, agent: Agent) -> str: return f'Today: {ctx.context.current_date}, User: {ctx.context.name}' agent = Agent(..., instructions=dynamic_instr)
42. It requires Python syntax to define agents, tools, and orchestration—with no new DSL.
43. handoffs=[handoff(agent=AuditAgent, on_handoff=log_callback)]
44. Before the agent processes the user's input
45. Handoffs should use the Handoff class, not return agent objects directly
46. Instruct: "Generate multiple reasoning branches, evaluate each, prune low-quality paths, then select and continue the best one until solution."
47. False

---

## Categories Covered

-   **Agent Configuration** (3 questions)
-   **Agent Lifecycle** (3 questions)
-   **Async/Sync Integration** (1 question)
-   **Dynamic Instructions** (3 questions)
-   **Error Handling** (4 questions)
-   **Error Handling & Resilience** (1 question)
-   **Guardrails** (4 questions)
-   **Handoffs** (3 questions)
-   **Hooks & Lifecycle** (2 questions)
-   **Markdown** (2 questions)
-   **Model Settings** (3 questions)
-   **Multi-Agent Systems** (2 questions)
-   **Output Schema** (1 question)
-   **Output Types** (1 question)
-   **Output Validation** (1 question)
-   **Pydantic & Type Hints** (1 question)
-   **Prompt Engineering** (2 questions)
-   **Runner Methods** (1 question)
-   **SDK Philosophy** (1 question)
-   **Security & Best Practices** (1 question)
-   **Streaming** (2 questions)
-   **Tool Design** (1 question)
-   **Tools** (2 questions)
-   **Tracing** (2 questions)

## Difficulty Distribution

-   **Beginner:** 12 questions (25.5%)
-   **Intermediate:** 25 questions (53.2%)
-   **Advanced:** 10 questions (21.3%)
