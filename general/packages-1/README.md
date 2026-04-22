# PACKAGES

> The Semantic Kernel has the packages below, all are under the groupId `com.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Semantic Kernel for Java Packages

The Semantic Kernel has the packages below, all are under the groupId `com.microsoft.semantic-kernel`, and can be imported
to maven.

```xml
    <dependency>
        <groupId>com.microsoft.semantic-kernel</groupId>
        <artifactId>semantickernel-api</artifactId>
    </dependency>
```

A BOM is provided that can be used to define the versions of all Semantic Kernel packages.

```xml
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.microsoft.semantic-kernel</groupId>
                <artifactId>semantickernel-bom</artifactId>
                <version>${semantickernel.version}</version>
                <scope>import</scope>
                <type>pom</type>
            </dependency>
        </dependencies>
    </dependencyManagement>
```

## Common Packages

`semantickernel-bom`
: A Maven project BOM that can be used to define the versions of all Semantic Kernel packages.

`semantickernel-api`
: Package that defines the core public API for the Semantic Kernel for a Maven project.

`semantickernel-core`
: The internal implementation of the Semantic Kernel API.
This package contains the core implementation of the Semantic Kernel. This must be made available to the
application at runtime. Note that these classes are considered internal and should not be used directly by the application. Should they be used directly, it could cause instability in the application as they may change without notice over time.

## Connectors

`semantickernel-connectors-ai-openai`
: Provides a connector that can be used to interact with the OpenAI API.

### Memory Connectors

#### JDBC Memory Connectors

`semantickernel-connectors-memory-jdbc`
: A package that serves as a parent for all JDBC based connectors, adding a new JDBC database should be a matter of extending the classes within this module.

Provides a memory connector that can be used to interact with a JDBC database.
- `semantickernel-connec

*[truncated — see source for full prompt]*