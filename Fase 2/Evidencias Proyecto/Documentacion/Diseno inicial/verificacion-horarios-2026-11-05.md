# Verificación de horarios disponibles

Fecha: 5 de noviembre de 2026. Código de referencia: `e7e02c4`.

Se ejecutó la función `getAvailableSlots` con consultas de Prisma simuladas.
Los cinco escenarios aprobaron sus aserciones, sin consultas ni escrituras en Neon.

| Caso | Resultado observado |
| --- | --- |
| Servicio de 30 minutos; tramo 10:00–12:00; reserva 10:30–11:00 | Para el 09-11-2026, en America/Santiago, se devuelven 10:00, 11:00 y 11:30. |
| Sin disponibilidad configurada | Lista vacía. |
| Tramo completamente reservado | Lista vacía. |
| Bloques repetidos, sin reservas | Horarios ordenados y sin duplicados. |
| Servicio inactivo | Respuesta 404. |

También se ejecutaron `booking.spec.ts` y `booking-regressions.spec.ts`: cuatro
pruebas aprobadas. Cubren creación del componente sin servicios externos, cambio de
fecha, fecha mínima en la zona del negocio y conservación del error al recargar horarios.

Esta comprobación no sustituye la demostración de interfaz, API y base de datos
real trabajando en conjunto. Esa validación conserva su propia evidencia.
