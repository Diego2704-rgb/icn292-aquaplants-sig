# 03 — Modelo de datos preliminar

> Versión navegable de la sección E del informe. Diagrama exportado en
> [`../assets/er-preliminar.png`](../assets/er-preliminar.png).
>
> **Estado:** preliminar. En la Entrega 2 este modelo se congela en el hito H2 y se implementa como
> `schema.sql`; toda diferencia entre lo documentado y lo implementado queda justificada aquí.

## Entidades principales

| Entidad | Razón de existir | Requisitos que la exigen |
| --- | --- | --- |
| Cliente | Titular de la relación comercial y del seguimiento | RF-01, RF-07 |
| Orden | Transacción de venta con sus ítems, medio y estado de pago | RF-02 |
| Ítem de orden | Detalle de productos y cantidades de cada orden | RF-02, RF-11 |
| Producto (SKU) | Catálogo con stock, distinguiendo almácigos por variedad | RF-11, RF-14 |
| **Huerto** | Objeto de negocio que hoy no existe: el kit instalado, derivado de la orden | RF-03 |
| Estado de huerto | Historial de verificaciones con fecha, fuente y responsable | RF-04, RNF-03 |
| Interacción | Contacto con el cliente: canal, fecha, motivo, responsable, estado | RF-06 |
| Despacho | Transportista, número de seguimiento, fecha comprometida y aviso | RF-09 |
| Ticket | Incidencia con estado, acción tomada y cierre | RF-10 |
| Usuario y Rol | Control de acceso por perfil a los datos personales | RF-08, RNF-01 |
| Bitácora de acceso | Registro de consultas y modificaciones sobre datos personales | RNF-02, RNF-03 |

## Relaciones clave

- Un **Cliente** tiene muchas **Órdenes**; una **Orden** pertenece a un solo Cliente.
- Una **Orden** origina cero o más **Huertos** (uno por kit vendido). Esta es la relación que
  resuelve el problema: conecta la transacción con el objeto que se debe seguir.
- Un **Huerto** tiene muchos registros de **Estado de huerto**; el estado vigente es el más
  reciente. Se modela como historial y no como campo único para cumplir RNF-03.
- Un **Cliente** tiene muchas **Interacciones**, provenientes de distintos canales.
- Un **Usuario** interno tiene un **Rol**, y ese rol determina qué datos personales puede ver.

## Puntos abiertos para la Entrega 2

- Llave natural del Cliente: el RUT es la llave de deduplicación de RF-07, pero se usa solo para
  identificación y no se expone en listados operativos (ver sección G del informe).
- Definición de "huerto activo" y del umbral N de días sin verificación: pendiente de validación con
  la contraparte (hito H1).
- Estrategia de borrado: el modelo debe soportar borrado lógico y físico para atender solicitudes de
  supresión (RNF-02).
