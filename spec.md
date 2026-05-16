# Spec: Habit Tracker

## Objetivo

Aplicación web para que usuarios registrados declaren hábitos personales, marquen cumplimiento diario y visualicen su progreso con racha actual, usando Next.js 15 App Router, Supabase Auth/Postgres y Tailwind.

## Scope

### Entra

- Autenticación con email/password usando Supabase Auth.
- CRUD de hábitos: crear, editar y archivar hábitos con nombre obligatorio (máximo 50 caracteres), descripción opcional (máximo 100 caracteres) y frecuencia diaria o semanal.
- Frecuencia semanal = N veces por semana con días seleccionables por hábito.
- Check-in diario: hábitos diarios solo pueden marcarse cumplidos en el día actual; hábitos semanales solo pueden marcarse en los días programados.
- Vista de hábitos activos con estado del día actual, `current_streak` y `best_streak`.
- Estadísticas de cumplimiento sobre las últimas 28 días corridos: diario % = completados / 28; semanal % = completados / (días programados × 4).
- Archivado de hábitos con `archived_at`; los hábitos archivados conservan su historial y se excluyen de la lista activa.
- Cada usuario ve solo sus propios hábitos y check-ins.

### No entra

- Apps móviles nativas o PWA.
- Monetización, pagos, anuncios o suscripciones.
- Gamificación como badges, niveles o retos.
- Notificaciones push o email en el MVP.
- Compartir social.
- Onboarding extenso, identidad de marca premium o animaciones de celebración.

## Criterios de aceptación

- Un usuario puede registrarse, iniciar sesión y cerrar sesión.
- Un usuario autenticado ve solo sus hábitos y no puede acceder a los de otro usuario.
- Crear hábito guarda nombre y descripción con validaciones de longitud.
- Un hábito diario puede marcarse cumplido solo en el día actual según la zona horaria del usuario.
- Un hábito semanal solo puede marcarse cumplido en los días agendados para ese hábito.
- Hábito sin check-ins muestra `current_streak = 0` y `best_streak = 0`.
- Eliminar/archivar hábito registra `archived_at` y oculta el hábito de la vista activa, conservando sus datos.
- La vista de estadísticas presenta los últimos 28 días corridos y calcula el porcentaje de cumplimiento según la frecuencia seleccionada.
- La ruta de detalle del hábito permite edición dinámica y check-in en la misma página.
- Si la sesión expira, la UI muestra mensaje de sesión caducada; otros errores se muestran con mensaje genérico.
- Los flujos de signup, login y logout están incluidos como casos verificables.

## Pruebas técnicas fuera de QA manual

- Verificar que cada usuario no puede ver ni acceder a hábitos o check-ins de otro usuario.
- Confirmar integridad de `user_id` en hábitos y check-ins.
- Confirmar que `checkin_date` respeta la zona horaria configurada del usuario.

## Decisiones tomadas en entrevista

- Semanal se modela como N días seleccionables por semana.
- Check-ins se almacenan en tabla diaria con indicador booleano.
- Archivado es soft delete (`archived_at`) y conserva el historial.
- Los nombres de hábito son únicos por usuario.
- Se permiten múltiples check-ins en el mismo día, contándose como cumplido binario.
- `current_streak` y `best_streak` se persisten en el hábito.
- La zona horaria es propiedad del usuario y `checkin_date` se guarda como DATE local.
- Validaciones: nombre requerido 50 caracteres, descripción opcional 100 caracteres.
- Estadísticas de 28 días corridos; diarios % = completados/28; semanales % = completados/(días programados × 4).
- Rutas principales usan Server Components y Server Actions; la página de hábito es Client Page.
- La UI debe distinguir sesión expirada de errores generales.
- No-goals explícitos: mobile nativo, PWA, monetización, gamificación, notificaciones, compartir social, diseño premium, onboarding extenso y animaciones de celebración.

