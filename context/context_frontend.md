# Contexto Frontend — Encuesta sobre la atención

> Estado vivo del frontend. Actualizar en cada cambio (regla de `CLAUDE.md`).

## Estado actual
- **Fase 00 (setup) completada.** `frontend/` existe y corre.
- Proyecto generado con `npm create vite@latest -- --template react-ts`: **React 19.2**,
  **TypeScript ~6.0**, **Vite 8.1**. `npm install` corrido, 0 vulnerabilidades. Scaffold base
  de Vite (`src/App.tsx`, `src/main.tsx`), aún sin router, servicios ni componentes propios.
- Roadmap de construcción en `plan/` (fases 00–11). Fase 00: ver `plan/00-setup-entorno.md`
  (los 7 pasos están marcados `(listo)`).
- **`.env.example`** creado con `VITE_API_URL=http://localhost:8000/api` (apunta al backend
  Laravel local, prefijo `/api` que se define en la Fase 01 del backend).
- **`.gitignore`**: el scaffold de Vite solo ignoraba `*.local` (no cubría `.env` a secas).
  Se agregó bloque explícito `.env` / `.env.*` / `!.env.example`, verificado con
  `git check-ignore`.
- **Jest + React Testing Library**: todavía **no instalados/configurados**. No hay test
  runner funcionando aún (`npm test` no existe en `package.json`); se configura en la
  Fase 06/07 cuando se creen los primeros componentes.
- **Comandos de desarrollo** documentados en la raíz `CLAUDE.md` (sección Comandos):
  `npm install`, `npm run dev`, `npm run build`, `npm run lint`.

## Stack
- React + **TypeScript** + **Vite** (SPA).
- Tests: **Jest** + **React Testing Library** (pendiente de instalar), **junto a cada componente**
  (`Componente/Componente.tsx` + `Componente/Componente.test.tsx`).

## Estructura prevista (de `CLAUDE.md`)
- `src/components/` — componentes reutilizables (cada uno con su test al lado).
- `src/pages/` — vistas principales (Login, Registro, Perfil, Encuesta, Admin).
- `src/services/` — llamadas a la API (axios): `apiClient`, `authService`, `encuestaService`,
  `adminService`.

## Flujos previstos (ver `plan/07`, `plan/08`, `plan/09`)
- **Auth**: registro, login, perfil (editar), logout, eliminar cuenta. Token Sanctum en `apiClient`.
- **Encuesta**: iniciar, responder, volver atrás a cambiar respuestas, progreso, enviar,
  pantalla finalizada, compartir link.
- **Admin** (solo `rol = admin`): métricas, lista de usuarios, detalle de respuestas, editar/eliminar.

## Decisiones
- Paleta de **colores que relajen la vista** (requisito no funcional).
- Validación en cliente coherente con el backend (la **fuente de verdad es el backend**).
- Google OAuth → fase posterior (botón en Login/Registro en fase 10).

## Convenciones
- camelCase, SOLID. **Componentes < 300 líneas** (preguntar antes de dividir).
- No `any` en TS sin justificar. `VITE_API_URL` desde `.env` (no subir `.env`).
- No instalar dependencias sin avisar (incluida librería de gráficos para el panel admin).
