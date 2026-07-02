# Fase 05 — Administración y métricas (API)

## Objetivo
Endpoints solo para `rol = admin`: ver métricas de la encuesta, listar usuarios, ver respuestas de
cada usuario, editar y eliminar usuarios. Proteger con middleware de rol.

## Endpoints (bajo `/api/admin`, requieren `auth:sanctum` + middleware `EsAdmin`)
- `GET    /metricas` — métricas agregadas: **promedio (AVG) por pregunta** y **distribución de valores 1–5**
  por pregunta, % por edad/sexo, completadas.
- `GET    /usuarios` — listado de usuarios (paginado).
- `GET    /usuarios/{id}/respuestas` — encuesta + respuestas de un usuario.
- `PUT    /usuarios/{id}` — editar nombre, clave, edad, sexo, correo (y rol si se confirma).
- `DELETE /usuarios/{id}` — eliminar usuario (cascada a su encuesta/respuestas).

## Pasos
1. Middleware `EsAdmin` que verifica `rol === 'admin'` (registrar en Kernel) → `403` si no.
2. `Admin/MetricasController` — consultas agregadas: como `respuesta` es numérica (1–5), calcular
   `AVG(respuesta)` y conteo por valor (distribución 1–5) agrupando por pregunta; además agrupar por
   edad, sexo, `is_ok`.
3. `Admin/UsuarioController` — index, respuestas, update, destroy.
4. Validación en update (correo único excluyendo al propio usuario; clave hasheada si cambia).
5. Registrar rutas con grupo `prefix('admin')->middleware(['auth:sanctum','es_admin'])`.

## Archivos a tocar
- `app/Http/Middleware/EsAdmin.php`, `app/Http/Kernel.php`.
- `app/Http/Controllers/Api/Admin/MetricasController.php`, `.../UsuarioController.php`.
- `routes/api.php`.

## Criterio de "hecho"
- Un usuario normal recibe `403` en `/api/admin/*`.
- El admin lista usuarios, ve respuestas, edita y elimina; las métricas cuadran con los datos.

## Tests
- `tests/Feature/Admin/AccesoAdminTest.php` — usuario normal 403, admin 200.
- `tests/Feature/Admin/MetricasTest.php`, `tests/Feature/Admin/GestionUsuariosTest.php`.

## Notas
- Las métricas alimentan el panel del frontend (fase 09).
- Actualizar `context/context_backend.md`.
