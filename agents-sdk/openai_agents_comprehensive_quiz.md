# OpenAI Agents SDK Comprehensive Quiz

## 80+ Intermediate to Advanced Questions

### Section 1: Agent Configuration and Architecture (Questions 1-15)

**1. When configuring an agent with dynamic instructions, what parameter types can the instruction function receive?**
a) Only the agent object
b) Only the context object  
c) Both RunContextWrapper[T] and Agent[T]
d) Only string parameters

**2. What happens to tool_choice after a tool call is made when it's set to a specific tool name?**
a) It remains the same for subsequent calls
b) It automatically resets to "auto"
c) It gets set to "none"
d) It causes an infinite loop

**3. Which of the following is NOT a valid value for ModelSettings.tool_choice?**
a) "auto"
b) "required"
c) "optional"
d) "none"

**4. When using agent.tool_use_behavior="stop_on_first_tool", what happens after a tool call?**
a) The agent continues with auto mode
b) The tool output becomes the final response without further LLM processing
c) An error is raised
d) The agent waits for user input

**5. What is the primary difference between Agent.reset_tool_choice and tool_use_behavior settings?**
a) They control different aspects of tool usage flow
b) They are identical in functionality
c) One is for input, one is for output
d) One is deprecated

**6. In agent lifecycle hooks, which class should you subclass to observe agent events?**
a) AgentObserver
b) AgentHooks
c) AgentLifecycle
d) AgentMonitor

**7. When cloning an agent, which properties can be modified?**
a) Only the name
b) Only instructions and model
c) Any agent property
d) Only tools and handoffs

**8. What is the correct way to force an agent to NOT use any tools?**
a) Set tools=[]
b) Set tool_choice="none"
c) Set tool_use_behavior="disabled"
d) Set model_settings.disable_tools=True

**9. Which output type configuration enables structured outputs instead of plain text?**
a) Setting output_format="json"
b) Setting any output_type parameter
c) Setting structured_output=True
d) Setting response_format="structured"

**10. What constraint applies to context objects across all components in an agent run?**
a) They must be Pydantic models
b) They must be dataclasses
c) They must all use the same type
d) They must be serializable

**11. When using non_strict_output_type, what capability does this provide?**
a) Allows partial outputs
b) Enables output validation bypass
c) Permits flexible output structures
d) Allows mixed output types

**12. What is the recommended approach for handling sensitive data in agent instructions?**
a) Use encryption within instructions
b) Use dynamic instructions with context
c) Store in environment variables
d) Use base64 encoding

**13. In agent configuration, what is the relationship between model and model_settings?**
a) model_settings overrides model completely
b) model_settings provides tuning parameters for the specified model
c) They are mutually exclusive
d) model_settings is deprecated

**14. Which pattern is recommended for agents that need user-specific information?**
a) Hard-code user data in instructions
b) Use dynamic instructions with context
c) Pass user data as tool parameters
d) Store in global variables

**15. What happens when an agent has both instructions and dynamic instructions defined?**
a) Dynamic instructions take precedence
b) They are concatenated
c) An error is raised
d) Instructions are ignored

### Section 2: Context Management and Dependencies (Questions 16-25)

**16. What is the fundamental difference between local context and LLM context?**
a) Local context is for tools, LLM context is for generation
b) Local context is not sent to LLM, LLM context is conversation history
c) Local context is synchronous, LLM context is asynchronous
d) Local context is cached, LLM context is not

**17. When should you add information to agent instructions vs. using function tools for context?**
a) Instructions for always-useful info, tools for on-demand data
b) Instructions for small data, tools for large data
c) Instructions for static data, tools for dynamic data
d) Instructions for public data, tools for private data

**18. What is the correct way to access the context object within a tool function?**
a) context.get_current()
b) wrapper.context
c) RunContext.current()
d) ctx.data

**19. Which approach is recommended for providing the current date to an agent?**
a) Hard-code in instructions
b) Use dynamic instructions
c) Create a get_current_date tool
d) Pass in the input message

**20. When using context for dependencies like loggers, what pattern is recommended?**
a) Use global variables
b) Pass dependencies in context object
c) Use environment variables
d) Initialize in each tool

**21. What constraint exists for function tools regarding context types?**
a) All tools must use the same context type
b) Tools can use different context types
c) Context is optional for tools
d) Context must be serializable

**22. How should you handle user authentication information in context?**
a) Store in instructions
b) Pass in context object
c) Use environment variables
d) Hard-code in tools

