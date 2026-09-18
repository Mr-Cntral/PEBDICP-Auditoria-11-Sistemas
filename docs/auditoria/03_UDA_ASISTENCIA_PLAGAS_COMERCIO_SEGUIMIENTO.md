# **4.3 UDA-03 — Registro y Control de Asistencia Técnica a Productores con Georreferenciación**

| **Campo**          | **Definición**                                                                                                                      |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UDA                                                                                                                                 |
| Nivel de evidencia | A · TDR directo (INFORME_2026-0013_UDA) + AS-IS de campo + presentación UDA                                                         |
| Objetivo           | Digitalizar el registro y control de la asistencia técnica a productores, incorporando georreferenciación y seguimiento de visitas. |
| Cobertura          | Productores atendidos por UDA dentro de su ámbito de intervención.                                                                  |
| Fuentes base       | INFORME_2026-0013_UDA.docx; Presentacion_Indice_Proyectos_UDA-1.pdf; Consolidado AS-IS UDA/UGRF                                     |

## **Actores/usuarios**

- Técnico de campo

- Productor/beneficiario

- Coordinador/residente

- Supervisor

- Jefatura/usuario de consulta

## **Entidades y datos que la IA debe localizar**

productor, beneficiario, organización, parcela/predio, cultivo, técnico,
visita, fecha/hora, actividad/asistencia, GPS/geometry,
fotografía/evidencia, observación, recomendación, estado/revisión.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                                        | **Nivel** |
|--------|----------------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Registrar productores/técnicos y vincularlos con visitas de asistencia.                                              | A         |
| RF-02  | Registrar digitalmente cada visita/asistencia técnica.                                                               | A         |
| RF-03  | Capturar o asociar georreferenciación a la visita/predio.                                                            | A         |
| RF-04  | Consultar historial de asistencias por productor, técnico, fecha y/o ubicación.                                      | C         |
| RF-05  | Generar reportes e indicadores de cumplimiento de asistencia.                                                        | A         |
| RF-06  | Permitir evidencias/observaciones del trabajo de campo y conservar su vínculo con la visita.                         | B         |
| RF-07  | Soportar revisión/conformidad u observación del registro cuando el proceso institucional lo requiera.                | B         |
| RF-08  | Evitar visitas sin identidad de productor/técnico/fecha y sin ubicación cuando la georreferenciación es obligatoria. | C         |
| RF-09  | Permitir consolidación para informes y seguimiento del proyecto.                                                     | B         |

## **Flujo funcional esperado**

> **→** Programación o necesidad de asistencia
>
> **→** Técnico identifica productor/predio
>
> **→** Realiza visita
>
> **→** Registra actividad, ubicación, evidencias y recomendaciones
>
> **→** Envía registro
>
> **→** Supervisor/coordinador revisa
>
> **→** Si observa, retorna para corrección; si conforma, consolida
>
> **→** Se generan indicadores/reportes UDA

## **Salidas/resultados esperados**

- Ficha digital de visita

- Mapa/georreferenciación

- Historial del productor

- Reporte por técnico/comunidad/cultivo/periodo

- Indicadores de visitas y cumplimiento

- Evidencias vinculadas

## **Integraciones/dependencias**

- Datos maestros de productor/parcela/cultivo

- Módulo de proyectos/metas

- Posible reutilización de App Móvil de Campo o servicios GIS, si
  institucionalmente se integra

## **Reglas de negocio y control**

- La coordenada debe ser válida y estar vinculada a una visita/predio
  concreto.

- Una corrección no debería borrar el historial de revisión cuando
  existe workflow.

- La misma visita no debe duplicarse por reintentos sin control.

## **Pruebas mínimas que debe ejecutar la IA**

- Crear visita con GPS válido

- Buscar historial de productor

- Filtrar visitas por técnico/fecha

- Adjuntar evidencia

- Observar y corregir visita

