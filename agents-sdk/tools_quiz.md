# Advanced Quiz: Tools in Agent Frameworks

## Step 1: Real-World Use Cases

1. **Data Retrieval and Web Search**: Using hosted tools to fetch external information.
2. **Custom Business Logic**: Wrapping Python functions as tools for domain-specific actions.
3. **Agent Orchestration**: Using agents as tools for modular, multi-agent workflows.
4. **Automated File and Computer Operations**: Leveraging built-in tools for file search, code execution, and automation.
5. **Error Handling and Robustness**: Managing tool failures and customizing error responses.
6. **Schema-Driven Validation**: Ensuring correct tool input/output via automatic schema extraction.
7. **Custom Output Processing**: Extracting, transforming, or validating tool outputs before returning to the agent.
8. **Advanced Tool Chaining**: Composing tools and agents for complex, multi-step tasks.
9. **Integration with External APIs**: Creating tools that call out to third-party services.
10. **Security and Permissions**: Controlling access and behavior of tools in sensitive environments.

---

## Scenario-Based, Multi-Step Questions

### **Scenario 1: Hosted Tools and Data Retrieval**

#### **Q1.1**

You want your agent to answer questions using both web search and a private vector store. Which tools should you add to the agent?

A. Only `WebSearchTool`
B. `WebSearchTool` and `FileSearchTool`
C. Only `FileSearchTool`
D. `CodeInterpreterTool` and `ComputerTool`

#### **Q1.2**

If you want to limit the number of results from a vector store search, which parameter should you set on `FileSearchTool`?

A. `max_num_results`
B. `vector_store_ids`
C. `tool_name`
D. `directory`

#### **Q1.3**

Which hosted tool allows the agent to execute code in a sandboxed environment?

A. `WebSearchTool`
B. `CodeInterpreterTool`
C. `ComputerTool`
D. `ImageGenerationTool`

---

### **Scenario 2: Function Tools and Custom Logic**

#### **Q2.1**

You want to expose a Python function as a tool for your agent. What is the simplest way to do this?

A. Subclass `FunctionTool` manually
B. Decorate the function with `@function_tool`
C. Use `@staticmethod`
D. Only use built-in tools

#### **Q2.2**

How does the SDK determine the schema for a function tool's arguments?

A. By running the function
B. By parsing the function's type annotations and docstring
C. By asking the user
D. By using only the function name

#### **Q2.3**

If you want to override the tool's name and description, how can you do this?

A. Only by changing the function name
B. By passing `name_override` and a custom docstring to `@function_tool`
C. By editing the agent's instructions
D. By subclassing `Agent`

#### **Q2.4**

What is the benefit of including the context (`ctx`) as the first argument to a function tool?

A. It allows the tool to access the agent's context and dependencies
B. It is required for all tools
C. It disables docstring parsing
D. It makes the tool synchronous only

---

### **Scenario 3: Agents as Tools and Orchestration**

#### **Q3.1**

You want a central agent to use specialized translation agents as tools, rather than handing off control. What method should you use?

A. `agent.as_tool()`
B. `agent.clone()`
C. `function_tool`
D. `Runner.run()`

#### **Q3.2**

If you want to customize the output of a tool-agent before returning it to the central agent, what argument should you provide to `as_tool()`?

A. `custom_output_extractor`
B. `max_turns`
C. `tool_name`
D. `params_json_schema`

#### **Q3.3**

What is a limitation of using `agent.as_tool()` compared to running the agent directly?

A. You cannot set `max_turns` or advanced run configs
B. You cannot use custom output extractors
C. You cannot use function tools
D. You cannot use hosted tools

#### **Q3.4**

For advanced orchestration, how can you run an agent as a tool with custom configs?

A. Call `Runner.run()` inside a function tool implementation
B. Use only built-in tools
C. Use `agent.as_tool()` with `max_turns`
D. Use `FileSearchTool` only

---

### **Scenario 4: Error Handling and Robustness**

#### **Q4.1**

If a function tool call crashes, what is the default behavior?

