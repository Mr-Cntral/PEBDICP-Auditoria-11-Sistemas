# **3. Inventario de los 11 sistemas**

| **ID**  | **Unidad** | **Sistema**                                                                                               | **Base de evidencia**                                                                                                          |
|---------|------------|-----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| UDA-01  | UDA        | Asistente Virtual Inteligente con Procesamiento de Lenguaje Natural                                       | A · TDR directo (INFORME_2026-0002_UDA) + presentación UDA                                                                     |
| UDA-02  | UDA        | Sistema Predictivo y Analítico para Estimación de Rendimientos de Aguaje y Camu Camu                      | A · TDR directo (INFORME_2026-0003_UDA) + presentación UDA                                                                     |
| UDA-03  | UDA        | Registro y Control de Asistencia Técnica a Productores con Georreferenciación                             | A · TDR directo (INFORME_2026-0013_UDA) + AS-IS de campo + presentación UDA                                                    |
| UDA-04  | UDA        | Gestión de Incidencias y Seguimiento de Plagas para Cacao y Camu Camu                                     | A · TDR directo (INFORME_2026-0014_UDA) + presentación UDA                                                                     |
| UDA-05  | UDA        | Módulo de Comercio Electrónico y Vitrina Digital para Productos Amazónicos                                | A · TDR directo (INFORME_2026-0016_UDA) + presentación UDA                                                                     |
| UDA-06  | UDA        | Plataforma de Seguimiento de Proyectos, Indicadores y Metas                                               | A · Presentación UDA para la aplicación; B · AS-IS institucional para alcance ampliado                                         |
| UGRF-01 | UGRF       | Sistema Inteligente de Alerta Temprana y Monitoreo de Incendios Forestales                                | A · nombre/servicio confirmado; B/C · diseño técnico detallado consolidado el 04/09/2026                                       |
| UGRF-02 | UGRF       | Sistema de Auditoría de Archivos Compartidos y Panel de Control de Actividades de Usuarios                | A · título del servicio confirmado; C · detalle funcional mínimo derivado del objetivo del título y trazabilidad institucional |
| UGRF-03 | UGRF       | Gestión del Conocimiento / Repositorio Técnico e Institucional                                            | A · módulo visible en Portal UGRF; D · TDR detallado no localizado en el material consolidado                                  |
| UGRF-04 | UGRF       | Plataforma Tecnológica de Monitoreo Ambiental Integrada con Datos Satelitales y Climáticos                | A · título del servicio confirmado; C · detalle funcional derivado del objeto técnico                                          |
| UGRF-05 | UGRF       | Aplicación Móvil Inteligente para Recojo de Datos Georreferenciados, Incidencias y Fiscalización en Campo | A · título del servicio confirmado; B · flujo de campo institucional; C · detalle técnico mínimo                               |

| **Importante:** los informes UDA cargados contienen también consultorías que no son aplicaciones. Los 6 sistemas UDA son las aplicaciones operativas enumeradas en la presentación UDA; las consultorías se incluyen después como condicionantes y fuentes de requerimientos, no como “sistemas faltantes”. |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

# **4. Especificación auditable por sistema**

# **4.1 UDA-01 — Asistente Virtual Inteligente con Procesamiento de Lenguaje Natural**

| **Campo**          | **Definición**                                                                                                                                                                            |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UDA                                                                                                                                                                                       |
| Nivel de evidencia | A · TDR directo (INFORME_2026-0002_UDA) + presentación UDA                                                                                                                                |
| Objetivo           | Fortalecer la atención de consultas técnicas de productores agropecuarios mediante un asistente virtual inteligente, mejorando oportunidad, cobertura y calidad de la asistencia técnica. |
| Cobertura          | Consultas técnicas de productores agropecuarios dentro del ámbito de intervención de UDA.                                                                                                 |
| Fuentes base       | INFORME_2026-0002_UDA.docx; Presentacion_Indice_Proyectos_UDA-1.pdf                                                                                                                       |

## **Actores/usuarios**

- Productor/usuario consultante

- Técnico UDA

- Administrador de base de conocimiento

- Informática/administrador técnico

## **Entidades y datos que la IA debe localizar**

base_conocimiento, categoría/tema, documento o fuente técnica, consulta,
respuesta, fecha/hora, usuario/canal, retroalimentación, métrica de
desempeño.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                              | **Nivel** |
|--------|------------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Levantar y representar consultas técnicas recurrentes, casos de uso y canales de atención.                 | A         |
| RF-02  | Contar con flujo conversacional y base de conocimiento técnico gestionable.                                | A         |
| RF-03  | Procesar preguntas en lenguaje natural y devolver respuestas técnicas coherentes.                          | A         |
| RF-04  | Configurar/entrenar el componente de PLN y demostrar que está conectado al flujo real.                     | A         |
| RF-05  | Integrarse con los canales de atención que hayan sido definidos en el proyecto.                            | A         |
| RF-06  | Registrar consultas y disponer de indicadores de desempeño.                                                | A         |
| RF-07  | Permitir administración/actualización de la base de conocimiento sin alterar manualmente cada respuesta.   | C         |
| RF-08  | Manejar preguntas no conocidas evitando inventar respuestas y derivando o declarando falta de información. | C         |
| RF-09  | Mantener trazabilidad de versiones/fuentes del conocimiento cuando sea posible.                            | B/C       |

## **Flujo funcional esperado**

> **→** Usuario formula consulta
>
> **→** Sistema interpreta intención/tema
>
> **→** Busca contexto en base de conocimiento
>
> **→** Genera/selecciona respuesta
>
> **→** Registra consulta/resultado
>
> **→** Usuario recibe respuesta y opcionalmente califica
>
> **→** Administrador revisa métricas y mejora conocimiento

