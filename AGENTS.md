# Contrato de agentes del proyecto Habit Tracker

## 1. Stack
- Next.js 15 con App Router.
- Supabase: Postgres, Auth y Storage.
- Vercel para despliegue.
- TypeScript en modo estricto.
- Tailwind CSS para estilos.

## 2. Convenciones de TypeScript
- Siempre usar tipos explícitos cuando sea necesario.
- No usar `any` salvo justificación documentada en el código y aprobada por el equipo.
- Preferir `unknown` sobre `any` para datos de orígenes externos.
- Validar y tipar entradas y salidas de funciones críticas.
- No deshabilitar reglas de linter o comprobaciones estrictas sin justificación documentada.

## 3. Estructura de carpetas esperada
- `app/` para rutas y componentes de página.
- `components/` para componentes reutilizables.
- `lib/` o `utils/` para lógica compartida y helpers.
- `styles/` para configuraciones globales de Tailwind o estilos compartidos.
- `public/` para activos estáticos.
- `tests/` queda explícitamente fuera de este alcance; no se agregan pruebas automatizadas para esta tarea.

## 4. Política de commits
- Commits atómicos y verificables.
- Un commit por unidad funcional.
- No se aceptan commits gigantescos tipo "implement everything".
- Documentar ediciones manuales en `CONTEXT.md` con justificación clara.
- Cada commit debe corresponder a una tarea concreta y revisable.

## 5. Flujo git
- `main` es estable.
- `develop` es rama de integración.
- Cada unidad de trabajo va en una rama tipada:
  - `feat/` para nuevas funcionalidades.
  - `docs/` para documentación.
  - `chore/` para tareas de mantenimiento.
  - `fix/` para correcciones puntuales.
- Las ramas tipadas se mergean en `develop`.
- No se trabaja directamente en `main`.

## 6. Regla de `CONTEXT.md`
- Cualquier edición manual de código debe quedar registrada en `CONTEXT.md`.
- La entrada debe explicar qué se cambió y por qué.
- La regla se aplica tanto a agentes como a desarrolladores humanos.

## 7. Prohibiciones explícitas
- No usar `any` sin justificación y documentación.
- No incorporar librerías de componentes pesadas como Material UI o Chakra UI.
- No agregar tests automatizados en este alcance del proyecto.
- No reescribir commits existentes en `main`.
- No crear código sin plan aprobado.

## 8. Decisiones libres vs cerradas
- Libre: elección de patrones internos coherentes con Next.js, Tailwind y TypeScript estricto.
- Libre: estructura de carpetas adicionales si respetan la estructura esperada y el contrato.
- Cerrado: no alterar el flujo git definido ni la política de commits.
- Cerrado: no cambiar el stack o agregar dependencias de UI pesadas sin aprobación.
- Cerrado: no violar la regla de `CONTEXT.md`.