- Generar reporte consolidado

- Validar coordenadas fuera de rango

- Intentar crear visita sin productor/técnico

## **Señales de posible incumplimiento**

- Solo CRUD de productores sin visitas

- Mapa decorativo sin coordenadas persistidas

- Visitas sin vínculo a productor/técnico

- Fotos sin metadatos o sin relación a visita

- Reporte estático

- No existe historial

# **4.4 UDA-04 — Gestión de Incidencias y Seguimiento de Plagas para Cacao y Camu Camu**

| **Campo**          | **Definición**                                                                                          |
|--------------------|---------------------------------------------------------------------------------------------------------|
| Unidad             | UDA                                                                                                     |
| Nivel de evidencia | A · TDR directo (INFORME_2026-0014_UDA) + presentación UDA                                              |
| Objetivo           | Gestionar incidencias fitosanitarias, alertas y seguimiento de plagas en cultivos de cacao y camu camu. |
| Cobertura          | Cacao y camu camu atendidos por UDA.                                                                    |
| Fuentes base       | INFORME_2026-0014_UDA.docx; Presentacion_Indice_Proyectos_UDA-1.pdf; Consolidado AS-IS UDA              |

## **Actores/usuarios**

- Técnico/especialista

- Productor

- Coordinador/supervisor

- Administrador fitosanitario

- Jefatura/consulta

## **Entidades y datos que la IA debe localizar**

cultivo, parcela/productor, plaga, incidencia, fecha/hora, ubicación,
observación/síntoma, nivel/severidad si el formato lo contempla, alerta,
acción/control, seguimiento, estado, evidencia.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                         | **Nivel** |
|--------|-------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Registrar catálogo/identificación de plagas y cultivos objetivo.                                      | A         |
| RF-02  | Registrar incidencias fitosanitarias vinculadas a cultivo/productor/parcela.                          | A         |
| RF-03  | Implementar módulo de alertas fitosanitarias.                                                         | A         |
| RF-04  | Permitir seguimiento posterior de la incidencia/plaga y registrar acciones de control.                | A         |
| RF-05  | Generar reportes e indicadores de incidencias/plagas.                                                 | A         |
| RF-06  | Conservar fecha, ubicación y evidencia cuando se dispone de datos de campo.                           | B         |
| RF-07  | Distinguir una incidencia reportada de una incidencia resuelta/cerrada mediante estados equivalentes. | C         |
| RF-08  | Evitar que una alerta sea solo un registro manual sin regla/evento que la origine.                    | C         |

## **Flujo funcional esperado**

> **→** Detección/reportada en campo
>
> **→** Registro de incidencia
>
> **→** Clasificación de cultivo/plaga
>
> **→** Evaluación técnica
>
> **→** Generación de alerta cuando corresponda
>
> **→** Asignación/recomendación de control
>
> **→** Seguimiento
>
> **→** Verificación de resultado
>
> **→** Cierre y reporte

## **Salidas/resultados esperados**

- Ficha de incidencia

- Alertas activas

- Historial de seguimiento

- Mapa/listado por zona

- Reporte por plaga/cultivo/periodo

- Indicadores

## **Integraciones/dependencias**

- Asistencia técnica georreferenciada

- Datos maestros de productor/parcela/cultivo

- Posibles fuentes técnicas/knowledge base

## **Reglas de negocio y control**

- Una incidencia debe conservar su evolución y no sobrescribirse como si
  nunca hubiese existido.

- El catálogo de plagas debe evitar nombres duplicados/inconsistentes.

- Los estados y umbrales definitivos requieren validación institucional
  si no están en TDR.

## **Pruebas mínimas que debe ejecutar la IA**

- Registrar incidencia cacao

- Registrar incidencia camu camu

- Generar alerta

- Agregar seguimiento y control

- Cerrar incidencia

- Consultar historial

- Filtrar por plaga/fecha/ubicación

