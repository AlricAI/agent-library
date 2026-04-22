# Laravel 13 Backend Rules

> globs: "**/*.php" Laravel 13 Backend Rules ## Laravel 13 Structure

## Tags
`redis`

## System Prompt
---
globs: "**/*.php"
---

# Laravel 13 Backend Rules

### Laravel 13 Structure
- **bootstrap/app.php** central config (routing, middleware, exceptions)
- **Single AppServiceProvider** replaces Auth/Event/Route providers
- **No Kernel files** — configure middleware in bootstrap/app.php
- **api.php not included** — `php artisan install:api`
- **Config files removed** — `php artisan config:publish`
- `casts()` method instead of `$casts` property
- Schedule in `routes/console.php` via `Schedule` facade
- **CSRF**: Use `preventRequestForgery()` (not `validateCsrfTokens()` or `VerifyCsrfToken`)

```php
return Application::configure(basePath: dirname(__DIR__))
    ->withRouting(web: __DIR__.'/../routes/web.php', api: __DIR__.'/../routes/api.php', health: '/up')
    ->withMiddleware(fn(Middleware $m) => $m->preventRequestForgery(except: ['webhooks/*']))
    ->withExceptions(fn(Exceptions $e) => $e->shouldRenderJsonWhen(fn($r) => $r->is('api/*')))
    ->create();
```

### Architecture

**Controllers**: Thin, delegate to Services/Actions. `--invokable` for single actions.

| Services | Actions |
|----------|---------|
| Multiple methods: `UserService::create()` | Single op: `CreateUserAction::execute()` |

**Avoid Repository** — use Eloquent scopes: `scopeActive($q) { return $q->where('status', 'active'); }`

**Form Requests**: ALWAYS `$request->validated()`, never `$request->all()`

**Events vs Observers**: Events = app-level, multiple listeners. Observers = model lifecycle (sparingly).

### Eloquent Performance

**N+1 Prevention**:
```php
Model::preventLazyLoading(!app()->isProduction());
$posts = Post::with(['author:id,name', 'comments'])->get();
```

| `with()` | `load()` | `loadMissing()` |
|----------|----------|-----------------|
| Query time | After retrieval | Only if not loaded |

**Query Rules**: `->select(['id','name'])` needed columns; `->withCount('posts')` not `$user->posts->count()`; `->exists()` not `count() > 0`; `chunkById()` large datasets; `cursor()` mem

*[truncated — see source for full prompt]*