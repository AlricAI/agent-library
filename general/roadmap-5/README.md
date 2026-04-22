# Roadmap

> Current status and future direction for elastic-script — a procedural language for Elasticsearch inspired by Oracle PL/SQL.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Roadmap

Current status and future direction for elastic-script — a procedural language for Elasticsearch inspired by Oracle PL/SQL.

---

## ✅ Completed Features (v1.0)

### Core Language
- [x] **Procedure Creation** - `CREATE PROCEDURE ... END PROCEDURE`
- [x] **Variable System** - `DECLARE`, `VAR`, `CONST` with type inference
- [x] **Control Flow** - IF/THEN/ELSEIF/ELSE, FOR loops, WHILE loops
- [x] **Data Types** - STRING, NUMBER, BOOLEAN, ARRAY, DOCUMENT, DATE
- [x] **Functions with Parameters** - IN/OUT/INOUT parameter modes

### Built-in Functions (118 total)
- [x] **String Functions** (18) - LENGTH, SUBSTR, REPLACE, REGEXP_*, etc.
- [x] **Number Functions** (11) - ABS, ROUND, SQRT, LOG, etc.
- [x] **Array Functions** (18) - ARRAY_LENGTH, APPEND, FILTER, MAP, etc.
- [x] **Date Functions** (8) - CURRENT_DATE, DATE_ADD, EXTRACT_*, etc.
- [x] **Document Functions** (6) - DOCUMENT_GET, KEYS, VALUES, MERGE, etc.
- [x] **Elasticsearch Functions** (5) - ESQL_QUERY, ES_GET, ES_INDEX, etc.
- [x] **AI/LLM Functions** (6) - LLM_COMPLETE, LLM_SUMMARIZE, ES_INFERENCE
- [x] **Integration Functions** (~30) - Slack, PagerDuty, K8s, AWS, HTTP

### Async Execution Model
- [x] **Pipe-Driven Syntax** - `procedure() | ON_DONE handler(@result)`
- [x] **Error Continuations** - `ON_FAIL`, `FINALLY` handlers
- [x] **Parallel Execution** - `PARALLEL [proc1(), proc2()] | ON_ALL_DONE`
- [x] **Execution Control** - `EXECUTION('name') | STATUS/CANCEL/RETRY`
- [x] **State Persistence** - Execution state stored in `.escript_executions`

### First-Class Commands
- [ ] **INDEX Command** - `INDEX document INTO 'index-name';` (Planned)
- [ ] **DELETE Command** - `DELETE FROM 'index-name' WHERE id;` (Planned)
- [ ] **SEARCH Command** - `SEARCH 'index-name' QUERY {...};` (Planned)
- [ ] **REFRESH Command** - `REFRESH 'index-name';` (Planned)
- [ ] **CREATE INDEX Command** - `CREATE INDEX 'name' WITH MAPPINGS {...};` (Planned)

### Type-Aware ES|QL Binding
- [ ] **ARRAY Binding** - `DECLARE erro

*[truncated — see source for full prompt]*