- Intentar usar cultivo no permitido

## **Señales de posible incumplimiento**

- Solo catálogo de plagas

- Alertas hardcodeadas

- No existe seguimiento temporal

- No se puede saber si la incidencia fue atendida

- Datos sin productor/parcela

- Reportes estáticos

# **4.5 UDA-05 — Módulo de Comercio Electrónico y Vitrina Digital para Productos Amazónicos**

| **Campo**          | **Definición**                                                                                                                    |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UDA                                                                                                                               |
| Nivel de evidencia | A · TDR directo (INFORME_2026-0016_UDA) + presentación UDA                                                                        |
| Objetivo           | Facilitar la comercialización de cacao, camu camu y aguaje mediante catálogo/vitrina digital y funciones de comercio electrónico. |
| Cobertura          | Oferta productiva UDA de cacao, camu camu y aguaje.                                                                               |
| Fuentes base       | INFORME_2026-0016_UDA.docx; Presentacion_Indice_Proyectos_UDA-1.pdf; INFORME_2026-0008_UDA.docx                                   |

## **Actores/usuarios**

- Productor/ofertante

- Comprador/cliente

- Administrador de catálogo

- UDA/usuario de seguimiento

## **Entidades y datos que la IA debe localizar**

productor, producto, categoría/cultivo, ficha técnica, imagen,
precio/presentación/unidad, disponibilidad, pedido, detalle pedido,
cliente, medio de pago, estado pedido, fecha, indicador de venta.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                        | **Nivel** |
|--------|----------------------------------------------------------------------|-----------|
| RF-01  | Levantar/gestionar oferta productiva y canales de comercialización.  | A         |
| RF-02  | Disponer de catálogo y vitrina digital de productos amazónicos.      | A         |
| RF-03  | Mostrar fichas técnicas de productos.                                | A         |
| RF-04  | Implementar flujo de comercio electrónico/pedidos.                   | A         |
| RF-05  | Integrar medios de pago conforme a lo definido en la implementación. | A         |
| RF-06  | Relacionar productos con productores/oferta real.                    | A/B       |
| RF-07  | Registrar pedidos y sus estados para permitir seguimiento.           | A/C       |
| RF-08  | Generar indicadores de ventas/comercialización.                      | A         |
| RF-09  | Evitar checkout ficticio o confirmaciones sin persistencia/backend.  | C         |

## **Flujo funcional esperado**

> **→** Productor/oferta se registra
>
> **→** Administrador publica producto y ficha
>
> **→** Comprador consulta vitrina
>
> **→** Selecciona producto/cantidad
>
> **→** Sistema crea pedido
>
> **→** Se procesa/registran medio de pago y resultado
>
> **→** Pedido cambia de estado
>
> **→** Sistema actualiza indicadores/reportes

## **Salidas/resultados esperados**

- Vitrina/catálogo

- Ficha técnica

- Pedido y detalle

- Comprobante/resultado de pago según integración

- Panel de pedidos

- Indicadores de ventas

## **Integraciones/dependencias**

- Datos maestros de productores

- Inteligencia de mercados/precios como insumo analítico

- Calidad/inocuidad y trazabilidad como información complementaria si se
  formaliza

## **Reglas de negocio y control**

- El producto publicado debe tener productor/origen y datos suficientes
  para comercialización.

- No marcar un pedido como pagado sin evidencia de pago o mecanismo
  equivalente.

- La vitrina debe distinguir productos activos/no disponibles.

## **Pruebas mínimas que debe ejecutar la IA**

- Publicar producto

- Buscar/filtrar catálogo

- Crear pedido

- Validar total

- Procesar/registrar pago

- Cambiar estado de pedido

- Cancelar/rechazar pago

- Indicadores se actualizan

## **Señales de posible incumplimiento**

- Solo landing page de productos

- Botón Comprar sin backend

- Pedido no persiste

- Medio de pago simulado sin marcar demo

