# Brief: Habit Tracker

> Esto es el **brief del proyecto**, no la spec. El brief describe qué se quiere construir en lenguaje de producto. La spec la escribes tú a partir de este brief.

---

## El problema

Mucha gente quiere construir hábitos pero no sostiene el seguimiento. Las apps que existen son demasiado pesadas (sociales, gamificadas, con suscripción) o demasiado ligeras (una nota en el teléfono). Falta algo intermedio: una app simple, seria, que te permita declarar tus hábitos y revisar tu progreso sin fricción.

---

## Núcleo obligatorio

### 1. Autenticación

El usuario se registra y entra a la app con email y password. Cada usuario ve solo sus propios hábitos.

### 2. CRUD de hábitos

El usuario puede crear, editar y eliminar hábitos. Cada hábito tiene mínimo: nombre, descripción y frecuencia (diaria o semanal).

**Decisiones abiertas:** ¿Borrar un hábito borra su historial o lo archiva? ¿Se puede editar un hábito que ya tiene check-ins registrados?

### 3. Check-in diario

El usuario puede marcar un hábito como cumplido en el día actual. Una vez marcado, queda registrado.

**Decisiones abiertas:** ¿Se puede desmarcar un check-in? ¿Se puede hacer check-in de días pasados?

### 4. Vista de progreso

El usuario ve una lista de sus hábitos con: estado del día actual (cumplido / no cumplido) y racha actual (días consecutivos cumpliendo).

---

## Extensiones (elige máximo 1)

| Extensión               | Descripción                                      |
|-------------------------|--------------------------------------------------|
| Recordatorios           | Notificaciones (email o in-app) a una hora configurada. |
| Estadísticas históricas | Gráfico o tabla de cumplimiento por semana/mes. |
| Categorías              | Agrupar hábitos por categorías (salud, trabajo, etc). |
| Hábitos compartidos     | Invitar a otros usuarios a coparticipar en un hábito. |
| Importar/exportar       | Descargar historial en CSV o JSON. |
| Personalización visual  | Modo oscuro, colores por hábito, íconos.        |
| Metas numéricas         | Cada hábito puede tener una meta (ej: 30 días seguidos). |

---

## Restricciones técnicas

- Frontend: Next.js 15 con App Router.
- Backend / DB: Supabase (Postgres + Auth).
- Deploy: Vercel.
- TypeScript estricto. Nada de `any` salvo justificado en CONTEXT.md.
- Estilos: Tailwind. Sin librerías de componentes pesadas.

---

## Lo que NO se evalúa

- Diseño visual premium. Que se vea decente, no premium.
- Performance avanzada. Salvo que cargue en >5 segundos.
- Tests automatizados.
- Responsive perfecto. Se prueba en desktop.
- Integración con IA o análisis predictivo.

---

> Una decisión no documentada es una decisión no tomada. Cuando dudes, decide ahora y escríbelo en la spec.
