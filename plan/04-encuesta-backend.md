# Fase 04 — Encuesta (API)

## Objetivo
Endpoints para que un usuario autenticado inicie su encuesta, responda preguntas (pudiendo volver
atrás a cambiar respuestas), envíe la encuesta y consulte su estado. Incluir link para compartir.

## Endpoints (bajo `/api`, requieren `auth:sanctum` salvo el público de compartir)
- `GET  /preguntas` — lista de preguntas fijas (ordenadas).
- `POST /encuesta/iniciar` — crea (o recupera) la `encuesta` del usuario con `is_ok = false`.
- `GET  /encuesta` — encuesta del usuario + respuestas ya guardadas (para reanudar/volver atrás).
- `PUT  /encuesta/respuestas/{idPregunta}` — guarda/actualiza una respuesta (idempotente).
- `POST /encuesta/enviar` — valida que estén todas las respuestas y marca `is_ok = true`.
- `GET  /encuesta/estado` — devuelve si terminó (`is_ok`) y progreso (respondidas/total).
- `GET  /encuesta/compartir` — devuelve el link público de la encuesta para compartir.

## Pasos
1. `EncuestaController` (Api): iniciar, show, estado, enviar.
2. `RespuestaController` (Api): upsert de respuesta por pregunta (vuelta atrás = volver a `PUT`).
3. Validar que la pregunta exista y la respuesta sea un **entero entre 1 y 5**; impedir editar si `is_ok = true`
   (o permitir reapertura según se confirme con el usuario).
4. `enviar` exige respuestas completas; si falta alguna → `422` indicando cuáles.
5. Endpoint/ruta pública de compartir (landing que invita a registrarse y responder).

## Archivos a tocar
- `app/Http/Controllers/Api/EncuestaController.php`, `.../RespuestaController.php`.
- `app/Http/Requests/GuardarRespuestaRequest.php` — regla `'respuesta' => ['required','integer','min:1','max:5']`.
- `routes/api.php`.

## Criterio de "hecho"
- Flujo completo: iniciar → responder varias → volver atrás y cambiar → enviar → estado `is_ok=true`.
- No se puede enviar incompleta. Respuestas son 1 por (encuesta, pregunta).

## Tests
- `tests/Feature/Encuesta/FlujoEncuestaTest.php` — iniciar, responder, reabrir respuesta, enviar.
- `tests/Feature/Encuesta/EnviarIncompletaTest.php` — rechazo si faltan respuestas.
- `tests/Feature/Encuesta/RespuestaInvalidaTest.php` — `422` ante respuestas fuera de rango (`0`, `6`, no numérico).

## Notas
- Confirmar con el usuario si tras `enviar` se permite editar respuestas.
- Actualizar `context/context_backend.md`.
