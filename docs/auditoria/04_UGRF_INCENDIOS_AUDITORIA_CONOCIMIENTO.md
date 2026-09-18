# **4.7 UGRF-01 — Sistema Inteligente de Alerta Temprana y Monitoreo de Incendios Forestales**

| **Campo**          | **Definición**                                                                                                                                                                                                  |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UGRF                                                                                                                                                                                                            |
| Nivel de evidencia | A · nombre/servicio confirmado; B/C · diseño técnico detallado consolidado el 04/09/2026                                                                                                                        |
| Objetivo           | Detectar automáticamente focos de calor y alertas oficiales que afecten el ámbito PEBDICP, georreferenciarlos, enriquecerlos, validarlos, asignar responsables y registrar atención/evidencias hasta el cierre. |
| Cobertura          | Ámbito PEBDICP; el servicio contratado menciona zonas críticas de la cuenca del Putumayo. El diseño debe poder soportar Putumayo, Amazonas, Napo y Yavarí aunque el despliegue inicial sea parametrizable.      |
| Fuentes base       | Servicio UGRF listado en inventario; INVESTIGACION_DE_LOS_1-12_PENDIENTES(1).md; Consolidado AS-IS UGRF                                                                                                         |

## **Actores/usuarios**

- Administrador UGRF

- Monitorista

- Validador

- Coordinador/revisor

- Brigada/técnico de campo

- Usuario de consulta

- Administrador técnico

## **Entidades y datos que la IA debe localizar**

fuente de datos, foco_calor, alerta, incidente, estado_fuente,
estado_interno, fecha/hora, latitud/longitud, peligro, sensor,
cobertura, cuenca/distrito/comunidad, responsable, atención, evidencia,
motivo_descarte, historial.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                                                   | **Nivel** |
|--------|---------------------------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Ingerir automáticamente focos/alertas desde fuentes oficiales; SERFOR es la fuente primaria del diseño.                         | B         |
| RF-02  | Separar foco de calor, alerta e incidente confirmado. Un foco no puede convertirse automáticamente en incendio confirmado.      | B         |
| RF-03  | Filtrar/intersectar espacialmente eventos con el ámbito PEBDICP.                                                                | B         |
| RF-04  | Visualizar eventos georreferenciados en mapa y permitir filtros temporales/territoriales.                                       | B         |
| RF-05  | Aplicar workflow equivalente: NUEVA → VALIDADA → ASIGNADA → EN_ATENCION → CONTROLADA → CERRADA; rama DESCARTADA.                | B/D       |
| RF-06  | Registrar responsable, brigada, acciones, tiempos y evidencias de atención.                                                     | B         |
| RF-07  | Conservar motivo, usuario, fecha y evidencia de descarte.                                                                       | B         |
| RF-08  | Mantener estado de la fuente separado del estado interno PEBDICP.                                                               | B         |
| RF-09  | Mantener historial y evitar eliminación física de incidentes/evidencias.                                                        | B/C       |
| RF-10  | Integrar/enriquecer con datos meteorológicos y de riesgo cuando estén habilitados (SENAMHI/CENEPRED; NASA FIRMS como respaldo). | B         |
| RF-11  | Contar con motor de reglas configurable para prioridad/alerta; valores definitivos deben aprobarse institucionalmente.          | B/D       |
| RF-12  | Registrar evidencias versionadas: foto, video, PDF, acta, reporte, GPS o archivo geográfico.                                    | B         |

## **Flujo funcional esperado**

> **→** Conector consulta fuente oficial
>
> **→** Normaliza evento
>
> **→** Intersección espacial con ámbito
>
> **→** Registra foco
>
> **→** Genera/actualiza alerta si corresponde
>
> **→** Monitorista revisa
>
> **→** Validador confirma o descarta
>
> **→** Se asigna responsable
>
> **→** Brigada atiende y sube evidencias
>
> **→** Se marca controlado
>
> **→** Validador/admin cierra
>
> **→** Sistema conserva historial/reportes

## **Salidas/resultados esperados**

- Mapa de eventos

- Bandeja de alertas

- Ficha de incidente

- Historial de estados

- Evidencias

- Tiempos/SLA parametrizables

- Reportes por periodo/territorio/estado

- Indicadores de atención

## **Integraciones/dependencias**

- SERFOR REST/GeoJSON/WMS/WFS

- PostgreSQL/PostGIS o capacidad espacial equivalente

- SENAMHI

- CENEPRED

- NASA FIRMS como respaldo

- Capas territoriales PEBDICP/INEI/SERFOR/SERNANP según diseño

