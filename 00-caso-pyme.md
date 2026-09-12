# 00 — Caso PYME: AquaPlants

> Versión navegable de las secciones A y B del informe. El entregable formal está en `informe/`.

## Identificación

| Atributo | Descripción |
| --- | --- |
| Nombre / marca | AquaPlants (sitio propio: aquaplants.cl) |
| Rubro | Venta y producción de sistemas de cultivo hidropónico e insumos asociados |
| Antigüedad | Poco menos de 5 años de operación (declarado el 07-09-2026) |
| Tamaño | 5 personas de dotación permanente |
| Cartera | Más de 1.500 clientes, según declaración de la propia empresa |

Producto principal: el kit *Torre AquaPlants*, que se vende como paquete completo (estructura,
almácigos y nutrientes). En paralelo comercializa insumos de cultivo hidropónico —almácigos,
nutrientes, contenedores, espumas germinadoras— que por su naturaleza consumible generan demanda
recurrente.

## Evidencia de existencia

- **Principal:** entrevista presencial a Gabriel Daszenies, socio fundador y encargado comercial,
  el 07-09-2026, con pauta estructurada de 27 preguntas en 6 bloques. Acta completa en el Anexo A
  del informe.
- **Refuerzo:** presencia pública verificable (sitio propio y redes), con capturas fechadas en el
  Anexo B del informe.

## Problema de negocio

AquaPlants no sabe cuáles de los huertos que ha vendido siguen en uso. El estado de cultivo no se
registra en ningún sistema, por lo que el seguimiento post-venta se hace cliente por cliente por
WhatsApp, sin priorización ni cobertura verificable sobre una cartera de más de 1.500 clientes.

Es un problema de gestión de información y de procesos, no un requerimiento de interfaz: cae en
trazabilidad de servicios, atención a clientes y omnicanalidad, y exige modelar un objeto de
negocio que hoy no existe en ningún sistema, el **huerto instalado**.

Precisión de alcance del diagnóstico: el CRM sí mantiene actualizados los datos del cliente y su
historial de compras, y la web registra el pedido al momento de la compra. La brecha está en el
dato posterior a la transacción, es decir, en el ciclo de vida del huerto instalado. Hoy ese
estado se estima por el paso del tiempo (un ciclo supuesto de tres meses), no se verifica.

## Impacto

La entrevista no arrojó cifras de impacto. El informe no asigna valores: declara las dimensiones
afectadas, define la métrica con la que cada una se medirá y deja explícita la línea base como dato
a levantar. Las dimensiones son tiempo (HH de contacto post-venta), cobertura de seguimiento,
servicio y abandono, ingresos por recurrencia, y calidad de atención. Ver Tabla B.3.2 del informe.

## Objetivo del SIG

**Decisión que mejora:** a qué cliente contactar en la post-venta, en qué orden y con qué mensaje.

El sistema debe convertir cada kit vendido en un objeto de seguimiento con estado conocido y fecha
de última verificación, y entregar al encargado comercial una lista priorizada de clientes cuyo
huerto está inactivo o sin verificar.

Objetivos específicos:

1. Registrar el huerto instalado como entidad propia, derivada de la orden de venta y asociada al cliente.
2. Mantener el estado de uso de cada huerto con fecha y fuente de la última verificación.
3. Priorizar y programar el contacto post-venta según antigüedad de la verificación y estado.
4. Consolidar en un solo lugar el historial de interacciones por cliente, hoy disperso entre WhatsApp, Instagram, Facebook y correo.
5. Medir la cobertura de seguimiento y la reactivación, para evaluar la mejora con datos.
