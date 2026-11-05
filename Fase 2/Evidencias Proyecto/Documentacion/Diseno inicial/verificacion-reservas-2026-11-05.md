# Verificación de estados de reservas

Fecha: 5 de noviembre de 2026. Código de referencia: `3c68c0d`.
Archivo: `backend/tests/reservation-state.test.ts`.

Se ejecutó el archivo sobre una copia de trabajo de esa versión, utilizando el
ejecutable tsx de las dependencias locales ya instaladas:

```text
tsx --test backend/tests/reservation-state.test.ts
```

Resultado: 5 pruebas aprobadas y 0 fallidas. Se usan transacciones simuladas;
no se escriben datos en Neon ni se acredita concurrencia real en PostgreSQL.

```text
✔ no permite cancelar una atención completada (2.0045ms)
✔ cancelar dos veces es idempotente (0.282ms)
✔ completar dos veces conserva una única atención y el precio original aunque cambie la tarifa (0.4215ms)
✔ una cancelación previa impide completar (0.2128ms)
✔ no permite completar reservas futuras o pendientes (0.3663ms)
ℹ tests 5
ℹ suites 0
ℹ pass 5
ℹ fail 0
ℹ cancelled 0
ℹ skipped 0
ℹ todo 0
ℹ duration_ms 382.3191
```

Este resultado verifica de manera parcial las reglas de estado de las reservas.
La reserva exitosa desde interfaz y la concurrencia real requieren sus propias evidencias.
