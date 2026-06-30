# Fase 11 — No funcionales y despliegue

## Objetivo
Cumplir los requisitos no funcionales y dejar la app desplegada en un hosting gratuito y estable,
con HTTPS, responsive y buen rendimiento.

## Requisitos no funcionales (de `docs/requisitos_no_funcionales.md`)
- Carga en **< 2 s**.
- **Lighthouse / PageSpeed > 90**.
- Colores que relajen la vista (ya abordado en fase 06).
- **HTTPS** obligatorio.
- Clave de usuario **cifrada** en BD (ya en fase 02).
- **Responsive** web/móvil.
- Hosting **gratuito y estable**.
- Soportar **≥ 50 usuarios concurrentes**.

## Pasos
1. **Rendimiento frontend**: build de producción Vite, code-splitting, lazy-loading de rutas,
   imágenes optimizadas; medir con Lighthouse hasta superar 90 y < 2 s.
2. **Responsive**: verificar layouts en breakpoints móvil/tablet/escritorio.
3. **Backend prod**: caché de config/rutas, conexión Postgres con pool; revisar consultas de métricas.
4. **HTTPS**: certificado en el hosting (o detrás de proxy/CDN con TLS).
5. **Despliegue** (elegir y confirmar opciones gratuitas):
   - Frontend estático (p. ej. Netlify/Cloudflare Pages/Vercel — SPA estática).
   - Backend Laravel + PostgreSQL (p. ej. Railway/Render/Fly free tier — confirmar con el usuario).
   - Variables de entorno de producción (sin subir `.env`).
6. **Carga**: prueba sencilla de ~50 usuarios concurrentes (k6/Artillery) y ajustar.

## Criterio de "hecho"
- App accesible por HTTPS, responsive, Lighthouse > 90 y carga < 2 s.
- Soporta la concurrencia objetivo sin errores.

## Tests / verificación
- Reporte Lighthouse adjunto. Resultado de prueba de carga.
- Smoke test del flujo completo en producción (registro → encuesta → admin).

## Fuera de alcance (de `docs/requisitos_fuera_alcance.md`)
- No crear otras encuestas con preguntas distintas.
- La encuesta no caduca.
- No exportar/descargar estadísticas a Excel.

## Notas
- Confirmar proveedores de hosting antes de configurar (implica cuentas/credenciales).
- Actualizar `/context` y `/docs` si cambian decisiones de despliegue.