## **Reglas de negocio y control**

- No confundir foco satelital con incendio confirmado.

- No mapear ciegamente estados externos a estados internos.

- No borrar evidencia anterior al subir una nueva versión.

- Roles/responsables, SLA, umbrales y evidencia mínima de cierre son
  decisiones parametrizables que requieren aprobación institucional.

## **Pruebas mínimas que debe ejecutar la IA**

- Importar evento SERFOR

- Evento fuera de ámbito no genera incidencia operativa

- Validar alerta

- Descartar con motivo/evidencia

- Asignar técnico

- Subir evidencia GPS/foto

- Pasar a controlada/cerrada

- Comprobar historial

- Falla de SERFOR y manejo de error/reintento

- Duplicado del mismo evento

## **Señales de posible incumplimiento**

- Mapa con puntos seed sin ingestión real

- Foco se guarda como incendio confirmado automáticamente

- No existe workflow

- Todos pueden cerrar/descartar

- Sin evidencia ni historial

- API externa declarada pero nunca consumida

- Eventos duplicados por polling

- Coordenadas sin validación

# **4.8 UGRF-02 — Sistema de Auditoría de Archivos Compartidos y Panel de Control de Actividades de Usuarios**

| **Campo**          | **Definición**                                                                                                                             |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UGRF                                                                                                                                       |
| Nivel de evidencia | A · título del servicio confirmado; C · detalle funcional mínimo derivado del objetivo del título y trazabilidad institucional             |
| Objetivo           | Proporcionar control, trazabilidad y revisión de archivos compartidos y de las actividades realizadas por usuarios en la red/entorno UGRF. |
| Cobertura          | Archivos y actividades de usuarios vinculados al entorno compartido de UGRF definido por la institución.                                   |
| Fuentes base       | Proyectos_Persona_Natural_Ordenado.xlsx; Portal UGRF: Gestión Forestal Integral; Flujo institucional de trazabilidad documental            |

| **Advertencia de evidencia:** No se localizó en el material consolidado un TDR completo con campos exactos. La IA debe diferenciar requisito mínimo técnicamente necesario de obligación contractual literal. |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

## **Actores/usuarios**

- Administrador UGRF/seguridad

- Informática

- Jefatura/revisor autorizado

- Usuario auditado

- Usuario de consulta restringida

## **Entidades y datos que la IA debe localizar**

usuario, equipo/origen cuando esté disponible, fecha/hora, acción,
archivo/ruta, tipo de evento, resultado, tamaño/hash opcional, origen/IP
opcional, detalle, nivel/riesgo, evento de auditoría.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                                                              | **Nivel** |
|--------|--------------------------------------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Registrar eventos de actividad de usuario relacionados con archivos compartidos.                                                           | A/C       |
| RF-02  | Identificar como mínimo quién, qué acción, sobre qué recurso y cuándo ocurrió.                                                             | C         |
| RF-03  | Permitir consulta, búsqueda y filtros por usuario, fecha, acción y archivo/ruta.                                                           | C         |
| RF-04  | Mostrar panel de control con actividad agregada e indicadores.                                                                             | A/C       |
| RF-05  | Conservar historial de auditoría y protegerlo frente a modificación ordinaria por usuarios auditados.                                      | C         |
| RF-06  | Permitir exportar/generar reportes de auditoría para revisión institucional.                                                               | C         |
| RF-07  | Distinguir acciones exitosas/fallidas y, cuando la fuente lo permita, creación, modificación, eliminación, renombrado/movimiento y acceso. | C         |
| RF-08  | Aplicar RBAC: solo roles autorizados pueden consultar información sensible de auditoría.                                                   | B/C       |

## **Flujo funcional esperado**

> **→** Agente/servicio/fuente detecta evento
>
> **→** Normaliza usuario/archivo/acción/fecha
>
> **→** Guarda evento
>
> **→** Dashboard agrega indicadores
>
> **→** Revisor filtra/investiga
>
> **→** Genera reporte/exportación
>
> **→** Se conserva trazabilidad

## **Salidas/resultados esperados**

- Registro de eventos

- Dashboard de actividad

- Filtros/búsqueda

- Reporte por usuario/archivo/periodo

- Detalle cronológico

## **Integraciones/dependencias**

- Directorio/identidad de usuarios si existe

- Fuente de eventos de archivos compartidos

- Administración de usuarios/roles UGRF

## **Reglas de negocio y control**

- El usuario auditado no debe poder borrar su propia evidencia de
  auditoría.

