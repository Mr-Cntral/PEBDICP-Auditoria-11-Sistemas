**PEBDICP**

**MATRIZ MAESTRA DE VERIFICACIÓN FUNCIONAL**

**11 sistemas de UDA y UGRF**

*Documento consolidado para auditoría técnica y revisión por
inteligencia artificial*

| **Propósito:** servir como especificación de referencia para verificar si cada sistema implementado cumple con su objetivo, alcance funcional, flujo institucional, datos, controles, integraciones y evidencias mínimas esperadas. No reemplaza una conformidad formal del área usuaria ni de Informática. |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

| **Regla de uso:** cuando un requisito figure como “Confirmado”, debe exigirse evidencia objetiva. Cuando figure como “Derivado del AS-IS” o “Inferencia técnica”, debe evaluarse como alineamiento esperado y no como obligación contractual salvo que exista un TDR adicional que lo formalice. |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

Consolidado al 18 de septiembre de 2026

# **1. Cómo interpretar este documento**

Este documento consolida la información funcional construida durante el
levantamiento del PEBDICP para UDA y UGRF. Su objetivo es que una
persona o una IA pueda revisar un sistema real —código fuente, base de
datos, APIs, pantallas, manuales, capturas o despliegue— y determinar
qué se cumple, qué se cumple parcialmente, qué no existe y qué no puede
verificarse con la evidencia disponible.

## **1.1 Niveles de certeza**

| **Nivel**                              | **Significado**                                                                                                                                      | **Cómo debe usarlo la IA auditora**                                                                              |
|----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
| A · Confirmado                         | Existe TDR, informe, presentación o evidencia directa que exige o describe el punto.                                                                 | Tratarlo como requisito verificable. Si no existe evidencia en el sistema, marcar NO CUMPLE o NO VERIFICABLE.    |
| B · Confirmado por flujo institucional | El punto está respaldado por el AS-IS, documentos de proyectos o actores institucionales, aunque no figure literalmente en el TDR de una aplicación. | Evaluar alineamiento institucional y trazabilidad; no convertirlo automáticamente en incumplimiento contractual. |
| C · Inferencia técnica fuerte          | Se deriva del objetivo del sistema y de prácticas mínimas necesarias para que la función tenga sentido.                                              | Usarlo como criterio de calidad/diseño y señalar que requiere validación formal.                                 |
| D · Pendiente                          | No hay evidencia suficiente o la decisión corresponde a PEBDICP/UGRF/UDA.                                                                            | No inventar. Marcar PENDIENTE DE VALIDACIÓN.                                                                     |

## **1.2 Estados de auditoría recomendados**

| **Estado**                            | **Definición**                                                                                                             |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| CUMPLE                                | Existe evidencia funcional, de datos y/o de código suficiente y coherente con el requisito.                                |
| CUMPLE PARCIALMENTE                   | Existe una parte funcional, pero falta un subflujo, regla, integración, dato o evidencia relevante.                        |
| NO CUMPLE                             | La función requerida no existe, está simulada, usa datos ficticios como operación real o no produce el resultado esperado. |
| NO VERIFICABLE                        | No se pudo revisar por falta de acceso, datos, credenciales, código, entorno o documentación.                              |
| NO APLICA                             | El punto no corresponde al sistema evaluado o es una recomendación no formalizada.                                         |
| PENDIENTE DE VALIDACIÓN INSTITUCIONAL | La regla depende de una decisión que UDA/UGRF/Informática debe aprobar.                                                    |

## **1.3 Fuentes consolidadas**

