# 01 — Requerimientos

> Versión navegable de la sección C del informe. El detalle completo, con la trazabilidad a cada
> pregunta de la entrevista (P1 a P27), está en `informe/`.

## Actores humanos

| Actor | Rol en AquaPlants | Intervención |
| --- | --- | --- |
| Cliente | Comprador final del kit o de insumos | Compra en la web, recibe correos y WhatsApp. Es la fuente del estado de uso del huerto |
| Gabriel | Socio fundador, encargado comercial | Responde consultas por cuatro canales y hace el seguimiento post-venta. **Usuario principal del SIG** |
| Damián | Encargado de operaciones | Mantiene stock permanente. Consumidor de las alertas de stock |
| Yuri | Asistente de operaciones | Prepara estructura y plantas el día antes del despacho. Consumidor de la lista de pedidos por preparar |
| Andrés | Administrador de sistemas y plataforma digital | Contraparte técnica para la integración e importación de datos |
| Kevin | CEO y encargado de proyectos | Decisión de adopción. Consumidor del panel de indicadores |

## Sistemas y entidades externas

Ninguno se reemplaza en este proyecto: el SIG convive con ellos.

| Sistema / entidad | Relación con el SIG |
| --- | --- |
| Sitio web aquaplants.cl | Origen del pedido y de los datos de cliente e ítems |
| CRM | Fuente de la carga inicial y contraparte de integración; no se reemplaza |
| WhatsApp + asistente virtual con IA | Canal donde se registran las interacciones; el SIG consolida, no responde |
| Instagram / Facebook / correo | Origen de interacciones a registrar |
| Meta (publicidad) | Fuera de alcance; solo se registra el canal de origen |
| Mercado Pago | Fuera de alcance; el SIG solo registra estado y medio de pago |
| Mercado Libre | Origen de órdenes a registrar (carga manual en E1) |
| Starken / BlueExpress | El SIG registra transportista, seguimiento y aviso al cliente |
| Martiplant | Proveedor de almácigos; el SIG registra el requerimiento semanal |
| BACUPLAST | Inyección del molde; sin interacción con el SIG en esta entrega |

## Alcance

**Dentro (in).** Registro del huerto instalado como entidad derivada de la orden, con estado de uso
y fuente de verificación; lista priorizada de contacto post-venta y su resultado; historial de
interacciones consolidado por cliente; registro de cliente, orden, ítems, medio de pago y despacho;
catálogo por SKU con stock; tickets de incidencia; indicadores de cobertura, reactivación y
consultas sin respuesta; carga inicial desde el CRM y control de acceso por rol.

**Fuera (out).** Reemplazo del CRM; carro de compras, checkout y pagos; configuración del asistente
con IA; facturación y contabilidad; planificación productiva de proveedores; integración en tiempo
real con API de transportistas (en E2 el seguimiento se registra manualmente); app móvil nativa;
publicación en servidor productivo (la E2 se demuestra en localhost).

## Requisitos funcionales

| ID | Requisito | Prioridad |
| --- | --- | --- |
| RF-01 | Registrar y mantener la ficha de cliente (nombre, RUT, correo, teléfono, dirección) | Must |
| RF-02 | Registrar la orden de venta con fecha, canal, ítems, medio y estado de pago, incluido el caso 50/50 | Must |
| RF-03 | Crear una ficha de Huerto por cada kit vendido, asociada al cliente y a la orden | Must |
| RF-04 | Registrar y actualizar el estado de uso del huerto con fecha, fuente y responsable | Must |
| RF-05 | Generar la lista priorizada de huertos inactivos o sin verificar hace más de N días, y registrar el resultado del contacto | Must |
| RF-06 | Registrar cada interacción con el cliente y consultar el historial consolidado | Must |
| RF-07 | Importar clientes, productos y órdenes desde el CRM, con control de duplicados | Must |
| RF-08 | Administrar usuarios y permisos por rol, restringiendo el acceso a datos personales | Must |
| RF-09 | Registrar el despacho: transportista, seguimiento, fecha comprometida y aviso al cliente | Should |
| RF-10 | Registrar tickets de incidencia con estado, acción tomada y cierre | Should |
| RF-11 | Mantener el catálogo de productos por SKU, identificando almácigos por variedad | Should |
| RF-12 | Mostrar el panel de indicadores de cobertura, reactivación y consultas sin respuesta | Should |
| RF-13 | Registrar el requerimiento semanal de almácigos al proveedor | Could |
| RF-14 | Alertar a operaciones cuando el stock de un SKU cae bajo el umbral | Could |
| RF-15 | Responder automáticamente los mensajes entrantes | Won't |

## Requisitos no funcionales

| ID | Requisito | Prioridad |
| --- | --- | --- |
| RNF-01 | Seguridad de acceso: autenticación, hash de contraseñas, sesión con expiración | Must |
| RNF-02 | Cumplimiento de la Ley 21.719: finalidad, minimización, conservación, derechos del titular y registro de accesos | Must |
| RNF-03 | Auditabilidad de toda modificación de estado de huerto o ficha de cliente | Must |
| RNF-04 | Usabilidad para usuario no técnico, operable desde el navegador de un teléfono | Must |
| RNF-05 | Reproducibilidad: el sistema se levanta en localhost siguiendo el README | Must |
| RNF-06 | Interoperabilidad: import/export CSV y endpoints REST documentados | Should |
| RNF-07 | Desempeño: respuesta bajo 3 s para 1.500 clientes y 5.000 órdenes | Should |
| RNF-08 | Respaldo diario y procedimiento de restauración documentado | Should |
| RNF-09 | Documentación autoexplicativa en el repositorio, con control de versiones por rama | Must |
| RNF-10 | Disponibilidad: la operación comercial no depende del SIG para vender | Could |

## Supuestos a confirmar antes de la Entrega 2

- El CRM permite exportar en formato tabular. Si no, RF-07 se degrada a carga manual.
- El estado de uso se levanta por contacto humano o respuesta del cliente: no hay sensores en las torres.
- El umbral N de días sin verificación (RF-05) lo define la empresa; se propone 90 días como valor a validar.
- El volumen de referencia de RNF-07 se basa en la cifra declarada de más de 1.500 clientes.