**23. What is the benefit of using retrieval tools vs. adding data to instructions?**
a) Retrieval is faster
b) Retrieval provides grounding with relevant contextual data
c) Retrieval uses less memory
d) Retrieval is more secure

**24. When might you use web search tools instead of context?**
a) For real-time information
b) For user-specific data
c) For authentication
d) For configuration

**25. What is the recommended pattern for handling database connections in context?**
a) Create connections in each tool
b) Pass database connection in context
c) Use global connection pool
d) Create connections in instructions

### Section 3: Guardrails and Validation (Questions 26-35)

**26. What is the primary purpose of running guardrails in parallel to agents?**
a) To improve performance
b) To provide redundancy
c) To validate input/output and potentially stop expensive operations
d) To enable distributed processing

**27. When do input guardrails execute in relation to agent execution?**
a) After agent completes
b) During agent execution
c) Before agent starts, only for the first agent
d) Continuously throughout execution

**28. What must a guardrail function return to indicate a policy violation?**
a) GuardrailFunctionOutput with tripwire_triggered=True
b) GuardrailException
c) Boolean False
d) GuardrailViolation object

**29. What happens when an input guardrail tripwire is triggered?**
a) The agent continues with a warning
b) InputGuardrailTripwireTriggered exception is raised
c) The agent switches to safe mode
d) The output is filtered

**30. Why are guardrails defined on agents rather than passed to Runner.run?**
a) For performance optimization
b) Because guardrails are agent-specific and colocated code improves readability
c) To reduce memory usage
d) For backward compatibility

**31. What is the correct pattern for implementing a guardrail that uses another agent?**
a) Call the agent synchronously
b) Use Runner.run with the guardrail agent
c) Create a nested agent loop
d) Use agent.run_guardrail()

**32. When do output guardrails execute?**
a) After every tool call
b) After the final agent output, only for the last agent
c) Before each LLM generation
d) Continuously during execution

**33. What information can be included in GuardrailFunctionOutput besides tripwire status?**
a) Only the tripwire boolean
b) Additional output_info for logging/debugging
c) Alternative responses
d) Confidence scores

**34. How should you handle a scenario where you want different guardrails for different agents?**
a) Use global guardrails in RunConfig
b) Define guardrails on each specific agent
c) Use conditional logic in a single guardrail
d) Create guardrail inheritance

**35. What is the recommended approach for guardrails that need to call external services?**
a) Use synchronous calls
b) Use async functions in guardrail implementation
c) Cache results locally
d) Use background tasks

### Section 4: Handoffs and Agent Orchestration (Questions 36-50)

**36. How are handoffs represented to the LLM?**
a) As special system messages
b) As tools with names like "transfer*to*<agent_name>"
c) As context variables
d) As metadata

**37. What is the primary benefit of using handoff() function over passing agents directly?**
a) Better performance
b) Ability to customize tool names, descriptions, and add callbacks
c) Required for proper functioning
d) Automatic error handling

**38. When does the on_handoff callback execute?**
a) After the handoff completes
b) Before the handoff tool is called
c) When the handoff tool is invoked
d) During LLM generation

**39. What is the purpose of input_filter in handoffs?**
a) To validate handoff inputs
b) To modify conversation history passed to the next agent
c) To encrypt sensitive data
d) To compress data

**40. Which handoff input filter removes all tool calls from history?**
a) handoff_filters.clean_history
b) handoff_filters.remove_all_tools
c) handoff_filters.strip_tools
d) handoff_filters.clear_tools

**41. What happens to conversation history when a handoff occurs by default?**
a) History is cleared
b) Only the last message is passed
c) The new agent sees the entire previous conversation history
d) Only user messages are passed

**42. How should you handle handoffs that need additional data from the LLM?**
a) Use string parameters
b) Define input_type with a Pydantic model
c) Use context variables
d) Pass in tool descriptions

**43. What is the recommended approach for handoff tool naming?**
a) Use generic names like "handoff_tool"
b) Use descriptive names that indicate the target agent's purpose
c) Use numeric IDs
d) Use UUID-based names

**44. When might you want to customize handoff tool descriptions?**
a) To improve LLM understanding of when to use the handoff
b) For debugging purposes
c) To reduce token usage
d) For compliance requirements

**45. What is the difference between handoffs and agents-as-tools?**
a) Handoffs transfer control, agents-as-tools delegate tasks while maintaining control
b) They are identical
c) Handoffs are synchronous, agents-as-tools are asynchronous
d) Handoffs are deprecated

**46. How do you create a handoff with custom tool name and description?**
a) Use Agent.create_handoff()
b) Use handoff() function with overrides
c) Subclass HandoffTool
d) Use HandoffBuilder

