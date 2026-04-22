# Kotlin Coding Best Practices for Spring Boot Development

> Kotlin Coding Best Practices for Spring Boot Development # Project Structure and Organization 1.	Group your source code into clearly defined packages like controller, service, repository, and model to separate concerns and improve maintainability.

## System Prompt
# Kotlin Coding Best Practices for Spring Boot Development

## Project Structure and Organization

1.	Group your source code into clearly defined packages like controller, service, repository, and model to separate concerns and improve maintainability.
2.	Organize your file system so that each directory mirrors the Kotlin package name (e.g. put com.myapp.users under src/main/kotlin/com/myapp/users).
3.	Name each Kotlin file after the primary class or concept it contains to make the codebase easier to navigate and understand.
4.	Avoid vague file names like Utils.kt; instead, use concise and meaningful names that reflect the purpose of the file’s contents.
5.	Place your Spring Boot application entry point in the root package and structure sub-packages by layer or feature to help Spring scan and organize components efficiently.

## Coding Style and Conventions

1.	Use PascalCase for class and object names, camelCase for functions and variables, and UPPER_SNAKE_CASE for constants to follow Kotlin naming conventions and improve readability.
2.	Declare variables using `val` by default, and only use `var` when mutation is necessary to promote safer, more predictable code.
    ```kotlin
    val maxConnections = 10    // immutable reference
    var currentUsers = 0       // mutable, try to avoid if possible
    ```
3.	Limit the scope of variables to where they are actually used—inside functions or smaller blocks—to avoid accidental misuse and make code easier to follow.
4.	Format your code consistently using 4-space indentation, proper spacing around operators and commas, and short, focused functions to improve clarity and maintainability.
5.	Write clear and expressive code instead of clever one-liners; break complex logic into intermediate variables or well-named functions to improve readability.
6.	Name classes, functions, and variables descriptively to convey intent, and avoid vague suffixes like '-Manager' or '-Helper' that don’t add meaning.
7.	Keep property getters and

*[truncated — see source for full prompt]*