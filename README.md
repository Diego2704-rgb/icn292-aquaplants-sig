# SIG de seguimiento post-venta de huertos hidropónicos — Caso AquaPlants

**ICN-292 · Departamento de Industrias · UTFSM · Segundo semestre 2026**
Entrega 1 — Informe. Entrega 2 — Sistema demostrable en localhost.

---

## 1. Qué PYME y qué problema

**AquaPlants** (aquaplants.cl) es una microempresa chilena que produce y vende sistemas de
cultivo hidropónico doméstico. Su producto principal es el kit *Torre AquaPlants*, que se vende
como paquete completo (estructura, almácigos y nutrientes), junto con insumos consumibles que
generan demanda recurrente. Tiene cinco personas de dotación permanente y una cartera declarada
de más de 1.500 clientes.

**El problema.** AquaPlants no sabe cuáles de los huertos que ha vendido siguen en uso. El estado
de cultivo no se registra en ningún sistema, por lo que el seguimiento post-venta se hace cliente
por cliente por WhatsApp, sin priorización ni cobertura verificable.

La brecha no está en el dato de la transacción: el CRM mantiene al día los datos del cliente y su
historial de compras, y la web registra el pedido automáticamente. La brecha está en el dato
posterior a la venta. **El huerto instalado no existe como entidad en ningún sistema**, y por eso
su estado no es consultable, filtrable ni medible.

**Objetivo del SIG.** Convertir cada kit vendido en un objeto de seguimiento con estado conocido y
fecha de última verificación, y entregar al encargado comercial una lista priorizada de clientes
cuyo huerto está inactivo o sin verificar. La decisión que mejora es: a qué cliente contactar en
la post-venta, en qué orden y con qué mensaje.

La evidencia proviene de una entrevista presencial a **Gabriel Daszenies**, socio fundador y
encargado comercial, realizada el **07-09-2026** (acta completa en el Anexo A del informe).

---

## 2. Qué hay en cada carpeta

| Ruta | Contenido |
| --- | --- |
| `docs/00-caso-pyme.md` | La PYME, evidencia de existencia, problema de negocio, impacto y objetivo del SIG. |
| `docs/01-requerimientos.md` | Actores y roles, alcance in/out, requisitos funcionales (RF) y no funcionales (RNF) priorizados, trazabilidad y supuestos. |
| `docs/02-bpmn.md` | Proceso crítico modelado en BPMN 2.0: as-is, to-be y explicación de las mejoras. Los diagramas exportados están en `assets/`. |
| `docs/03-er-preliminar.md` | Modelo de datos preliminar: entidades, atributos, llaves candidatas y relaciones. |
| `assets/` | Diagramas exportados en PNG (BPMN as-is, BPMN to-be, modelo ER) más los archivos fuente `.bpmn` cuando corresponde. Cada imagen se referencia desde el `.md` que la explica. |
| `informe/` | **Informe de la Entrega 1 en PDF y en Word (`.docx`) o LaTeX (`.tex`).** Son exactamente los mismos archivos entregados en Aula. |

Los documentos de `docs/` son la versión navegable del informe. Ante cualquier diferencia, **manda
el informe de `informe/`**, que es el entregable formal.

---

## 3. Cómo se relaciona con la Entrega 2 (localhost)

Este repositorio es el mismo que alojará el sistema de la Entrega 2. La Entrega 1 define **qué** se
va a construir; la Entrega 2 lo construye y lo demuestra.

- El sistema se demostrará **levantado en localhost**, no en un servidor productivo. Este README se
  ampliará con la sección de instalación, las dependencias con versión fija y el script de carga de
  datos de prueba, de modo que un tercero pueda levantarlo siguiendo solo estas instrucciones
  (RNF-05).
- El alcance comprometido para la Entrega 2 son los requisitos de prioridad **Must** (RF-01 a
  RF-08), documentados en `docs/01-requerimientos.md`.
- El modelo de datos de `docs/03-er-preliminar.md` se implementará como `schema.sql` y se mantendrá
  documentado junto al código (RNF-09).
- **Los datos de prueba son sintéticos.** El repositorio no contiene ni contendrá datos reales de
  clientes de AquaPlants, en coherencia con la sección G del informe (Ley 21.719).
- Se trabaja con una rama por funcionalidad y cada cambio entra por pull request revisado por un
  integrante distinto al autor.

---

## 4. Integrantes y roles

| Integrante | Rol en el proyecto |
| --- | --- |
| Diego Zuñiga | Contraparte con la PYME y levantamiento de requerimientos (entrevistador en la visita del 07-09-2026) |
| Mateo Carbajal Inostroza | Modelo de datos (ER) y llaves candidatas |
| Felipe Vargas | Modelado de procesos (BPMN as-is / to-be) |
| Pedro Barrios | Arquitectura lógica, stack y administración del repositorio |
| Agustin Gonzalez | Coordinación, KPI y control de la Entrega 2 |

---

## 5. Informe y entrega en Aula

- Informe completo (PDF): [`informe/Entrega1_ICN292_AquaPlants.pdf`](informe/)
- Fuente editable (Word): [`informe/Entrega1_ICN292_AquaPlants.docx`](informe/)
- Entrega en Aula: los mismos archivos fueron subidos a la tarea correspondiente de la Entrega 1.

---

*Última actualización: [fecha]. Contacto del equipo para el acceso al repositorio: [correo].*
