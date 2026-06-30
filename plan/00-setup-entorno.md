# Fase 00 — Setup del entorno y estructura

## Objetivo
Dejar el repo listo para desarrollar: estructura `backend/` y `frontend/`, PostgreSQL local,
control de variables de entorno y `.gitignore`.

## Pasos
1. Crear proyecto **Laravel** en `backend/` (última versión). (listo)
2. Crear proyecto **React + TypeScript + Vite** en `frontend/`. (listo)
3. Configurar **PostgreSQL** local: crear base de datos `encuesta_simple` y usuario de desarrollo. (listo)
4. Crear `backend/.env.example` y `frontend/.env.example` (sin secretos reales). (listo)
5. Crear carpeta `logs/` para logs de errores del backend. (listo — Laravel ya usa
   `backend/storage/logs/laravel.log` por defecto, no se necesita carpeta aparte).
6. Revisar/ajustar `.gitignore`: ignorar `.env`, `vendor/`, `node_modules/`, `backend/storage/*`,
   builds del frontend. **Nunca** subir `.env`. (listo — `backend/.gitignore` ya cubría todo;
   se agregó protección de `.env` en `frontend/.gitignore`, que solo tenía `*.local`).
7. Documentar comandos de arranque (dev) en `CLAUDE.md` (sección Comandos, hoy vacía). (listo)

## Archivos a tocar
- `backend/` (scaffold Laravel), `frontend/` (scaffold Vite).
- `backend/.env.example`, `frontend/.env.example`, `.gitignore`, `logs/`, `CLAUDE.md`.

## Criterio de "hecho"
- `php artisan serve` levanta el backend; `npm run dev` levanta el frontend.
- Conexión a PostgreSQL OK (`php artisan migrate` corre sin error con migraciones base).
- No hay `.env` versionado.

## Tests
- Sin tests de app todavía; verificar que `php artisan test` y `npm test` ejecutan el runner.

## Notas
- ⚠️ Instalar Laravel/Vite implica dependencias → **avisar antes** (regla de `CLAUDE.md`).
- Actualizar `context/context_backend.md` y `context/context_frontend.md` al terminar.