## **Salidas/resultados esperados**

- Respuesta técnica al usuario

- Historial de consultas

- Base de conocimiento

- Indicadores de uso/desempeño

- Manual de usuario y documentación técnica

## **Integraciones/dependencias**

- Base de conocimiento institucional

- Canales definidos por UDA

- Autenticación/roles institucionales si el canal es interno

## **Reglas de negocio y control**

- No aceptar respuestas desconectadas de la base de conocimiento como
  evidencia de cumplimiento.

- Las métricas deben provenir de consultas reales/persistidas.

- No inventar respuesta cuando no exista conocimiento suficiente.

## **Pruebas mínimas que debe ejecutar la IA**

- Consulta conocida y respuesta correcta

- Consulta con sinónimos o redacción distinta

- Pregunta fuera del dominio

- Actualización de conocimiento y nueva respuesta

- Registro de consulta en historial

- Métrica incrementa de forma consistente

- Usuario no administrador intenta editar conocimiento

## **Señales de posible incumplimiento**

- Chat decorativo sin backend de PLN

- Respuestas fijas/hardcodeadas para pocas preguntas

- Base de conocimiento vacía o no editable

- No existe registro de consultas

- Indicadores son números estáticos

- El modelo responde cualquier cosa sin control de dominio

# **4.2 UDA-02 — Sistema Predictivo y Analítico para Estimación de Rendimientos de Aguaje y Camu Camu**

| **Campo**          | **Definición**                                                                                                                                                         |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Unidad             | UDA                                                                                                                                                                    |
| Nivel de evidencia | A · TDR directo (INFORME_2026-0003_UDA) + presentación UDA                                                                                                             |
| Objetivo           | Estimar rendimientos de cultivos amazónicos de aguaje y camu camu usando información agronómica, climática y productiva, con modelos analíticos/predictivos validados. |
| Cobertura          | Aguaje y camu camu en el ámbito de intervención UDA, región Loreto.                                                                                                    |
| Fuentes base       | INFORME_2026-0003_UDA.docx; Presentacion_Indice_Proyectos_UDA-1.pdf; INFORME_2026-0011_UDA.docx (gobernanza de datos)                                                  |

## **Actores/usuarios**

- Técnico/especialista UDA

- Analista/administrador

- Coordinador de proyecto

- Usuario de consulta/decisión

## **Entidades y datos que la IA debe localizar**

cultivo, parcela/predio, campaña/periodo, producción histórica,
rendimiento, variables agronómicas, variables climáticas,
cosecha/acopio, modelo, versión modelo, predicción, métrica de
validación, reporte.

## **Requisitos funcionales auditables**

| **ID** | **Requisito**                                                                                           | **Nivel** |
|--------|---------------------------------------------------------------------------------------------------------|-----------|
| RF-01  | Levantar y sistematizar información agronómica, climática y productiva.                                 | A         |
| RF-02  | Relacionar datos con procesos de registro, cosecha, acopio y comercialización que afecten rendimientos. | A         |
| RF-03  | Diseñar y ejecutar modelos analíticos y predictivos de rendimiento.                                     | A         |
| RF-04  | Permitir generar una estimación de rendimiento por cultivo/ámbito/periodo según los datos disponibles.  | A/C       |
| RF-05  | Validar el modelo y conservar métricas o evidencia de desempeño.                                        | A         |
| RF-06  | Generar reportes y tableros de control de resultados.                                                   | A         |
| RF-07  | Trazar qué datos y versión de modelo produjeron cada predicción.                                        | C         |
| RF-08  | Distinguir datos observados, datos faltantes y predicciones.                                            | C         |
| RF-09  | Impedir que datos seed/demo se confundan con predicciones institucionales reales.                       | B/C       |

## **Flujo funcional esperado**

> **→** Carga/ingesta de histórico
>
> **→** Validación/limpieza de variables
>
> **→** Selección de cultivo/parcela/periodo
>
> **→** Ejecución del modelo
>
> **→** Obtención de predicción
>
> **→** Registro de resultado y métricas
>
> **→** Visualización/reporte
>
> **→** Retroalimentación con valores observados futuros

## **Salidas/resultados esperados**

- Predicción de rendimiento

- Dashboard analítico

- Reporte de variables/resultados

- Métricas del modelo

- Historial de predicciones

- Manual y documentación técnica

## **Integraciones/dependencias**

- Datos maestros de productores/parcelas/cultivos

- Fuentes climáticas o archivos UDA

- Gestión de datos/ciencia de datos como marco de gobernanza

## **Reglas de negocio y control**

- Una predicción debe ser reproducible con entradas y versión de modelo
  identificables.

- Si no hay datos suficientes, el sistema debe informar limitación en
  lugar de producir certeza falsa.

- Las métricas del modelo deben ser calculadas, no textos decorativos.

## **Pruebas mínimas que debe ejecutar la IA**

- Predicción con datos válidos

- Mismo input reproduce resultado/modelo versionado

- Cultivo no soportado

- Datos incompletos

- Cambio de periodo

- Validación de métricas

- Comparación predicho vs observado

- Dashboard se actualiza al incorporar nuevos datos

## **Señales de posible incumplimiento**

- “Predicción” basada en random()

- Fórmula fija no documentada

- No existe dataset/histórico

- No hay métricas

- Dashboard con valores hardcodeados

- No distingue aguaje de camu camu

- Modelo no puede ejecutarse desde backend
