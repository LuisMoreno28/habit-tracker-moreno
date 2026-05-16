# Spec: Habit Tracker (Borrador inicial)

## Objetivo

Aplicación web para que usuarios registrados declaren hábitos personales, marquen su cumplimiento diario y visualicen su progreso. Foco: simplicidad y seguimiento sin fricción.

## Scope

### Entra

- Autenticación: registro e login con email/password vía Supabase Auth.
- CRUD de hábitos: crear, editar, eliminar. Cada hábito: nombre, descripción, frecuencia (diaria/semanal).
- Check-in: marcar cumplimiento del día actual. No se puede desmarcar ni hacer check-in de días pasados.
- Vista de progreso: lista de hábitos con estado hoy + racha actual (días consecutivos).
- Racha: se rompe cuando hay un día sin check-in.
- Eliminar hábito borra su historial.
- Extensión: estadísticas (gráfico o tabla cumplimiento por semana/mes).

### No entra

- Editar hábitos después de tener check-ins.
- Hábitos compartidos, recordatorios, categorías, importar/exportar, personalización visual.
- Tests automatizados, diseño premium, performance <5s.

## Criterios de aceptación

- Usuario autenticado ve solo sus hábitos.
- Crear hábito guarda nombre, descripción, frecuencia en BD.
- Check-in del día marca cumplimiento; persiste entre sesiones.
- Vista progreso muestra estado actual + racha. Racha se calcula correctamente.
- Eliminar hábito borra registro completo. Confirmar antes de eliminar.
- Estadísticas: tabla/gráfico con cumplimiento por semana (mínimo 4 semanas últimas).

## No-goals

- Sincronización en tiempo real (ok que sea eventual).
- Análisis predictivo o recomendaciones.
- Apps móviles nativas.
- Auditoría de cambios.
