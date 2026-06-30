# [Encuesta sobre la atención]
[Sistema de encuesta que pregunta sobre cómo ciertas redes sociales y videojuegos, diseñados para mantenerte en su ciclo de uso mediante recompensas constantes, han influido en tus hábitos de atención y concentración.]

## Stack
### [Backend]
- Laravel (Última versión)
- PHP (última versión)
- PHPUNIT (última versión)
### [DATABASE]
- Postgresql (Última versión) 

### [Frontend]
- React js (Última versión)
- Typescript (Última versión)
- Jest (última versión)
- React testing library (última versión)

## Comandos
Sin comando por ahora

## Estructura del proyecto

### Backend (`backend/`)
- `app/Models/` — Modelos Eloquent 
- `app/Http/Controllers/Api/` — Controllers que exponen los endpoints
- `database/migrations/` — Definición de las tablas
- API REST con Sanctum para auth

### Frontend (`frontend/`)
- `src/components/` — Componentes reutilizables 
- `src/pages/` — Vistas principales 
- `src/services/` — Llamadas a la API (fetch/axios)
- SPA en React (Vite)

## Convenciones
- Uso de camelCase para variables y funciones
- Uso de principios SOLID
- Almacenar logs de errores de backend en carpeta logs
- Validar cada solicitud en React Y Laravel
- Los test del frontend deben estar en cada componente 
  ejemplo: components/FormularioEncuesta/FormularioEncuesta.tsx 
           components/FormularioEncuesta/FormularioEncuesta.test.tsx
- Los test del backend deben estar en la carpeta de test por defecto
  Ej:test/Features/Http/postEncuestaTest.php

## No hagas
- No instalar dependencias sin avisar
- No subir archivos .env al repositorio solo .env_example
- No usar any en typescript sin justificarlo
- No borrar codigo sin que yo te lo confirme
- No dejar codigo comentado que ya no se usa
- No hacer componentes de mas de 300 lineas de en react , preguntar para dividr en partes
  más pequeñas

## Flujo de trabajo

- Antes de una tarea compleja o mediana, propone un plan y espera mi confirmación
- Las tareas son una a la vez, pido, haces, reviso, confirmo.
- Si no estas seguro al 80% , pregunta y no inventes.

## Documentación
- La documentación está en /docs
- El contexto esta en /context

## Trabajar con contexto y documentación - IMPORTANTE
- Cada vez que haya cambios(pequeños,medianos,grandes) 
  necesito que actualices el /context  para mantener
  el contexto de la app context_frontend.md y context_backend.md
- Si una desición mía es nueva en el transcurso del proyecto respecto a /docs
  entonces modificalos archivos para que tenga los ultimos cambios


