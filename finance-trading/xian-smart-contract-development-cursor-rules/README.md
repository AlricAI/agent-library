# Xian Smart Contract Development - Cursor Rules

> Xian Smart Contract Development - Cursor Rules XIAN is the currency of the Xian blockchain. Never mention TAU or Lamden.

## Tags
`python`

## System Prompt
# Xian Smart Contract Development - Cursor Rules

XIAN is the currency of the Xian blockchain.
Never mention TAU or Lamden.

## Contract Structure

### Basic Structure
- Smart contracts are written in native Python without transpilation
- Contract names must follow the pattern: `^con_[a-z][a-z0-9_]*$`
- Contract names must start with 'con_' prefix (except system contracts like 'currency')
- Contract names must be lowercase, only contain letters, numbers and underscores after prefix
- Contract names must be max 64 characters

### Naming Conventions
- You cannot use '_' as a prefix for variables or functions (e.g., `_private_var` is not allowed)
- Follow standard Python naming conventions otherwise
- Use descriptive names for clarity
- A contract can not be deployed by another contract

### Function Types
- `@export` decorator defines public functions callable by any user or contract
- `@construct` decorator defines initialization function executed once at contract submission (optional)
- Functions without decorators are private and can only be called by the contract itself
- Functions with `@export` can call private functions internally

### Constructor Arguments
- Optional arguments can be provided to the `@construct` function
- Initial state can be setup using these arguments

## State Management

### Variable
- `Variable` is a way to define a singular state variable in the contract
- Use `variable.set(value)` to modify
- Use `variable.get()` to retrieve

```python
my_var = Variable()

@construct
def seed():
    my_var.set(0)  # Initialize variable

@export
def increment():
    my_var.set(my_var.get() + 1)
```

### Hash
- `Hash` is a key-value store for the contract
- Default value can be specified with `Hash(default_value=0)`
- Access through dictionary-like syntax: `hash[key] = value` and `hash[key]`
- Supports nested keys with tuple: `hash[key1, key2] = value`

```python
my_hash = Hash(default_value=0)

@export
def set_value(key: str, value: int):
    my_hash[ke

*[truncated — see source for full prompt]*