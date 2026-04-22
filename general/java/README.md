# Java

> This document defines how we write Java.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Java Clean Code Best Practices

This document defines how we write Java.
The goal is code that reads like plain English, is easy to test, easy to reason about, and hard to misuse.

These rules are inspired by Clean Code principles and adapted for modern Java, Lombok, and production systems.

---

## 1. Prefer positive conditions first

Conditions should read naturally and avoid mental negation.

Bad

```java
if (isEnabled == false) {
  return;
}
```

Good

```java
if (!isEnabled) {
  return;
}
```

Better when the happy path is primary

```java
if (isEnabled) {
  start();
}
```

Avoid `== true` and `== false`.
Booleans already express intent.

### Null handling

If null is invalid, fail fast.

```java
Objects.requireNonNull(user, "user must not be null");
```

If absence is expected, model it explicitly.

```java
Optional<User> user = repository.findById(id);
user.ifPresent(this::sendEmail);
```

Avoid inverted null checks.

```java
if (user != null) { ... }
```

---

## 2. Return early

Handle invalid or edge cases immediately.
Keep the main logic flat and visible.

Bad

```java
if (order != null) {
  if (!order.isEmpty()) {
    if (order.hasPayment()) {
      charge(order);
    }
  }
}
```

Good

```java
Objects.requireNonNull(order, "order must not be null");
if (order.isEmpty()) {
  return;
}
if (!order.hasPayment()) {
  return;
}
charge(order);
```

The happy path should not be nested.

---

## 3. Avoid nested conditionals. Write flat code

Deep nesting hides intent and increases cognitive load.

Bad

```java
if (user.isActive()) {
  if (user.hasEmail()) {
    if (preferences.isMarketingEnabled()) {
      sendEmail(user);
    }
  }
}
```

Good

```java
if (!shouldSendMarketingEmail(user, preferences)) {
  return;
}
sendEmail(user);
```

```java
private boolean shouldSendMarketingEmail(User user, Preferences preferences) {
  return user.isActive()
      && user.hasEmail()
      && preferences.isMarketingEnabled();
}
```

---

## 4. Prefer immutability and Lomb

*[truncated — see source for full prompt]*