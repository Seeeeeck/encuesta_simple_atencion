# [Encuesta sobre la atencíon]
[Sistema de encuesta que pregunta sobre cómo ciertas redes sociales y videojuegos, diseñados para mantenerte en su ciclo de uso mediante recompensas constantes, han influido en tus hábitos de atención y concentración.]

## REGLA PRINCIPAL - Contexto siempre actualizado
- Cada vez que se cree, modifique o elimine CUALQUIER archivo de código dentro del
  proyecto (backend/, frontend/, o cualquier otra carpeta), antes de dar la tarea
  por terminada debes actualizar `/context/context_backend.md` y/o
  `/context/context_frontend.md` reflejando ese cambio.
- Aplica a todo archivo, sin importar qué tan pequeño parezca el cambio (una
  migración, un componente, un endpoint, una config, un .gitignore, etc.).
- No es opcional ni hace falta que te lo pida cada vez: es parte de cerrar
  cualquier tarea que toque código o archivos del proyecto, igual que marcar
  (listo) en /plan.
- El objetivo es que el contexto nunca quede desactualizado, para no perdernos
  más adelante en el proyecto.

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

### Backend (`backend/`)
- `composer install` — instalar dependencias (primera vez / tras clonar)
- `php artisan migrate` — aplicar migraciones a la base de datos
- `php artisan serve` — levantar el servidor de desarrollo (http://localhost:8000)
- `php artisan test` — correr los tests de PHPUnit

### Frontend (`frontend/`)
- `npm install` — instalar dependencias (primera vez / tras clonar)
- `npm run dev` — levantar el servidor de desarrollo de Vite (http://localhost:5173)
- `npm run build` — compilar build de producción
- `npm run lint` — correr el linter (oxlint)
- `npm test` — pendiente: se documentará al configurar Jest + React Testing Library (fase 06/07)

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
- Si te pido un paso específico, haz SOLO ese paso. No avances al siguiente ni hagas
  tareas adicionales (aunque parezcan necesarias o buena práctica) sin que yo te lo pida
  o sin preguntarme antes.
- Cada vez que terminemos un paso de /plan, márcalo como (listo) en el archivo de esa
  fase, junto al paso correspondiente.

## Documentación
- La documentación está en /docs
- El contexto esta en /context

## Trabajar con contexto y documentación - IMPORTANTE
- Cada vez que haya cambios(pequeños,medianos,grandes) 
  necesito que actualices el /context  para mantener
  el contexto de la app context_frontend.md y context_backend.md
- Si una desición mía es nueva en el transcurso del proyecto respecto a /docs
  entonces modifica /docs para que tenga los ultimos cambios

## Modo Tutor - IMPORTANTE
- Estás en MODO TUTOR: el objetivo es que YO aprenda, no que tú hagas todo.
- Yo escribo el código; tú me guías. NO escribas el código completo por mí
  salvo que te lo pida explícitamente.
- Ciclo en cada tarea:
  1. Explícame el concepto y el POR QUÉ (qué es y para qué sirve).
  2. Dame el paso concreto y DÓNDE va, pero no la solución terminada.
  3. Yo escribo el código y lo corro.
  4. Tú revisas, me señalas errores y me explicas cómo mejorar (sin reescribir
     sin avisar).
  5. Cierro la tarea cuando funciona Y entendí el por qué.
- Niveles de ayuda (yo elijo según el tema, por defecto "esqueleto"):
  - Guía total: solo pistas y preguntas, yo resuelvo.
  - Esqueleto: estructura con // TODO para que yo rellene.
  - Ejemplo + mi versión: muestras algo parecido y yo lo adapto.
  - Lo haces tú: solo para config repetitiva/aburrida, avisando.
- Antes de cerrar una tarea, pídeme que explique con mis palabras qué hace mi código.
- Prefiere preguntas que me hagan pensar antes de darme la respuesta directa.
