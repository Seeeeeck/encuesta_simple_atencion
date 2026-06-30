# Fase 02 — Migraciones, modelos y seeders

## Objetivo
Implementar el modelo de datos (`docs/modelo_relacional.png`) en migraciones, modelos Eloquent
con relaciones, y seeders para las preguntas fijas y un administrador inicial.

## Pasos
1. **Migraciones** (en `database/migrations/`):
   - `usuario` — id, nombre (VARCHAR 100, not null), correo (VARCHAR 150, unique), clave (VARCHAR 255,
     not null, **cifrada**), edad (nullable), sexo (nullable), **rol** (VARCHAR 20, not null,
     default `'usuario'`), timestamps.
   - `encuesta` — id, id_usuario (FK → usuario), is_ok (boolean, default false), timestamps.
   - `pregunta` — id, pregunta_texto (VARCHAR 255), timestamps.
   - `respuesta` — id, id_encuesta (FK → encuesta), id_pregunta (FK → pregunta), respuesta (VARCHAR 255),
     timestamps. Índice único (id_encuesta, id_pregunta) para 1 respuesta por pregunta.
2. **Modelos Eloquent** (`app/Models/`): `Usuario`, `Encuesta`, `Pregunta`, `Respuesta`.
   - Relaciones: Usuario hasMany Encuesta; Encuesta belongsTo Usuario, hasMany Respuesta;
     Pregunta hasMany Respuesta; Respuesta belongsTo Encuesta y Pregunta.
   - `clave` en `$hidden` y casteada con hash (cifrado, nunca texto plano).
3. **Seeders**:
   - `PreguntaSeeder` — preguntas fijas de la encuesta (definir lista con el usuario).
   - `AdminSeeder` — 1 usuario con `rol = 'admin'` (credenciales desde `.env`, no hardcodear).

## Archivos a tocar
- `database/migrations/*`, `app/Models/*`, `database/seeders/*`.

## Criterio de "hecho"
- `php artisan migrate:fresh --seed` crea las 4 tablas, carga preguntas y el admin.
- `correo` rechaza duplicados; `rol` por defecto `'usuario'`.
- La clave se guarda cifrada (hash), nunca en texto plano.

## Tests
- `tests/Feature/Models/RelacionesTest.php` — relaciones y cascada esperada.
- `tests/Feature/Database/SeedersTest.php` — seeders cargan preguntas + admin.

## Notas
- Confirmar con el usuario el **listado exacto de preguntas** antes de sembrar.
- Actualizar `context/context_backend.md` (esquema final).