- Los timestamps deben ser consistentes y auditables.

- Si la fuente no permite detectar una acción específica, el sistema
  debe declararlo en vez de simularla.

## **Pruebas mínimas que debe ejecutar la IA**

- Crear/modificar archivo y verificar evento

- Renombrar/mover y verificar evento

- Filtrar por usuario

- Filtrar por rango de fecha

- Usuario sin permisos intenta ver auditoría

- Exportar reporte

- Reinicio del servicio sin perder historial

## **Señales de posible incumplimiento**

- Dashboard con eventos seed

- No existe captura real de eventos

- Eventos sin usuario o timestamp

- Cualquier usuario puede borrar logs

- No hay filtros

- Métricas estáticas

- Auditoría se limita al login de la aplicación y no a archivos
  compartidos

# **4.9 UGRF-03 — Gestión del Conocimiento / Repositorio Técnico e Institucional**

| **Campo**          | **Definición**                                                                                                                                 |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UGRF                                                                                                                                           |
| Nivel de evidencia | A · módulo visible en Portal UGRF; D · TDR detallado no localizado en el material consolidado                                                  |
| Objetivo           | Organizar y facilitar la consulta de conocimiento técnico y documentación institucional de UGRF, evitando dispersión y pérdida de información. |
| Cobertura          | Documentación técnica/institucional autorizada para UGRF.                                                                                      |
| Fuentes base       | Portal UGRF: Gestión Forestal Integral; Consolidado AS-IS UGRF                                                                                 |

| **Advertencia de evidencia:** Este es el sistema con menor respaldo contractual localizado. Su nombre y propósito general sí están confirmados por el portal construido; los detalles deben contrastarse con TDR/orden/acta si se dispone de ellos. |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

## **Actores/usuarios**

- Administrador de conocimiento

- Jefatura/coord./supervisor

- Técnicos/especialistas

- Usuario de consulta

## **Entidades y datos que la IA debe localizar**

documento/contenido, título, tipo/categoría, tema, proyecto/CUI
opcional, autor/responsable, fecha, versión, estado, etiqueta, archivo,
metadatos, permiso, historial.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                             | **Nivel** |
|--------|---------------------------------------------------------------------------|-----------|
| RF-01  | Permitir registrar/publicar documentos o contenidos técnicos.             | A/C       |
| RF-02  | Clasificar por categorías, temas, proyectos o metadatos equivalentes.     | C         |
| RF-03  | Disponer de búsqueda y filtros que permitan localizar conocimiento.       | C         |
| RF-04  | Gestionar permisos de consulta/administración.                            | B/C       |
| RF-05  | Conservar versiones o historial cuando un documento se actualiza.         | C         |
| RF-06  | Permitir visualizar/descargar el archivo y sus metadatos.                 | C         |
| RF-07  | Evitar duplicación descontrolada mediante identificadores/versionado.     | C         |
| RF-08  | Permitir relacionar documentos con procesos/proyectos cuando corresponda. | B/C       |

## **Flujo funcional esperado**

> **→** Usuario autorizado carga contenido
>
> **→** Completa metadatos/categoría
>
> **→** Administrador revisa/publica si aplica
>
> **→** Contenido queda indexado
>
> **→** Usuario busca/filtra
>
> **→** Consulta/descarga
>
> **→** Nueva versión conserva historial

## **Salidas/resultados esperados**

- Repositorio

- Ficha de documento

- Búsqueda

- Categorías/etiquetas

- Historial/versiones

- Estadísticas básicas de contenido/consulta

## **Integraciones/dependencias**

- Gestión documental/SISGED como posible fuente o referencia;
  integración específica NO confirmada

- Proyectos/CUI para contextualizar conocimiento

- Usuarios/roles UGRF

## **Reglas de negocio y control**

- No presentar un simple explorador de archivos como gestión del
  conocimiento si no existe clasificación/búsqueda/metadatos.

- No asumir integración con SISGED sin evidencia técnica.

- La eliminación de una versión publicada debe estar restringida y
  trazada.

## **Pruebas mínimas que debe ejecutar la IA**

- Subir documento

- Buscar por término

- Filtrar por categoría/proyecto

- Actualizar versión

- Usuario sin permiso intenta editar

- Descargar documento correcto

- Detectar duplicado/versionar

## **Señales de posible incumplimiento**

- Carpeta estática sin buscador

- Documentos sin metadatos

- Sobrescritura que pierde versión anterior

- Todos editan/eliminan

- Enlaces rotos

- Contenido seed sin documentos reales
