# Query Hot Loading

> ## Context

Spring Data JPA compiles `@Query` annotations into query objects at application startup and
caches them for the lifetime of the applicatio

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Decision: How `hot-swap-query!` Patches Spring Data JPA + Hibernate

## Context

Spring Data JPA compiles `@Query` annotations into query objects at application startup and
caches them for the lifetime of the application. Changing a query normally requires a full
restart. `hot-swap-query!` eliminates this by mutating the live objects in place.

This document captures the implementation approach, the internals of the chain we patch, and
the lessons learned when the first version silently failed on Spring Data JPA 4.x / Hibernate 7.

---

## The Object Chain

When Spring Data JPA processes a `@Query`-annotated repository method, it builds the following
chain of objects and stores the root in a private map inside `QueryExecutorMethodInterceptor`:

```
QueryExecutorMethodInterceptor
  └─ Map<Method, RepositoryQuery> queries          ← keyed by java.lang.reflect.Method

       └─ SimpleJpaQuery  (implements RepositoryQuery)
            └─ [field] query: DefaultEntityQuery
                 ├─ [field] queryString: Lazy<String>   ← derived/cached query string
                 └─ [field] query: PreprocessedQuery
                      └─ [field] source: DeclaredQueries$JpqlQuery
                           └─ [field] jpql: String      ← THE string Hibernate actually reads
```

The `QueryExecutorMethodInterceptor` sits on the AOP proxy chain of every Spring Data
repository bean, at position 5 (0-indexed) among the `DefaultPointcutAdvisor` advisors.

### How to reach `QueryExecutorMethodInterceptor`

```clojure
(let [advised     (cast org.springframework.aop.framework.Advised repo)
      interceptor (->> (.getAdvisors advised)
                       (keep #(when (instance? org.springframework.aop.support.DefaultPointcutAdvisor %)
                                (.getAdvice ^org.springframework.aop.support.DefaultPointcutAdvisor %)))
                       (filter #(-> % class .getName (.contains "QueryExecutorMethodInterceptor")))
                       first)
      queries-ma

*[truncated — see source for full prompt]*