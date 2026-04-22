# Lombok

> Project Lombok is a Java library that automatically plugs into your editor and build tools to eliminate boilerplate code through annotations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Project Lombok

Project Lombok is a Java library that automatically plugs into your editor and build tools to eliminate boilerplate code through annotations. It uses annotation processing to generate common code patterns like getters, setters, constructors, builders, and more at compile-time. Lombok transforms annotated source code during compilation, modifying the Abstract Syntax Tree before final bytecode generation, ensuring zero runtime overhead while significantly reducing code verbosity.

The library integrates seamlessly with popular IDEs and build tools, providing a cleaner, more maintainable codebase. By automating repetitive coding tasks, Lombok allows developers to focus on business logic rather than mechanical code generation. It supports a wide range of Java versions and works with standard compilation processes, making it easy to adopt in existing projects without major architectural changes.

## @Getter and @Setter Annotations

Generate getter and setter methods for class fields automatically. Can be applied to individual fields or entire classes with customizable access levels.

```java
import lombok.Getter;
import lombok.Setter;
import lombok.AccessLevel;

public class User {
    @Getter @Setter private String username;
    @Getter @Setter private String email;
    @Getter private final Long id;
    @Setter(AccessLevel.PROTECTED) private String password;

    public User(Long id) {
        this.id = id;
    }
}

// Usage
User user = new User(1L);
user.setUsername("john_doe");
user.setEmail("john@example.com");
System.out.println(user.getUsername()); // Output: john_doe
System.out.println(user.getId()); // Output: 1
```

## @Builder Annotation

Creates a builder pattern implementation for flexible object construction with method chaining. Generates an inner builder class with fluent API for setting properties.

```java
import lombok.Builder;
import lombok.ToString;

@Builder
@ToString
public class Product {
    private String name;
    private doub

*[truncated — see source for full prompt]*