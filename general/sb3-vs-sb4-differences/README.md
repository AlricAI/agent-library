# Sb3 Vs Sb4 Differences

> This document captures the meaningful differences between Spring Boot 3.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Spring Boot 3.x vs Spring Boot 4.x — Livewire compatibility notes

This document captures the meaningful differences between Spring Boot 3.x (Spring Framework 6,
Hibernate 6) and Spring Boot 4.x (Spring Framework 7, Hibernate 7) that affect Livewire's
implementation or behaviour. It is written from a Livewire-internals perspective and is
intended to guide future development when adding support for new Spring Boot versions.

**Tested combinations:**

| Label | Spring Boot | Spring Framework | Hibernate | Jackson |
|---|---|---|---|---|
| **SB3** | 3.5.x | 6.x | 6.x | Jackson 2 (`com.fasterxml.jackson`) |
| **SB4** | 4.0.x | 7.x | 7.x | Jackson 3 (`tools.jackson`) |

---

## 1. JSON serialization — HTTP message converter split

This is the most impactful difference for Livewire.

### What changed

Spring Framework 7 introduced first-class support for **Jackson 3**, which lives in a completely
different Java package (`tools.jackson.*`) compared to Jackson 2 (`com.fasterxml.jackson.*`).
As part of this, the Spring HTTP message converter for JSON was renamed and re-implemented:

|  | SB3 / Spring Framework 6 | SB4 / Spring Framework 7 |
|---|---|---|
| Converter class | `org.springframework.http.converter.json.MappingJackson2HttpMessageConverter` | `org.springframework.http.converter.json.JacksonJsonHttpMessageConverter` |
| Mapper class | `com.fasterxml.jackson.databind.ObjectMapper` | `tools.jackson.databind.json.JsonMapper` |
| Get mapper from converter | `.getObjectMapper()` | `.getMapper()` |
| `MappingJackson2HttpMessageConverter` on SB4 | present but `@Deprecated(forRemoval=true)` since Spring Framework 7.0 | — |

The old `MappingJackson2HttpMessageConverter` is still present in SB4 (deprecated), meaning
a hard import of the **old** class would compile and run on both. However, that class is
scheduled for removal in Spring Framework 7.2, so it is not a viable long-term strategy.

### Livewire's original behaviour

`mvc.clj` originally hard-imported `JacksonJsonH

*[truncated — see source for full prompt]*