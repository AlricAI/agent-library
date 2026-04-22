# Openai Java

> The OpenAI Java SDK provides convenient access to the OpenAI REST API from Java applications.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# OpenAI Java SDK

The OpenAI Java SDK provides convenient access to the OpenAI REST API from Java applications. It offers a type-safe, immutable, and builder-pattern-based interface for interacting with OpenAI's language models, embeddings, image generation, video generation, audio transcription, content moderation, and other AI services. The SDK supports both synchronous and asynchronous execution, streaming responses, structured outputs with JSON schemas, function calling, file uploads, webhook verification, and comprehensive error handling.

The library is designed for Java 8+ and uses OkHttp as its default HTTP client, though it supports custom HTTP implementations. It includes special features like automatic pagination, retry logic with exponential backoff, connection pooling, and Azure OpenAI integration. The SDK follows semantic versioning and provides extensive configuration options through builders, environment variables, and Spring Boot integration for enterprise applications.

## Chat Completions API

Generate conversational AI responses using OpenAI's chat models with customizable parameters.

```java
import com.openai.client.OpenAIClient;
import com.openai.client.okhttp.OpenAIOkHttpClient;
import com.openai.models.ChatModel;
import com.openai.models.chat.completions.ChatCompletion;
import com.openai.models.chat.completions.ChatCompletionCreateParams;

// Initialize client using OPENAI_API_KEY environment variable
OpenAIClient client = OpenAIOkHttpClient.fromEnv();

// Build request parameters with user and developer messages
ChatCompletionCreateParams params = ChatCompletionCreateParams.builder()
    .model(ChatModel.GPT_5_2)
    .maxCompletionTokens(2048)
    .addDeveloperMessage("Make sure you mention Stainless!")
    .addUserMessage("Tell me a story about building the best SDK!")
    .build();

// Execute synchronous request and process response
ChatCompletion completion = client.chat().completions().create(params);
completion.choices().stream()
   

*[truncated — see source for full prompt]*