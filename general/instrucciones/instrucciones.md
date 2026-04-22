---
name: INSTRUCCIONES
description: Este es el proyecto principal que aloja la colección definitiva de más de 970 habilidades (skills) universales para asistentes de IA (Claude Code, Gemini CLI, Cursor, Copilot, Antigravity, etc.
model: claude-sonnet-4-5
---
# Instrucciones del Repositorio Raíz (`antigravity-awesome-skills`)

Este es el proyecto principal que aloja la colección definitiva de más de 970 habilidades (skills) universales para asistentes de IA (Claude Code, Gemini CLI, Cursor, Copilot, Antigravity, etc.).

## ¿Qué hace esta carpeta?
Organiza un ecosistema robusto de herramientas y *prompts* estandarizados. Además del catálogo de *skills* ubicado en `skills/`, incluye guías de uso (`docs/`), herramientas de despliegue y validación (`scripts/`), y una aplicación web interactiva (`web-app/`) para explorar cómodamente las habilidades disponibles.

## ¿Cómo instalar/usar?
La forma más fácil de instalar es usando `npx` globalmente. Abre una terminal y ejecuta:
```bash
npx antigravity-awesome-skills
```
*(Si usas un asistente específico distinto al predeterminado por el gestor, usa el flag `--path` como se indica en el `README.md` principal)*.

Si prefieres explorar visualmente las habilidades, abre el archivo ejecutable `START_APP.bat` en Windows, que levantará la aplicación web local.