**47. What constraint applies to handoff input types?**
a) Must be strings
b) Must be Pydantic models
c) Must be serializable
d) Must be TypedDict

**48. When should you use handoff_filters.remove_all_tools?**
a) When the next agent doesn't need tool history
b) To improve performance
c) To save memory
d) For security reasons

**49. What is the recommended pattern for handoff prompts?**
a) Use generic prompts
b) Use RECOMMENDED_PROMPT_PREFIX or prompt_with_handoff_instructions
c) Don't use specific prompts
d) Use tool-specific prompts

**50. How do you handle handoff scenarios where the target agent needs specific initialization?**
a) Use context in on_handoff callback
b) Use agent.initialize()
c) Use handoff preprocessing
d) Use agent lifecycle hooks

### Section 5: Multi-Agent Orchestration Patterns (Questions 51-60)

**51. What is the primary tradeoff between LLM-based orchestration and code-based orchestration?**
a) Speed vs. accuracy
b) Intelligence/flexibility vs. determinism/predictability
c) Cost vs. performance
d) Complexity vs. simplicity

**52. When should you prefer code-based orchestration over LLM-based orchestration?**
a) When tasks are open-ended
b) When you need deterministic, predictable workflows
c) When you have unlimited budget
d) When you need maximum intelligence

**53. What is a key tactic for successful LLM-based orchestration?**
a) Use generic prompts
b) Have specialized agents that excel at single tasks
c) Avoid error handling
d) Use simple workflows

**54. Which Python primitive is recommended for running multiple agents in parallel?**
a) threading.Thread
b) multiprocessing.Process
c) asyncio.gather
d) concurrent.futures

**55. What pattern is recommended for iterative improvement workflows?**
a) Single agent with multiple tools
b) Agent in while loop with evaluator agent providing feedback
c) Sequential agent chain
d) Parallel agent execution

**56. When should you use structured outputs in orchestration?**
a) Never, always use plain text
b) When you need to inspect LLM output with code for routing decisions
c) Only for final outputs
d) For all intermediate steps

**57. What is the recommended approach for decomposing complex tasks like blog post writing?**
a) Use a single general-purpose agent
b) Chain multiple specialized agents (research → outline → write → critique → improve)
c) Use parallel execution for all steps
d) Use handoffs exclusively

**58. How should you handle agent workflows that need evaluation criteria?**
a) Hard-code evaluation logic
b) Use an evaluator agent that provides feedback until criteria are met
c) Use external evaluation services
d) Skip evaluation

**59. What is the benefit of using evals in LLM orchestration?**
a) Faster execution
b) Lower costs
c) Training agents to improve at specific tasks
d) Simpler code

**60. When might you combine LLM and code orchestration patterns?**
a) Never, they are mutually exclusive
b) Use LLM for high-level planning, code for deterministic execution
c) Always use both for redundancy
d) Only in testing environments

### Section 6: Results, Streaming, and Execution (Questions 61-70)

**61. What is the difference between RunResult and RunResultStreaming?**
a) RunResult is for sync, RunResultStreaming is for async
b) RunResult is returned by run/run_sync, RunResultStreaming by run_streamed
c) RunResult is for single agents, RunResultStreaming for multi-agent
d) They are identical

**62. Why is final_output typed as Any in RunResult?**
a) For performance reasons
b) Because of handoffs - any agent might be the last agent
c) To maintain backward compatibility
d) To allow dynamic typing

**63. What is the purpose of result.to_input_list()?**
a) To convert outputs to strings
b) To concatenate original input with generated items for next turn
c) To serialize the result
d) To create backup copies

**64. Which RunItem type indicates that the LLM called a handoff tool?**
a) HandoffItem
b) HandoffCallItem
c) TransferItem
d) AgentCallItem

**65. What information can you extract from ToolCallOutputItem?**
a) Only the tool name
b) Tool output and the tool that was called
c) Only the raw output
d) Tool parameters only

**66. In streaming, what is the difference between raw_response_event and run_item_stream_event?**
a) Raw events are token-by-token, run_item events are complete items
b) Raw events are for tools, run_item events are for messages
c) Raw events are synchronous, run_item events are asynchronous
d) They are identical

**67. What triggers the agent loop to end?**
a) Max tokens reached
b) LLM returns final_output with no tool calls
c) User interruption
d) Time limit exceeded

**68. What exception is raised when max_turns is exceeded?**
a) MaxIterationsExceeded
b) MaxTurnsExceeded
c) TurnLimitError
d) AgentLoopError

