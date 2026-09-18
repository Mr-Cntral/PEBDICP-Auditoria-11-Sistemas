# **4.10 UGRF-04 — Plataforma Tecnológica de Monitoreo Ambiental Integrada con Datos Satelitales y Climáticos**

| **Campo**          | **Definición**                                                                                                                                         |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UGRF                                                                                                                                                   |
| Nivel de evidencia | A · título del servicio confirmado; C · detalle funcional derivado del objeto técnico                                                                  |
| Objetivo           | Monitorear aguajales y ecosistemas inundables usando información ambiental integrada, datos satelitales y climáticos consumidos vía APIs/geoservicios. |
| Cobertura          | Aguajales y ecosistemas inundables de interés para UGRF/PEBDICP.                                                                                       |
| Fuentes base       | Proyectos_Persona_Natural_Ordenado.xlsx; Portal UGRF: Gestión Forestal Integral; Consolidado AS-IS UGRF                                                |

## **Actores/usuarios**

- Especialista ambiental/forestal

- Técnico UGRF

- Jefatura/analista

- Administrador técnico

## **Entidades y datos que la IA debe localizar**

área/ecosistema, geometry/polígono, fuente, fecha de observación,
variable satelital, variable climática, indicador ambiental, serie
temporal, observación de campo, alerta/anomalía, capa geográfica,
metadatos de fuente.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                                                | **Nivel** |
|--------|------------------------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Integrar al menos las fuentes satelitales/climáticas que hayan sido definidas para la plataforma mediante APIs/geoservicios. | A         |
| RF-02  | Representar espacialmente aguajales/ecosistemas y capas de monitoreo.                                                        | A/C       |
| RF-03  | Consultar información por área y periodo, conservando serie temporal/histórico.                                              | C         |
| RF-04  | Calcular/mostrar indicadores ambientales derivados de datos integrados.                                                      | C         |
| RF-05  | Registrar la fuente y fecha de actualización de cada dato/capa.                                                              | C         |
| RF-06  | Permitir observaciones de campo complementarias cuando formen parte del monitoreo.                                           | B/C       |
| RF-07  | Generar reportes y visualizaciones para gestión ambiental.                                                                   | C         |
| RF-08  | Gestionar fallas de fuente externa sin reemplazar silenciosamente datos reales por seed.                                     | C         |

## **Flujo funcional esperado**

> **→** Conector consulta APIs/geoservicios
>
> **→** Normaliza datos
>
> **→** Asocia espacial/temporalmente con ecosistema
>
> **→** Almacena serie
>
> **→** Calcula indicador/anomalía
>
> **→** Visualiza mapa/gráficos
>
> **→** Especialista analiza
>
> **→** Genera reporte/observación

## **Salidas/resultados esperados**

- Mapa/capas

- Serie temporal

- Indicadores ambientales

- Ficha de área/ecosistema

- Estado de fuentes

- Reportes

## **Integraciones/dependencias**

- APIs/geoservicios satelitales y climáticos definidos por el proyecto

- GIS/PostGIS o capacidad espacial equivalente

- App móvil de campo como posible fuente de observaciones, si se integra

## **Reglas de negocio y control**

- Cada dato ambiental debe indicar fuente/fecha.

- No presentar datos de ejemplo como monitoreo en tiempo real.

- La plataforma debe seguir funcionando de forma controlada cuando una
  API externa falle, dejando trazabilidad del error/última
  actualización.

## **Pruebas mínimas que debe ejecutar la IA**

- Consultar área

- Cambiar periodo

- Ver fuente/fecha

- Caída de API

- Comparar series

- Cargar/visualizar observación de campo si aplica

- Exportar reporte

- Validar geometría fuera del ámbito

## **Señales de posible incumplimiento**

- Mapa estático

- Datos climáticos hardcodeados

- No hay fecha de actualización

- No se consumen APIs

- Indicadores no reproducibles

- No existe histórico

- Aguajales no están georreferenciados

# **4.11 UGRF-05 — Aplicación Móvil Inteligente para Recojo de Datos Georreferenciados, Incidencias y Fiscalización en Campo**

| **Campo**          | **Definición**                                                                                                                                 |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UGRF                                                                                                                                           |
| Nivel de evidencia | A · título del servicio confirmado; B · flujo de campo institucional; C · detalle técnico mínimo                                               |
| Objetivo           | Permitir a técnicos UGRF capturar en campo información georreferenciada, incidencias, fiscalizaciones y evidencias desde dispositivos móviles. |
| Cobertura          | Trabajo de campo de técnicos UGRF dentro del ámbito PEBDICP definido.                                                                          |
| Fuentes base       | Proyectos_Persona_Natural_Ordenado.xlsx; Consolidado AS-IS UGRF; Portal UGRF: Gestión Forestal Integral                                        |

## **Actores/usuarios**

- Técnico de campo

- Supervisor/coordinador

- Administrador UGRF

- Usuario de consulta/revisión

## **Entidades y datos que la IA debe localizar**