A. The error is silently ignored
B. The LLM receives a default error message
C. The agent stops running
D. The error is logged but not returned

#### **Q4.2**

How can you provide a custom error response to the LLM when a tool call fails?

A. Pass a `failure_error_function` to `@function_tool`
B. Only use the default error handler
C. Raise an exception in the agent
D. Use `custom_output_extractor`

#### **Q4.3**

If you want tool call errors to be re-raised for manual handling, what should you do?

A. Pass `None` as the `failure_error_function`
B. Always use the default error handler
C. Only use hosted tools
D. Use `max_turns=0`

#### **Q4.4**

When manually creating a `FunctionTool`, where should you handle errors?

A. Inside the `on_invoke_tool` function
B. In the agent's instructions
C. In the tool's docstring
D. In the agent's context

---

### **Scenario 5: Schema Extraction, Validation, and Advanced Patterns**

#### **Q5.1**

What Python module is used to extract the function signature and argument types for schema creation?

A. `inspect`
B. `os`
C. `json`
D. `asyncio`

#### **Q5.2**

Which docstring formats are supported for extracting argument descriptions?

A. Only Google
B. Google, Sphinx, and Numpy
C. Only Sphinx
D. Only Numpy

#### **Q5.3**

If you want to disable docstring parsing for a function tool, what should you do?

A. Set `use_docstring_info=False` in `@function_tool`
B. Remove the docstring
C. Use only built-in tools
D. Set `max_turns=0`

#### **Q5.4**

You want to create a tool that returns only a specific JSON payload from a sub-agent's output. What feature should you use?

A. `custom_output_extractor` in `as_tool()`
B. `failure_error_function`
C. `params_json_schema`
D. `max_num_results`

---

## Answer Key with Explanations

**Q1.1**  
Correct Answer: B  
Explanation: Both `WebSearchTool` and `FileSearchTool` are needed for web and vector store search.

**Q1.2**  
Correct Answer: A  
Explanation: `max_num_results` limits the number of results in `FileSearchTool`.

**Q1.3**  
Correct Answer: B  
Explanation: `CodeInterpreterTool` allows code execution in a sandboxed environment.

**Q2.1**  
Correct Answer: B  
Explanation: `@function_tool` is the simplest way to expose a Python function as a tool.

**Q2.2**  
Correct Answer: B  
Explanation: The SDK uses type annotations and docstrings to build the schema.

**Q2.3**  
Correct Answer: B  
Explanation: Use `name_override` and a custom docstring to override name and description.

**Q2.4**  
Correct Answer: A  
Explanation: Including context allows the tool to access dependencies and state.

**Q3.1**  
Correct Answer: A  
Explanation: `agent.as_tool()` turns an agent into a tool for orchestration.

**Q3.2**  
Correct Answer: A  
Explanation: `custom_output_extractor` lets you process the output before returning it.

**Q3.3**  
Correct Answer: A  
Explanation: `agent.as_tool()` does not support all advanced configs like `max_turns`.

**Q3.4**  
Correct Answer: A  
Explanation: For advanced configs, run the agent inside a function tool using `Runner.run()`.

**Q4.1**  
Correct Answer: B  
Explanation: By default, the LLM receives a standard error message if a tool call fails.

**Q4.2**  
Correct Answer: A  
Explanation: Pass a `failure_error_function` to customize error responses.

**Q4.3**  
Correct Answer: A  
Explanation: Passing `None` re-raises tool call errors for manual handling.

**Q4.4**  
Correct Answer: A  
Explanation: Errors must be handled inside `on_invoke_tool` for manual `FunctionTool` objects.

**Q5.1**  
Correct Answer: A  
Explanation: The `inspect` module is used for signature and type extraction.

**Q5.2**  
Correct Answer: B  
Explanation: Google, Sphinx, and Numpy docstring formats are supported.

**Q5.3**  
Correct Answer: A  
Explanation: Set `use_docstring_info=False` to disable docstring parsing.

**Q5.4**  
Correct Answer: A  
Explanation: Use `custom_output_extractor` to extract specific payloads from sub-agent output.

---

# End of Quiz
