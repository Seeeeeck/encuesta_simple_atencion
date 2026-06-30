# encuestas_simple_atencion

Sistema de encuesta que evalúa cómo el uso de redes sociales y videojuegos con
sistemas de alta recompensa (notificaciones, scroll infinito, rachas, loot, etc.)
influye en los hábitos de atención y concentración de las personas.

## Objetivo

Obtener métricas de personas de diferentes edades sobre el uso frecuente de redes
sociales y videojuegos con sistemas de alta recompensa, analizando su influencia en
la atención, el tiempo de permanencia y los hábitos de consumo digital.

## Stack

- **Backend**: Laravel + PHP, PostgreSQL, autenticación con Sanctum, tests con PHPUnit.
- **Frontend**: React + TypeScript (Vite), tests con Jest + React Testing Library.

## Estructura

- `backend/` — API REST en Laravel.
- `frontend/` — SPA en React.
- `docs/` — objetivo, requisitos funcionales/no funcionales y modelos de datos.
- `context/` — estado vivo del backend y frontend (se actualiza con cada cambio).
- `plan/` — roadmap de construcción por fases.

Ver `CLAUDE.md` / `AGENTS.md` para comandos de desarrollo y convenciones del proyecto.
