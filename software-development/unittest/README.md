# Unittest

> Your example is bad because it violates that rule and hides the flow.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
Your example is bad because it violates that rule and hides the flow.

Bad example (too many breaks, noisy spacing)

```java
@Test
void testAdd_withNullValues_shouldHandleGracefully() {
    Usage usage1 = Usage.builder()
        .inputTokens(100.0)
        .outputTokens(50.0)
        .build();

    Usage usage2 = Usage.builder()
        .requests(1.0)
        .totalTokens(150.0)
        .build();

    Usage result = usage1.add(usage2);

    assertEquals(1.0, result.getRequests());
    assertEquals(100.0, result.getInputTokens());
    assertEquals(50.0, result.getOutputTokens());
    assertEquals(150.0, result.getTotalTokens());
}
```

Why this is bad

You cannot immediately see the Act line.
The eye has to scan through multiple blank lines that add no meaning.
Spacing is not intentional. It is just empty air.

Good example with your rule
Exactly one space before and one space after the Act

```java
@Test
void add_withNullValues_handlesGracefully() {
    Usage usage1 = Usage.builder()
        .inputTokens(100.0)
        .outputTokens(50.0)
        .build();
    Usage usage2 = Usage.builder()
        .requests(1.0)
        .totalTokens(150.0)
        .build();

    Usage result = usage1.add(usage2);

    assertEquals(1.0, result.getRequests());
    assertEquals(100.0, result.getInputTokens());
    assertEquals(50.0, result.getOutputTokens());
    assertEquals(150.0, result.getTotalTokens());
}
```

The visual contract is now clear

Arrange is dense and uninterrupted
Act is isolated by exactly two spaces
Assert is dense and uninterrupted

That is AAA enforced by whitespace, not comments. We don't need any comment that is not very important
to understand code that is not well written. And NEVER add // Arrange // Act // Assert.

If a test cannot be made readable with only those two spaces, the test is too big and should be split.

## No Comments in Tests

DO NOT add comments inside tests. The code should be self-explanatory through:
- Clear variable names
- Descriptive t

*[truncated — see source for full prompt]*