usuario técnico, fecha/hora, GPS, comunidad/ámbito, proyecto/actividad,
tipo de registro, incidencia, fiscalización/inspección, observación,
fotografía/video, firma/acta si el proceso la usa, estado de
sincronización, revisión.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                                                                   | **Nivel** |
|--------|-------------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Capturar datos desde dispositivo móvil y asociarlos al técnico autenticado.                                                                     | A         |
| RF-02  | Capturar georreferenciación de los registros.                                                                                                   | A         |
| RF-03  | Registrar incidencias de campo.                                                                                                                 | A         |
| RF-04  | Registrar información de fiscalización/inspección en campo.                                                                                     | A         |
| RF-05  | Adjuntar evidencias de campo y conservar vínculo con ubicación/fecha/usuario.                                                                   | B/C       |
| RF-06  | Permitir envío/sincronización hacia el backend institucional.                                                                                   | C         |
| RF-07  | Mostrar al supervisor/coordinador los registros enviados para revisión/seguimiento.                                                             | B         |
| RF-08  | Evitar duplicados por reintentos de sincronización.                                                                                             | C         |
| RF-09  | Modo offline/cola local es recomendable por el contexto territorial, pero no debe marcarse como obligación contractual sin TDR que lo confirme. | D         |

## **Flujo funcional esperado**

> **→** Técnico inicia sesión
>
> **→** Selecciona proyecto/actividad/tipo de registro
>
> **→** Captura GPS
>
> **→** Completa formulario
>
> **→** Adjunta evidencia
>
> **→** Guarda/envía
>
> **→** Backend valida y persiste
>
> **→** Supervisor revisa
>
> **→** Se observa/corrige o consolida
>
> **→** Registro alimenta reportes/sistemas especializados

## **Salidas/resultados esperados**

- Registro georreferenciado

- Ficha de incidencia/fiscalización

- Evidencias

- Mapa de registros

- Bandeja de revisión

- Reporte por técnico/zona/periodo

## **Integraciones/dependencias**

- Usuarios/roles UGRF

- GIS/mapas

- Monitoreo ambiental e incendios como posibles receptores de registros
  si se integra

- Proyectos/actividades

## **Reglas de negocio y control**

- No permitir coordenadas inválidas.

- La evidencia debe mantener autor/fecha/registro asociado.

- La sincronización debe ser idempotente para no duplicar registros.

- No afirmar modo offline si solo funciona con conexión.

## **Pruebas mínimas que debe ejecutar la IA**

- Captura GPS

- Adjuntar foto

- Enviar incidencia

- Enviar fiscalización

- Duplicar envío/retry

- Usuario no autorizado

- Supervisor revisa registro

- Pérdida de red durante captura si existe soporte offline

## **Señales de posible incumplimiento**

- Formulario web no adaptado a móvil

- GPS no persistido

- Foto no asociada al registro

- No existe backend/sincronización

- Registros duplicados por reintento

- Cualquier usuario puede alterar evidencia ya revisada

# **5. Consultorías UDA que condicionan la verificación de los sistemas**

Estas iniciativas aparecen en los informes UDA cargados, pero no deben
confundirse con aplicaciones operativas. Su función es definir diseño,
gobernanza, procesos, modelos o controles que luego deberían reflejarse
en los sistemas cuando corresponda.

| **Fuente**                | **Consultoría**                                                | **Qué exige**                                                                                                                                          | **Impacto en auditoría**                                                                                                               |
|---------------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| INFORME_2026-0004_UDA     | Diseño de trazabilidad de cacao basada en registro distribuido | Cadena de valor del cacao, puntos de control, brechas, requerimientos funcionales, gobernanza, evaluación de tecnologías y hoja de ruta.               | Afecta datos de origen/lotes/actores y trazabilidad. No implica por sí solo que blockchain deba estar implementado en los 11 sistemas. |
| INFORME_2026-0008_UDA     | Inteligencia de mercados y análisis predictivo de precios      | Información de mercados/precios de camu camu y aguaje, modelos predictivos, reportes/tableros y hoja de ruta.                                          | Puede alimentar comercio electrónico y decisiones productivas; es consultoría, no el sistema de comercio.                              |
| INFORME_2026-0011_UDA     | Plan de gestión de datos y ciencia de datos                    | Inventario/fuentes, brechas, madurez, gobernanza, estándares, casos de uso y hoja de ruta.                                                             | Condiciona identificadores maestros, calidad, interoperabilidad y trazabilidad de datos en todas las aplicaciones UDA.                 |
| INFORME_2026-0015_UDA     | Sistema de gestión de calidad e inocuidad en plantas           | Diagnóstico, procedimientos/registros, saneamiento, BPM, HACCP, controles y capacitación.                                                              | Aporta datos/controles de calidad a la cadena productiva; no es necesariamente una aplicación informática.                             |
| INFORME_xxx-2026-xxxx_UDA | Estrategia de soluciones inteligentes y automatización         | Mapa de procesos de asistencia, beneficiarios, cultivos y reportes; brechas, cuellos de botella, reprocesos, priorización, tecnologías y hoja de ruta. | Sirve como marco para comprobar que las aplicaciones reducen reprocesos y no duplican información sin necesidad.                       |