**69. When does the agent loop update the current agent?**
a) After each LLM call
b) When a handoff occurs
c) After each tool call
d) At the beginning of each turn

**70. What is the recommended approach for handling long-running conversations?**
a) Use single run with large input
b) Use to_input_list() to chain multiple runs
c) Store conversation in database
d) Use session management

### Section 7: Tools and Function Integration (Questions 71-80)

**71. What is the primary advantage of hosted tools over function tools?**
a) Hosted tools are faster
b) Hosted tools run on LLM servers alongside models
c) Hosted tools are free
d) Hosted tools are more secure

**72. Which hosted tool would you use for accessing proprietary documents?**
a) WebSearchTool
b) FileSearchTool with vector_store_ids
c) ComputerTool
d) CodeInterpreterTool

**73. What happens when you use @function_tool on a function with a context parameter?**
a) The context is ignored
b) The context must be the first parameter and receives RunContextWrapper
c) An error is raised
d) The context is passed as a tool parameter

**74. How does the SDK generate JSON schema for function tools?**
a) Manual specification required
b) Automatically from function signatures using inspect and Pydantic
c) Uses OpenAPI specification
d) Requires separate schema files

**75. What is the purpose of failure_error_function in function tools?**
a) To handle network failures
b) To provide error responses to LLM when tool calls crash
c) To validate tool inputs
d) To log errors

**76. When should you use agents as tools instead of handoffs?**
a) When you want to transfer control
b) When you want a central agent to orchestrate specialized agents while maintaining control
c) When you need better performance
d) When you need simpler code

**77. What is the benefit of custom_output_extractor in agent tools?**
a) Better performance
b) Ability to modify sub-agent output before returning to central agent
c) Automatic error handling
d) Reduced memory usage

**78. How should you handle tool calls that need to access external APIs?**
a) Make synchronous calls
b) Use async functions and proper error handling
c) Cache all responses
d) Use polling mechanisms

**79. What is the recommended approach for tools that need configuration?**
a) Use global variables
b) Pass configuration through context
c) Use environment variables exclusively
d) Hard-code configuration

**80. When might you create a custom FunctionTool instead of using @function_tool?**
a) For better performance
b) When you need full control over schema, validation, and invocation
c) When using async functions
d) When working with external APIs

### Section 8: Advanced Topics (Questions 81-90)

**81. What is the primary purpose of tracing in the Agents SDK?**
a) Performance monitoring only
b) Comprehensive debugging, visualization, and monitoring of agent workflows
c) Error logging only
d) Cost tracking only

**82. What is the relationship between traces and spans in the tracing system?**
a) They are identical
b) Traces contain multiple spans representing operations with start/end times
c) Spans contain multiple traces
d) They are unrelated

**83. How do you disable tracing for sensitive applications?**
a) Set OPENAI_AGENTS_DISABLE_TRACING=1 or RunConfig.tracing_disabled=True
b) Use trace.disable()
c) Set tracing=False in agent config
d) Remove tracing imports

**84. What is the difference between add_trace_processor() and set_trace_processors()?**
a) They are identical
b) add_trace_processor adds additional processors, set_trace_processors replaces default
c) One is for sync, one is for async
d) One is deprecated

**85. When should you use custom span creation?**
a) Never, it's automatic
b) For tracking custom operations not covered by default spans
c) Only for debugging
d) For performance optimization

**86. What is the recommended approach for handling trace metadata?**
a) Store in global variables
b) Pass through RunConfig.trace_metadata
c) Use environment variables
d) Hard-code in spans

**87. How do you group related traces across multiple agent runs?**
a) Use the same trace_id
b) Use the same group_id
c) Use the same workflow_name
d) Use trace linking

**88. What is the purpose of trace_include_sensitive_data configuration?**
a) To improve performance
b) To control whether LLM inputs/outputs and tool data are captured
c) To enable debugging
d) To reduce storage costs

**89. When implementing custom trace processors, what interface must you implement?**
a) TraceHandler
b) TraceProcessor
c) SpanExporter
d) The interface depends on your backend

**90. What is the recommended pattern for production tracing?**
a) Disable all tracing
b) Use workflow_name, group_id for conversations, and custom metadata
c) Only log errors
d) Use minimal tracing

### Answer Key

