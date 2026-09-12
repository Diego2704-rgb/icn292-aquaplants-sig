# 02 — Procesos BPMN

> Versión navegable de la sección D del informe. Diagramas exportados en `../assets/`.

| Diagrama | Archivo |
| --- | --- |
| Proceso crítico as-is | [`../assets/bpmn-as-is.png`](../assets/bpmn-as-is.png) |
| Proceso crítico to-be | [`../assets/bpmn-to-be.png`](../assets/bpmn-to-be.png) |
| Fuentes editables | `../assets/bpmn-as-is.bpmn`, `../assets/bpmn-to-be.bpmn` |

## As-is

El diagrama modela el proceso crítico en notación BPMN 2.0, desde la compra en la web hasta el
seguimiento post-venta, en cinco fases: compra y pago, preparación de producto, despacho y envío,
post-venta y seguimiento post-venta. Se representa con un pool para AquaPlants subdividido en los
carriles Comercial, Operaciones y Web / CRM, más pools independientes para Cliente, Mercado Pago,
Starken / BlueExpress y Martiplant.

El modelo cubre el ciclo completo y no solo el tramo del problema, porque así el to-be puede
intervenir donde está el dolor y el diagrama hace visible el punto exacto de quiebre: el ciclo de
pedido está razonablemente estructurado, pero al momento de la entrega el kit vendido deja de
existir como objeto de negocio y el proceso continúa sin ningún registro que lo sostenga.

Dos elementos del as-is son la representación gráfica del problema:

1. El evento que gatilla el seguimiento no responde a un dato del cultivo, sino al paso de un tiempo estimado desde la venta o desde el último mantenimiento.
2. La tarea "Seleccionar arbitrariamente al cliente" es el mecanismo real con el que hoy se decide a quién contactar, y el propio diagrama lo declara arbitrario.

El proceso cierra en un evento de fin que registra la situación tal como es: fin del ciclo de
mantenimiento y sin registro de cultivos activos.

## To-be

Conserva la misma estructura de pools, carriles y fases para que la comparación sea directa, e
incorpora un carril adicional para el SIG. El carril Web / CRM se mantiene separado para hacer
explícito que el SIG no lo reemplaza: el pedido se sigue registrando en la web y el correo
automático se sigue enviando desde ahí; lo que se agrega es que esa orden alimenta al SIG, que crea
la ficha de Huerto.

Tres intervenciones centrales quedan identificadas sobre el diagrama:

1. Creación de la ficha de Huerto asociada a la orden que la originó (**RF-03**): nace el objeto de negocio que hoy no existe.
2. Actualización del estado de uso con fecha, fuente y responsable de la verificación (**RF-04**).
3. Generación de la lista priorizada de huertos sin verificar (**RF-05**), que reemplaza la selección arbitraria del as-is.

Se suman el registro del despacho (RF-09), el registro de la interacción (RF-06) y la actualización
del panel de indicadores (RF-12).

El diagrama distingue dos tipos de tarea que no deben confundirse: las **tareas de servicio**
(símbolo de engranaje), ejecutadas por el sistema sin intervención humana, y las **tareas humanas
marcadas "→ SIG"**, ejecutadas por una persona que registra el resultado en el sistema, vinculadas
a la base de datos mediante asociaciones de datos.
