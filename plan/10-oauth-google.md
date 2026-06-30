# Fase 10 — Google OAuth (fase posterior)

> **Decisión**: el MVP usa auth clásica (correo + clave vía Sanctum). Esta fase se hace **después**
> de tener el flujo principal funcionando.

## Objetivo
Permitir crear cuenta e iniciar sesión con Google, además de la auth clásica.

## Pasos
1. **Backend**: instalar **Laravel Socialite** (avisar antes — dependencia).
2. Crear credenciales OAuth en Google Cloud Console; guardar `GOOGLE_CLIENT_ID/SECRET/REDIRECT` en
   `.env` (y `.env.example` sin valores reales).
3. Migración: añadir `google_id` (nullable, unique) a `usuario`; permitir `clave` nullable para
   cuentas creadas solo con Google. **Actualizar los diagramas** en `docs/` y `/context`.
4. Endpoints: `GET /api/auth/google/redirect` y `GET /api/auth/google/callback` — crea/recupera el
   usuario por `google_id`/correo y emite token Sanctum.
5. **Frontend**: botón "Continuar con Google" en Login/Registro que inicia el flujo OAuth.
6. Manejar enlace de cuenta existente (mismo correo) y conflictos.

## Archivos a tocar
- `backend/`: Socialite config, `routes/api.php`, `AuthController` (acciones Google), migración
  `google_id`.
- `frontend/`: botón en `pages/Login` y `pages/Registro`, `authService.ts`.
- `docs/modelo_*.dot` + PNG regenerados; `context/context_backend.md`.

## Criterio de "hecho"
- Registro/login con Google crea sesión válida; convive con la auth clásica.

## Tests
- `tests/Feature/Auth/GoogleOAuthTest.php` (mock de Socialite): crea/recupera usuario y emite token.
- Front: test del botón y del manejo del callback.

## Notas
- Requisito funcional: "confirmar la cuenta con Google" / "crear e iniciar con Google".
