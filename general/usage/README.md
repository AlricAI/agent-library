# Usage

> ## Overview
See /Readme.md for library overview.

## Getting started
This page is the quick-start. The formal overview is in /Readme.md.

### Adding t

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Existential Library Usage

## Overview
See /Readme.md for library overview.

## Getting started
This page is the quick-start. The formal overview is in /Readme.md.

### Adding the library to your project
If you build and install the library locally, use the Maven coordinates below.

Maven:

    <dependency>
        <groupId>com.taitl</groupId>
        <artifactId>existential</artifactId>
        <version>0.0.1-SNAPSHOT</version>
    </dependency>

Gradle:

    dependencies {
        implementation "com.taitl:existential:0.0.1-SNAPSHOT"
    }

### Minimal workflow
Minimal workflow: configure rules, initiate transaction, send events. 

Configure rules:

    Ex.configure()
      .context("/app/orders/submit")
          .invariant(Order.class)
              .create(o -> o.total() > 0, "Total must be positive");

Create transaction, send events:

    Tr tr = Ex.begin("/app/orders/submit"); // <-- (1)
    try
    {
        // ...create Order...
        Ex.create(order, tr.id()); // <-- (2)
        // ...
        Ex.commit(tr); // <-- (3)
    }
    catch (Exception e)
    {
        Ex.rollback(tr); // <-- (4)
        throw e;
    }

    (1) Start a transaction to collect application events and apply the configured rules   
    (2) Notify the library about entity creation by sending 'Create' event  
    (3) Evaluate the rules that match received events, throw on violations
    (4) No rule evaluation takes place in case of a rollback

Notes:
- Configuration code may live in a separate place from transaction code, e.g. at application startup.
- After `commit()` or `rollback()`, transaction object becomes unusable.

### Creating a constraint on an entity
Constraints are created in the context of a business operation, 
such as "creating an order" or "updating an account".

    Ex.configure()
      .context("/api/accounts/update")
          .invariant(Account.class)
              .create(a -> validEmail(a.emailAddress()), "Ensure valid email address")
              .update(a -

*[truncated — see source for full prompt]*