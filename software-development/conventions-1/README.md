# CONVENTIONS

> This document defines all coding conventions, naming standards, and team practices for the software development team.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Software Development Team Conventions

This document defines all coding conventions, naming standards, and team practices for the software development team.

## Naming Conventions

### General Principles
- Use descriptive, self-documenting names
- Avoid abbreviations except well-known ones
- Be consistent within the codebase
- Prefer clarity over brevity

### Language-Specific Conventions

#### JavaScript/TypeScript
```javascript
// Classes: PascalCase
class UserAccount { }

// Interfaces: PascalCase with 'I' prefix (optional)
interface IUserService { }

// Functions/Methods: camelCase
function calculateTotal() { }

// Variables: camelCase
const userAge = 25;

// Constants: UPPER_SNAKE_CASE
const MAX_RETRY_COUNT = 3;

// Private members: underscore prefix
private _internalState;

// Files: kebab-case
user-service.ts
api-controller.js
```

#### Python
```python
# Classes: PascalCase
class UserAccount:
    pass

# Functions/Methods: snake_case
def calculate_total():
    pass

# Variables: snake_case
user_age = 25

# Constants: UPPER_SNAKE_CASE
MAX_RETRY_COUNT = 3

# Private members: underscore prefix
_internal_state = None

# Files: snake_case
user_service.py
api_controller.py
```

#### Java
```java
// Classes: PascalCase
public class UserAccount { }

// Interfaces: PascalCase
public interface UserService { }

// Methods: camelCase
public void calculateTotal() { }

// Variables: camelCase
int userAge = 25;

// Constants: UPPER_SNAKE_CASE
public static final int MAX_RETRY_COUNT = 3;

// Packages: lowercase
com.company.project.service

// Files: PascalCase (matching class name)
UserAccount.java
```

### Database Conventions
```sql
-- Tables: snake_case plural
CREATE TABLE users ( );
CREATE TABLE order_items ( );

-- Columns: snake_case
user_id INTEGER
created_at TIMESTAMP

-- Indexes: idx_table_column
CREATE INDEX idx_users_email ON users(email);

-- Foreign keys: fk_table_referenced
ALTER TABLE orders 
  ADD CONSTRAINT fk_orders_users 
  FOREIGN KEY (user_id) 
  REFE

*[truncated — see source for full prompt]*