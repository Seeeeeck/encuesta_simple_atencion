# Fase 08 — Frontend encuesta

## Objetivo
Flujo de respuesta de la encuesta: iniciar, navegar entre preguntas (ida y vuelta para cambiar
respuestas), enviar y ver el estado de finalización.

## Pasos
1. Página `src/pages/Encuesta/` que carga preguntas (`GET /api/preguntas`) y la encuesta del usuario
   (`GET /api/encuesta`) para reanudar.
2. Componente de navegación pregunta-a-pregunta: avanzar, **retroceder** y editar respuestas previas.
   La respuesta se captura como **escala 1–5** (radios o botones) con **anclas de texto en los extremos**
   (ej. 1 = "Nunca" … 5 = "Siempre"); las anclas son solo display, en BD se guarda el número. Validación
   en cliente: entero 1–5, requerido, coherente con el backend. *(Confirmar el texto de las anclas.)*
3. Guardado de cada respuesta (`PUT /api/encuesta/respuestas/{idPregunta}`) — autosave o por paso.
4. Indicador de progreso (respondidas/total) usando `GET /api/encuesta/estado`.
5. Enviar (`POST /api/encuesta/enviar`): bloquear si está incompleta y mostrar qué falta.
6. Pantalla de "encuesta finalizada" + opción de **compartir link** (`GET /api/encuesta/compartir`).

## Archivos a tocar
- `frontend/src/pages/Encuesta/*`.
- `frontend/src/components/Pregunta/*`, `src/components/ProgresoEncuesta/*`,
  `src/components/CompartirLink/*`.
- `frontend/src/services/encuestaService.ts`.

## Criterio de "hecho"
- Usuario inicia, responde, retrocede a cambiar una respuesta, envía y ve el estado finalizado.
- No deja enviar incompleta; el progreso refleja lo respondido.

## Convenciones
- Componentes **< 300 líneas** (la página de encuesta probablemente se divide en subcomponentes;
  preguntar antes de partir).
- Test al lado de cada componente.

## Tests
- `src/pages/Encuesta/Encuesta.test.tsx` — flujo cargar/responder/enviar.
- `src/components/Pregunta/Pregunta.test.tsx`, `ProgresoEncuesta/ProgresoEncuesta.test.tsx`.

## Notas
- Actualizar `context/context_frontend.md`.