| **Grupo**          | **Fuente**                                                                       | **Aporte**                                                                                                                         |
|--------------------|----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
| UDA · TDR/Informes | INFORME_2026-0002_UDA.docx                                                       | Asistente virtual inteligente con PLN.                                                                                             |
| UDA · TDR/Informes | INFORME_2026-0003_UDA.docx                                                       | Sistema predictivo y analítico de rendimientos.                                                                                    |
| UDA · TDR/Informes | INFORME_2026-0013_UDA.docx                                                       | Registro y control de asistencia técnica georreferenciada.                                                                         |
| UDA · TDR/Informes | INFORME_2026-0014_UDA.docx                                                       | Incidencias y seguimiento de plagas.                                                                                               |
| UDA · TDR/Informes | INFORME_2026-0016_UDA.docx                                                       | Comercio electrónico y vitrina digital.                                                                                            |
| UDA · Presentación | Presentacion_Indice_Proyectos_UDA-1.pdf                                          | Resumen de 6 aplicaciones, estado, arquitectura y modelos de datos.                                                                |
| UDA · Consultorías | INFORME_2026-0004 / 0008 / 0011 / 0015 / xxx-2026-xxxx                           | Trazabilidad cacao; inteligencia de mercados; gestión de datos; calidad/inocuidad; estrategia de automatización.                   |
| UGRF · Inventario  | Proyectos_Persona_Natural_Ordenado.xlsx y equivalentes                           | Nombres de servicios UGRF: incendios, app móvil, auditoría, monitoreo ambiental.                                                   |
| UGRF · Portal      | Portal UGRF: Gestión Forestal Integral                                           | Confirma los módulos visibles: Alerta de Incendios, Auditoría, Gestión del Conocimiento, Monitoreo Ambiental y App Móvil de Campo. |
| AS-IS              | Consolidado de flujos UGRF/UDA (agosto 2026)                                     | Actores, documentos, seguimiento físico-financiero, F12/12-B, SISGED, campo y cierre.                                              |
| Incendios          | Investigación técnica de Alerta y Monitoreo de Incendios Forestales (04/09/2026) | Fuentes oficiales, arquitectura, flujo, estados, roles, datos, evidencias e integraciones.                                         |

# **2. Contexto institucional y flujo común que condiciona los 11 sistemas**

UGRF y UDA son unidades de línea del PEBDICP y trabajan dentro de un
ciclo de proyectos que combina ejecución técnica, trabajo de campo,
administración, contratación, seguimiento físico-financiero, documentos,
evaluación, decisiones y cierre. Por eso un sistema no debe evaluarse
solo por la existencia de pantallas CRUD; debe comprobarse que resuelve
el problema operativo y conserva trazabilidad suficiente.

## **2.1 Flujo AS-IS maestro consolidado**

> **→** Necesidad / proyecto / actividad programada.
>
> **→** Solicitud, pedido, requerimiento o actividad originada por el
> proyecto/área usuaria.
>
> **→** Administración del proyecto coordina recursos, documentación y
> soporte operativo.
>
> **→** Especialistas, técnicos o contratistas ejecutan actividades y
> generan evidencias.
>
> **→** Coordinador/residente consolida información técnica; supervisor
> verifica avance físico y financiero.
>
> **→** El proyecto genera informe técnico, informe de supervisión,
> reporte de avance y/o información para seguimiento.
>
> **→** Jefatura UGRF/UDA revisa y emite Informe UGRF/UDA u Oficio según
> corresponda.
>
> **→** Administración/Abastecimiento y/o UAJ intervienen cuando el
> trámite lo requiere.
>
> **→** Dirección Ejecutiva adopta decisiones y, en diversos casos,
> formaliza mediante Resolución Directoral.
>
> **→** El proyecto continúa, subsana, modifica, amplía o cierra.
>
> **→** El cierre se sustenta con informe final, consolidación
> física-financiera, liquidación y decisión correspondiente.

## **2.2 Microflujo de campo que debe reflejarse en sistemas operativos**

El patrón de campo usado como referencia de diseño es: programación/meta
→ técnico asignado → productor/comunidad/predio → actividad o visita →
registro de datos y evidencia → revisión del coordinador/supervisor →
conformidad u observación → consolidado → informe/seguimiento. Los
campos exactos de cada ficha deben contrastarse con formatos
institucionales reales; el flujo sí es una referencia funcional fuerte.

| **Etapa**          | **Datos/evidencias típicas**                                                                             | **Responsable habitual**                  |
|--------------------|----------------------------------------------------------------------------------------------------------|-------------------------------------------|
| Programación       | Proyecto, actividad, meta, fecha, comunidad/ámbito                                                       | Coordinador / administración del proyecto |
| Ejecución de campo | Productor/beneficiario, parcela/predio, cultivo o recurso forestal, GPS, fotos, actividad, observaciones | Técnico / especialista                    |
| Revisión           | Cumplimiento de actividad, consistencia de evidencia, observaciones                                      | Supervisor / coordinador                  |
| Consolidación      | Avance físico, relación de actividades, resultados, incidencias                                          | Proyecto / supervisor                     |
| Seguimiento        | Indicadores, metas, avance físico-financiero, alertas                                                    | Jefatura / responsables de seguimiento    |
| Cierre             | Informe final, evidencia, liquidación cuando corresponda                                                 | Proyecto / unidad / Dirección             |

