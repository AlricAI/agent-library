# Security

> LangChain has a large ecosystem of integrations with various external resources like local and remote file systems, APIs and databases.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Security

LangChain has a large ecosystem of integrations with various external resources like local and remote file systems, APIs and databases. These integrations allow developers to create versatile applications that combine the power of LLMs with the ability to access, interact with and manipulate external resources.

## Best Practices

When building such applications developers should remember to follow good security practices:

* [**Limit Permissions**](https://en.wikipedia.org/wiki/Principle_of_least_privilege): Scope permissions specifically to the application's need. Granting broad or excessive permissions can introduce significant security vulnerabilities. To avoid such vulnerabilities, consider using read-only credentials, disallowing access to sensitive resources, using sandboxing techniques (such as running inside a container), etc. as appropriate for your application.

* **Anticipate Potential Misuse**: Just as humans can err, so can Large Language Models (LLMs). Always assume that any system access or credentials may be used in any way allowed by the permissions they are assigned. For example, if a pair of database credentials allows deleting data, it’s safest to assume that any LLM able to use those credentials may in fact delete data.

* [**Defense in Depth**](https://en.wikipedia.org/wiki/Defense_in_depth_(computing)): No security technique is perfect. Fine-tuning and good chain design can reduce, but not eliminate, the odds that a Large Language Model (LLM) may make a mistake. It’s best to combine multiple layered security approaches rather than relying on any single layer of defense to ensure security. For example: use both read-only permissions and sandboxing to ensure that LLMs are only able to access data that is explicitly meant for them to use.

Risks of not doing so include, but are not limited to:

* Data corruption or loss.

* Unauthorized access to confidential information.

* Compromised performance or availability of critical resourc

*[truncated — see source for full prompt]*