# Language Reference

> elastic-script is a procedural scripting language designed for Elasticsearch operations.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# elastic-script Language Reference

elastic-script is a procedural scripting language designed for Elasticsearch operations.

## Statements

### CREATE PROCEDURE

```sql
CREATE PROCEDURE procedure_name(
  param1 TYPE,
  param2 TYPE DEFAULT value,
  IN input_param TYPE,
  OUT output_param TYPE,
  INOUT both_param TYPE
)
BEGIN
  -- statements
END PROCEDURE;
```

### CREATE FUNCTION

```sql
CREATE FUNCTION function_name(param1 TYPE, param2 TYPE)
RETURNS TYPE
BEGIN
  -- statements
  RETURN value;
END FUNCTION;
```

### CREATE SKILL

```sql
CREATE SKILL skill_name
  VERSION 'semver'
  DESCRIPTION 'description for AI agents'
  [AUTHOR 'author name']
  [TAGS ['tag1', 'tag2']]
  [REQUIRES ['dependency1']]
  (param1 TYPE [DEFAULT value], ...)
  [RETURNS TYPE]
BEGIN
  -- skill body
END SKILL;
```

### CALL

```sql
CALL procedure_name(arg1, arg2);
```

### DECLARE / VAR / CONST

```sql
DECLARE variable_name TYPE;
DECLARE variable_name TYPE := initial_value;
VAR variable_name := value;
CONST constant_name := value;
```

### SET

```sql
SET variable_name = expression;
SET variable_name := expression;
```

### IF/THEN/ELSE

```sql
IF condition THEN
  -- statements
ELSEIF other_condition THEN
  -- statements
ELSE
  -- statements
END IF;
```

### FOR Loop

```sql
FOR i IN 1..10 LOOP
  -- statements
END LOOP;
```

### WHILE Loop

```sql
WHILE condition LOOP
  -- statements
END LOOP;
```

### TRY/CATCH

```sql
TRY
  -- statements that might fail
CATCH exception_variable
  -- handle error
FINALLY
  -- cleanup
END TRY;
```

### PRINT

```sql
PRINT 'Message';
PRINT variable;
PRINT 'Value is: ' || variable;
```

### RETURN

```sql
RETURN value;
RETURN {"key": "value"};
```

## Data Types

| Type | Description | Example |
|------|-------------|---------|
| `STRING` | Text | `'hello'` |
| `NUMBER` | Numeric | `42`, `3.14` |
| `BOOLEAN` | True/false | `TRUE`, `FALSE` |
| `ARRAY` | List | `[1, 2, 3]` |
| `DOCUMENT` | Object/Map | `{"key": "value"}` |

## Operators

### Arithmetic
- `+` Addi

*[truncated — see source for full prompt]*