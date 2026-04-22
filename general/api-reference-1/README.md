# Api Reference

> This document provides a reference for the various APIs and interfaces used in CycoD.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# API Reference

This document provides a reference for the various APIs and interfaces used in CycoD.

## Chat Client API

The Chat Client API is responsible for handling communication with AI service providers.

### ChatClientFactory

```csharp
// Creates chat clients based on configuration
static class ChatClientFactory {
    // Creates a chat client instance based on available environment variables
    public static ChatClient CreateChatClientFromEnv();
    
    // Creates an OpenAI chat client
    public static ChatClient CreateOpenAIChatClient();
    
    // Creates an Azure OpenAI chat client
    public static ChatClient CreateAzureOpenAIChatClient();
    
    // Creates a GitHub Copilot chat client with token authentication
    public static ChatClient CreateCopilotChatClientWithToken();
}
```

### FunctionCallingChat

```csharp
// Main chat client class that handles communication with AI models
class FunctionCallingChat {
    // Constructor
    public FunctionCallingChat(ChatClient openAIClient, string systemPrompt, FunctionFactory factory);
    
    // Clears the chat history
    public void ClearChatHistory();
    
    // Loads chat history from a file
    public void LoadChatHistory(string fileName);
    
    // Gets a streaming chat completion and handles function calls
    public async Task<string> CompleteChatStreamingAsync(
        string userPrompt,
        Action<IList<ChatMessage>>? messageCallback = null,
        Action<StreamingChatCompletionUpdate>? streamingCallback = null,
        Action<string, string, string?>? functionCallCallback = null);
}
```

## Function Calling API

The Function Calling API provides mechanisms to define and execute tools that the AI can use.

### FunctionFactory

```csharp
// Creates function definitions from helper classes
public class FunctionFactory {
    // Constructors
    public FunctionFactory();
    public FunctionFactory(Assembly assembly);
    public FunctionFactory(Type type);
    public FunctionFactory(Typ

*[truncated — see source for full prompt]*