- Indicadores estáticos

- Productos seed presentados como oferta real

# **4.6 UDA-06 — Plataforma de Seguimiento de Proyectos, Indicadores y Metas**

| **Campo**          | **Definición**                                                                                                           |
|--------------------|--------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UDA                                                                                                                      |
| Nivel de evidencia | A · Presentación UDA para la aplicación; B · AS-IS institucional para alcance ampliado                                   |
| Objetivo           | Centralizar el seguimiento de proyectos UDA, sus indicadores y metas, permitiendo visualizar avance y apoyar la gestión. |
| Cobertura          | Proyectos e indicadores bajo responsabilidad de UDA/PEBDICP.                                                             |
| Fuentes base       | Presentacion_Indice_Proyectos_UDA-1.pdf; Consolidado AS-IS UDA/UGRF                                                      |

## **Actores/usuarios**

- Jefatura UDA

- Coordinador/residente

- Supervisor

- Administrador del proyecto

- Usuario de seguimiento/consulta

## **Entidades y datos que la IA debe localizar**

proyecto, CUI cuando corresponda, indicador, meta, periodo, valor
programado, valor ejecutado, estado, responsable, actividad/componente,
evidencia, tablero.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                                               | **Nivel** |
|--------|-----------------------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Registrar y gestionar proyectos.                                                                                            | A         |
| RF-02  | Registrar indicadores y metas vinculados al proyecto.                                                                       | A         |
| RF-03  | Mostrar tableros de control y KPIs calculados desde datos persistidos.                                                      | A         |
| RF-04  | Permitir seguimiento por periodo y comparación programado vs ejecutado.                                                     | C         |
| RF-05  | Identificar metas atrasadas, cumplidas o con desviación mediante estados/alertas equivalentes.                              | B/C       |
| RF-06  | Relacionar proyecto con componentes/actividades y responsables cuando esos datos existan.                                   | B         |
| RF-07  | Permitir adjuntar o referenciar evidencia/informe que sustente el avance.                                                   | B         |
| RF-08  | Alinear, cuando se defina institucionalmente, la información física-financiera y datos requeridos para seguimiento/F12-12B. | B/D       |
| RF-09  | Conservar histórico de cambios de metas/avances relevantes.                                                                 | C         |

## **Flujo funcional esperado**

> **→** Crear/registrar proyecto
>
> **→** Definir indicadores y metas
>
> **→** Registrar avance periódico
>
> **→** Adjuntar/sustentar evidencia
>
> **→** Calcular cumplimiento/desviación
>
> **→** Supervisor/jefatura revisa
>
> **→** Dashboard consolida
>
> **→** Se generan alertas/reportes y acciones de gestión

## **Salidas/resultados esperados**

- Dashboard de proyectos

- Indicadores/metas

- Semáforo o estado de cumplimiento

- Reporte de avance

- Historial por periodo

- Alertas/desviaciones

## **Integraciones/dependencias**

- Datos de proyectos/CUI

- Información de coordinación/supervisión

- Posible F12/12-B y SISGED: integración específica pendiente de validar

## **Reglas de negocio y control**

- Los KPIs deben calcularse con datos reales, no valores fijos.

- Cambios de meta no deberían borrar la meta anterior sin historial.

- No afirmar integración con 12-B/SISGED si no existe evidencia técnica.

## **Pruebas mínimas que debe ejecutar la IA**

- Crear proyecto e indicador

- Definir meta mensual/anual

- Registrar avance

- Calcular porcentaje

- Modificar meta con historial

- Filtrar proyectos atrasados

- Generar reporte

- Validar permisos de edición

## **Señales de posible incumplimiento**

- Dashboard sin relación con proyectos

- Metas sin periodo/responsable

- Porcentaje escrito manualmente sin cálculo

- No hay histórico

- Alertas decorativas

- CUI/proyecto duplicado sin control