## **2.3 Actores y roles transversales**

| **Actor**                                                | **Participación esperada**                                                                                        |
|----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
| Dirección Ejecutiva                                      | Aprobaciones y decisiones institucionales; resoluciones cuando corresponde.                                       |
| Jefe UGRF / Jefe UDA                                     | Revisión, control y supervisión de procesos y proyectos de su unidad.                                             |
| Coordinador / residente de proyecto                      | Coordina componentes, actividades, personal y consolidación técnica.                                              |
| Supervisor                                               | Verifica cumplimiento físico y financiero; formula observaciones e informes.                                      |
| Administrador del proyecto                               | Pedidos, documentación administrativa, soporte de ejecución y coordinación.                                       |
| Técnicos / especialistas / extensionistas                | Trabajo de campo, asistencia, levantamiento de datos y evidencias.                                                |
| Unidad de Administración / Abastecimiento                | Contratación, órdenes, contratos, pagos, gestión documentaria y apoyo administrativo.                             |
| UAJ                                                      | Opinión legal y revisión cuando el trámite lo exige.                                                              |
| Informática                                              | Arquitectura, seguridad, interoperabilidad, integración, usuarios, respaldo y conformidad técnica complementaria. |
| Productores / beneficiarios / comunidades / asociaciones | Usuarios externos, receptores de asistencia y fuente de datos de campo/productivos.                               |

## **2.4 Datos maestros y componentes compartidos**

Los 11 sistemas pueden ser aplicaciones separadas, pero no deberían
duplicar sin control los mismos identificadores. La arquitectura
conceptual construida previamente propone una capa común de datos
maestros y trazabilidad.

- Usuarios, roles, unidad organizacional y permisos.

- Proyectos de inversión: CUI, expediente/estudio, componentes,
  actividades, metas, presupuesto y cronograma.

- Productores/beneficiarios, organizaciones, comunidades y ámbitos
  territoriales.

- Predios/parcelas, cultivos, recursos forestales y
  geometrías/ubicaciones.

- Técnicos, visitas, asistencias, incidencias, evidencias y
  observaciones.

- Documentos: solicitudes, informes, oficios, cartas, TDR, contratos,
  órdenes, resoluciones, observaciones e historial.

- Seguimiento: avance físico, avance financiero, indicadores, alertas y
  datos relacionados con F12/12-B.

- Catálogos especializados: plagas, productos, precios/mercados,
  conocimiento técnico, fuentes ambientales y tipos de incidente.

## **2.5 Reglas transversales de verificación**

- No considerar “implementado” un sistema que solo tenga login,
  dashboard y CRUD genérico si no ejecuta la función sustantiva
  contratada.

- Toda información simulada/seed debe distinguirse de información
  operativa; la IA debe detectar datos ficticios usados como si fueran
  producción.

- Las operaciones sensibles deben tener trazabilidad de usuario,
  fecha/hora y cambios relevantes.

- Los roles deben impedir que cualquier usuario ejecute acciones
  administrativas o de cierre sin autorización.

- Los sistemas de campo deben conservar ubicación/evidencia cuando la
  función depende de georreferenciación.

- Los modelos predictivos deben demostrar cálculo/modelo real y
  métricas; no basta mostrar un número aleatorio o una fórmula fija sin
  sustento.

- Las integraciones declaradas deben probarse en código/configuración o
  mediante llamadas reales; un botón sin backend no cuenta como
  integración.

- Los reportes e indicadores deben calcularse desde datos persistidos y
  reproducibles.

- El sistema debe permitir distinguir estado actual e historial cuando
  existe workflow.

- Cuando una regla institucional no está definida (por ejemplo SLA o
  responsable de cierre), no inventar: parametrizar o marcar pendiente.
