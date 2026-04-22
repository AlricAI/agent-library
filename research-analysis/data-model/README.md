# Data Model

> Create comprehensive Entity Relationship Diagrams (ERDs) and data documentation for the current project.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Data Model Generation Command

Create comprehensive Entity Relationship Diagrams (ERDs) and data documentation for the current project.

## Objective

Generate complete data model documentation including:
1. **Database schemas** - Tables, relationships, constraints, indexes
2. **Service layer models** - DTOs, domain models, business logic data structures
3. **UI data structures** - Component props, state management, data flows

## Output Location

Save all documentation to: `./docs/architecture/data-model.md` (relative to current project directory)

**Important:** Auto-create the `./docs/architecture/` directory if it doesn't exist.

## Discovery Phase

Before generating documentation, perform comprehensive project analysis:

1. **Database Technology Detection**
   - Scan for Prisma schema files (`prisma/schema.prisma`)
   - Check for TypeORM entities (`*.entity.ts`, decorators like `@Entity`)
   - Look for Sequelize models (`models/*.js`, `sequelize.define`)
   - Find Mongoose schemas (`*.model.ts`, `mongoose.Schema`)
   - Detect raw SQL files (`*.sql`, `migrations/*.sql`)
   - Check for Django models (`models.py`)
   - Look for SQLAlchemy models (Python `Base.metadata`)

2. **Backend Framework Detection**
   - Next.js (check `next.config.js`, API routes in `app/api/` or `pages/api/`)
   - Express.js (check `package.json` for express, look for `app.js` or `server.js`)
   - FastAPI (check `requirements.txt`, `main.py` with `@app` decorators)
   - Django (check `settings.py`, `urls.py`)
   - NestJS (check for `@Module`, `@Controller` decorators)

3. **Frontend State Management Detection**
   - Redux (check for `createSlice`, `configureStore`)
   - Zustand (check for `create` from zustand)
   - Context API (check for `createContext`, `useContext`)
   - React Query (check for `useQuery`, `useMutation`)
   - MobX (check for `makeObservable`, `@observable`)
   - Jotai (check for `atom` from jotai)

4. **Service Layer Patterns**
   - Repository pattern (look for `*.repo

*[truncated — see source for full prompt]*