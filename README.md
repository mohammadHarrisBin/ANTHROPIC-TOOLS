# ANTHROPIC-TOOLS 🛠️

The **ANTHROPIC-TOOLS** package is a basic utility designed to simplify the usage and integration of tools within the ANTHROPIC AI SDK. It's **open source** 🌐, allowing everyone to contribute and improve its functionality.

## Installation

To install **ANTHROPIC-TOOLS**, follow these steps:

  ```
  git clone https://github.com/mohammadHarrisBin/ANTHROPIC-TOOLS.git
  ```

## Usage

Integrate it into your project following these steps:

1. **Setting up the tool**: Define your tool

    ```javascript
    // 🛠️ Tool setting
    const tool_name = "Your tool name";
    const tool_description = `Your tool description`;
    const parameters = [
      {
        "name": "title",
        "type": "string",
        "description": "The description of the parameter"
      },
      {
        "name": "title",
        "type": "string",
        "description": "The description of the parameter"
      },
    ];

    // 🛠️ Construct and format the tool for CLAUDE prompt
    const tool = await construct_format_tool_for_claude_prompt(tool_name, tool_description, parameters);

    // 🛠️ Construct system prompt for tool use
    const system_prompt = await constructToolUseSystemPrompt([tool]);
    ```

2. **Using the tool**: ANTHROPIC SDK:

    ```javascript
    // 🚀 Call the ANTHROPIC generator
    const response2 = await anthropic_generator.messages.create({
      model: "claude-2.0",
      max_tokens: 4000,
      stream: true,
      messages: [{
        role: "user",
        content: `Your prompt`
      }],
      system: system_prompt,
      stop_sequences: ["\n\nHuman:", "\n\nAssistant", "</function_calls>"]
    });

    // 🎉 Convert the response into a friendly text-stream
    const stream = AnthropicStream(response2);

    // 📜 Respond with the stream
    return new StreamingTextResponse(stream);
    ```

4. **Explanation**: This code sets up your tool and then calls it on the ANTHROPIC SDK to generate content based on the tool provided. It utilizes the ANTHROPIC-TOOLS package to simplify this process.

5. **Customization**: Customize parameters and user input message (e.g., `What is 2 + 2` ) based on your specific use case.

You're now ready to integrate ANTHROPIC-TOOLS into your project for content generation using the ANTHROPIC AI SDK.