1. c) Both RunContextWrapper[T] and Agent[T]
2. b) It automatically resets to "auto"
3. c) "optional"
4. b) The tool output becomes the final response without further LLM processing
5. a) They control different aspects of tool usage flow
6. b) AgentHooks
7. c) Any agent property
8. b) Set tool_choice="none"
9. b) Setting any output_type parameter
10. c) They must all use the same type
11. c) Permits flexible output structures
12. b) Use dynamic instructions with context
13. b) model_settings provides tuning parameters for the specified model
14. b) Use dynamic instructions with context
15. a) Dynamic instructions take precedence
16. b) Local context is not sent to LLM, LLM context is conversation history
17. a) Instructions for always-useful info, tools for on-demand data
18. b) wrapper.context
19. b) Use dynamic instructions
20. b) Pass dependencies in context object
21. a) All tools must use the same context type
22. b) Pass in context object
23. b) Retrieval provides grounding with relevant contextual data
24. a) For real-time information
25. b) Pass database connection in context
26. c) To validate input/output and potentially stop expensive operations
27. c) Before agent starts, only for the first agent
28. a) GuardrailFunctionOutput with tripwire_triggered=True
29. b) InputGuardrailTripwireTriggered exception is raised
30. b) Because guardrails are agent-specific and colocated code improves readability
31. b) Use Runner.run with the guardrail agent
32. b) After the final agent output, only for the last agent
33. b) Additional output_info for logging/debugging
34. b) Define guardrails on each specific agent
35. b) Use async functions in guardrail implementation
36. b) As tools with names like "transfer*to*<agent_name>"
37. b) Ability to customize tool names, descriptions, and add callbacks
38. c) When the handoff tool is invoked
39. b) To modify conversation history passed to the next agent
40. b) handoff_filters.remove_all_tools
41. c) The new agent sees the entire previous conversation history
42. b) Define input_type with a Pydantic model
43. b) Use descriptive names that indicate the target agent's purpose
44. a) To improve LLM understanding of when to use the handoff
45. a) Handoffs transfer control, agents-as-tools delegate tasks while maintaining control
46. b) Use handoff() function with overrides
47. b) Must be Pydantic models
48. a) When the next agent doesn't need tool history
49. b) Use RECOMMENDED_PROMPT_PREFIX or prompt_with_handoff_instructions
50. a) Use context in on_handoff callback
51. b) Intelligence/flexibility vs. determinism/predictability
52. b) When you need deterministic, predictable workflows
53. b) Have specialized agents that excel at single tasks
54. c) asyncio.gather
55. b) Agent in while loop with evaluator agent providing feedback
56. b) When you need to inspect LLM output with code for routing decisions
57. b) Chain multiple specialized agents (research → outline → write → critique → improve)
58. b) Use an evaluator agent that provides feedback until criteria are met
59. c) Training agents to improve at specific tasks
60. b) Use LLM for high-level planning, code for deterministic execution
61. b) RunResult is returned by run/run_sync, RunResultStreaming by run_streamed
62. b) Because of handoffs - any agent might be the last agent
63. b) To concatenate original input with generated items for next turn
64. b) HandoffCallItem
65. b) Tool output and the tool that was called
66. a) Raw events are token-by-token, run_item events are complete items
67. b) LLM returns final_output with no tool calls
68. b) MaxTurnsExceeded
69. b) When a handoff occurs
70. b) Use to_input_list() to chain multiple runs
71. b) Hosted tools run on LLM servers alongside models
72. b) FileSearchTool with vector_store_ids
73. b) The context must be the first parameter and receives RunContextWrapper
74. b) Automatically from function signatures using inspect and Pydantic
75. b) To provide error responses to LLM when tool calls crash
76. b) When you want a central agent to orchestrate specialized agents while maintaining control
77. b) Ability to modify sub-agent output before returning to central agent
78. b) Use async functions and proper error handling
79. b) Pass configuration through context
80. b) When you need full control over schema, validation, and invocation
81. b) Comprehensive debugging, visualization, and monitoring of agent workflows
82. b) Traces contain multiple spans representing operations with start/end times
83. a) Set OPENAI_AGENTS_DISABLE_TRACING=1 or RunConfig.tracing_disabled=True
84. b) add_trace_processor adds additional processors, set_trace_processors replaces default
85. b) For tracking custom operations not covered by default spans
86. b) Pass through RunConfig.trace_metadata
87. b) Use the same group_id
88. b) To control whether LLM inputs/outputs and tool data are captured
89. d) The interface depends on your backend
90. b) Use workflow_name, group_id for conversations, and custom metadata

---

**Scoring Guide:**

-   90-80: Expert level understanding
-   79-70: Advanced level understanding
-   69-60: Intermediate level understanding
-   59-50: Basic level understanding
-   Below 50: Needs more study

This quiz tests deep understanding of the OpenAI Agents SDK concepts, practical implementation knowledge, and critical thinking about when to use different features and patterns.
