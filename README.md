# Chain of Thought Prompting

Chain of Thought is a prompting technique that guides large language models to break down complex problems into sequential steps before producing a final answer. This approach:

- Improves reasoning capabilities
- Provides visibility into the model's thinking process
- Enhances accuracy for complex, multi-step problems
- Allows for easier error detection

## Implementation

- **Analyze**: Understand the problem
- **Think**: Break down the reasoning steps
- **Output**: Generate the solution
- **Validate**: Verify the solution
- **Result**: Present the final answer with explanation

## Other Advanced Prompting Techniques

### Self-Consistency Prompting

- Generates multiple independent reasoning paths for the same problem
- Selects the most consistent answer across different solution attempts
- Particularly effective for math and logical reasoning tasks

### Persona-Based Prompting

- Guides the model to adopt specific expert personas (e.g., "As a mathematician...")
- Leverages role-specific knowledge and problem-solving approaches
- Can improve performance in specialized domains

### Role-Play Prompting

- Instructs the model to engage in a simulated dialogue between multiple entities
- Enables exploration of different perspectives on a problem
- Useful for creative brainstorming or debating complex issues

### Tree of Thoughts

- Extends CoT by exploring multiple reasoning branches
- Allows backtracking when a reasoning path seems unproductive
- Enables more comprehensive exploration of solution spaces

### ReAct (Reasoning + Acting)

- Combines reasoning with the ability to take actions
- Alternates between thinking steps and tool/environment interactions
- Useful for tasks requiring both reasoning and external information

## System Prompt for Agent with Tooling

```json
<instruction>
    eg: You are an agent specialized in Analysis of Data
</instruction>

<rules>
    Rules:
        1. Follow the strict JSON output as per Output schema.
        2. Always perform one step at a time and wait for next input
        3. Carefully analyse the user query
</rules>

<output format>
    Output Format:
        {{ step: "string", content: "string" }}
</output format>

<available tools>
    - getWeatherData
    - getImageDescription
</available tools>

<example>
    Example:
    Input: What is 2 + 2.
    Output: {{ step: "analyse", content: "Alright! The user is intersted in maths query and he is asking a basic arthermatic operation" }}
</example>
```