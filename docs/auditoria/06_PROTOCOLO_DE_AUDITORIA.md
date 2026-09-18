# **6. Matriz transversal de datos e integración**

| **Sistema** | **Proyecto/CUI** | **Productor/benef.** | **Parcela/GPS** | **Evidencia** | **Workflow/estado** | **Reporte/KPI** | **Integración externa** |
|-------------|------------------|----------------------|-----------------|---------------|---------------------|-----------------|-------------------------|
| UDA-01      | ●                | ○                    | ○               | ●             | ●                   | ●               | Canal/KB                |
| UDA-02      | ●                | ●                    | ○               | ○             | ●                   | ●               | Clima/datos             |
| UDA-03      | ●                | ●                    | ●               | ●             | ●                   | ●               | GIS                     |
| UDA-04      | ●                | ●                    | ●               | ●             | ●                   | ●               | Asistencia/GIS          |
| UDA-05      | ●                | ○                    | ●               | ●             | ●                   | ●               | Pagos                   |
| UDA-06      | ○                | ○                    | ●               | ●             | ●                   | ●               | F12/SISGED pendiente    |
| UGRF-01     | ○                | ●                    | ●               | ●             | ●                   | ●               | SERFOR/SENAMHI/etc.     |
| UGRF-02     | ○                | ○                    | ●               | ●             | ●                   | ●               | Fuente logs             |
| UGRF-03     | ○                | ○                    | ●               | ●             | ●                   | ●               | SISGED pendiente        |
| UGRF-04     | ○                | ●                    | ●               | ●             | ●                   | ●               | APIs sat./clima         |
| UGRF-05     | ○                | ●                    | ●               | ●             | ●                   | ●               | GIS/backend             |

*Leyenda: ● = componente relevante/esperado; ○ = puede existir como
referencia o no aplica de forma central. La tabla es una guía de
integración, no una sustitución del TDR.*

## **6.1 Documentos y trazabilidad institucional que deben considerarse**

- Expediente técnico/estudio definitivo y sus modificaciones.

- Términos de Referencia, especificaciones, requerimientos y pedidos.

- Órdenes de servicio/compra y contratos cuando el proceso lo requiere.

- Informes técnicos del proyecto, informes de supervisión e informes
  UDA/UGRF.

- Oficios, cartas, observaciones, devoluciones y subsanaciones.

- Resoluciones Directorales en decisiones que se formalizan por esa vía.

- Formato 12-B / seguimiento de inversiones: la relación con el “F12”
  interno es una hipótesis muy fuerte que debe confirmarse para el flujo
  específico.

- Informe final y liquidación físico-financiera en cierre de proyectos.

## **6.2 Requisitos no funcionales transversales**

| **Dimensión**         | **Criterio**                                                                                                                           |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------|
| Seguridad/RBAC        | Autenticación; autorización por rol; no exponer administración a usuarios de consulta.                                                 |
| Trazabilidad          | Usuario, fecha/hora y acción en cambios sensibles; historial en workflows críticos.                                                    |
| Integridad            | Validaciones de claves, coordenadas, fechas, estados y relaciones obligatorias.                                                        |
| Persistencia          | Datos operativos deben sobrevivir reinicios y no depender de estado solo en frontend.                                                  |
| Respaldo              | La documentación UDA recomienda respaldos periódicos; Informática debe definir política real.                                          |
| Interoperabilidad     | Evitar duplicar maestros; usar APIs/servicios o sincronización cuando se formalice.                                                    |
| Mantenibilidad        | Configuración separada de código para catálogos, umbrales y reglas que cambian.                                                        |
| Observabilidad        | Logs de error e integración suficientes para diagnosticar fallas.                                                                      |
| Responsive/usabilidad | Las aplicaciones UDA presentadas fueron descritas como interfaces responsivas; la app móvil UGRF debe ser usable en dispositivo móvil. |
| Datos demo            | Seeds deben estar identificados y no contaminar reportes operativos.                                                                   |

# **7. Protocolo recomendado para que una IA audite el software**

La IA no debe limitarse a leer el README. Debe reconstruir la evidencia
desde código, base de datos, APIs, interfaz y documentación. El
siguiente procedimiento reduce falsos positivos.

> **→** Inventariar repositorios, carpetas, servicios, puertos,
> tecnologías, variables de entorno y módulos.
>
> **→** Identificar la base de datos: esquemas, tablas, relaciones,
> migraciones, seeds y datos de prueba.
>
> **→** Localizar autenticación y RBAC; construir matriz rol →
> endpoint/pantalla/acción.
>
> **→** Mapear cada requisito RF de este documento a archivos,
> endpoints, tablas, componentes y pruebas.
>
> **→** Levantar el flujo de cada sistema desde evento inicial hasta
> resultado/estado final.
>
> **→** Comprobar que las pantallas consumen backend real y que el
> backend persiste datos.
>
> **→** Ejecutar pruebas felices, negativas y de permisos; conservar
> evidencia de respuesta y cambio en BD.
>
> **→** Revisar integraciones externas y comprobar que los datos no
> provienen de mocks en modo producción.
>
> **→** Validar reportes/KPIs recalculando al menos un caso desde datos
> base.
>
> **→** Revisar historial/auditoría: quién cambió qué y cuándo.
>
> **→** Revisar manejo de errores, reintentos, duplicados e idempotencia
> donde corresponda.
>
> **→** Comparar manual de usuario/documentación técnica contra el
> comportamiento real.
>
> **→** Asignar estado CUMPLE / PARCIAL / NO CUMPLE / NO VERIFICABLE por
> requisito, con evidencia exacta.
>
> **→** Generar una lista priorizada de brechas: crítica, alta, media,
> baja; justificar impacto operativo.

## **7.1 Evidencia mínima que debe citar la IA**

| **Tipo**      | **Ejemplo de evidencia válida**                                              |
|---------------|------------------------------------------------------------------------------|
| Código        | Ruta de archivo + clase/función/componente + líneas o fragmento relevante.   |
| API           | Método + endpoint + payload + respuesta observada.                           |
| Base de datos | Tabla/columna/relación + registro de prueba antes/después.                   |
| UI            | Pantalla/acción + resultado visible; idealmente captura.                     |
| Integración   | Configuración real + llamada externa + respuesta/registro de sincronización. |
| Prueba        | Caso, precondición, pasos, resultado esperado y resultado real.              |
| Documento     | Manual/TDR/informe que respalda el requisito.                                |

## **7.2 Formato de salida esperado de la auditoría**

| **Campo**         | **Contenido**                                                          |
|-------------------|------------------------------------------------------------------------|
| Sistema           | ID y nombre.                                                           |
| Requisito         | RF-XX del sistema.                                                     |
| Estado            | CUMPLE / PARCIAL / NO CUMPLE / NO VERIFICABLE / PENDIENTE.             |
| Evidencia         | Archivo, endpoint, tabla, captura o prueba concreta.                   |
| Hallazgo          | Qué funciona y qué falta.                                              |
| Impacto           | Qué proceso o usuario se afecta.                                       |
| Prioridad         | Crítica / Alta / Media / Baja.                                         |
| Acción correctiva | Cambio concreto sugerido; no reescribir todo el sistema sin necesidad. |

# **8. Prompt listo para usar con una IA auditora**

Actúa como auditor técnico y funcional del proyecto PEBDICP. Toma este
documento como matriz de referencia, no como sustituto del código ni de
la evidencia real. Debes revisar cada uno de los 11 sistemas UDA/UGRF y
verificar requisito por requisito.

Reglas obligatorias:

1\. No inventes funciones, tablas, APIs, roles ni integraciones.

2\. Distingue requisitos A (confirmados), B (flujo institucional), C
(inferencia técnica) y D (pendiente institucional).

3\. Un login, dashboard o CRUD genérico NO demuestra que el objetivo
sustantivo del sistema se cumple.

4\. Busca evidencia en código, base de datos, APIs, UI, pruebas,
configuración y documentación.

5\. Los datos seed/mock deben identificarse. No los aceptes como
evidencia de operación real.

6\. Para cada RF entrega: estado, evidencia exacta, explicación,
impacto, prioridad y acción correctiva.

7\. Ejecuta o describe pruebas funcionales y negativas; verifica
permisos y persistencia.

8\. Para modelos predictivos, comprueba modelo real, dataset/variables,
inferencia reproducible y métricas.

9\. Para georreferenciación, comprueba que GPS/geometría se persiste y
se vincula al registro correcto.

10\. Para integraciones externas, demuestra consumo real o marca NO
VERIFICABLE/NO CUMPLE.

11\. Para workflows, verifica estados, transiciones, historial,
responsables y observaciones.

12\. No marques como incumplimiento contractual un punto C/D sin señalar
que es inferido o pendiente.

Salida obligatoria por sistema:

\- resumen del sistema;

\- arquitectura encontrada;

\- matriz RF → estado → evidencia;

\- pruebas ejecutadas;

\- datos/tablas principales;

\- roles y permisos;

\- integraciones;

\- hallazgos críticos;

\- brechas;

\- conclusión sin puntuación arbitraria: qué está completo, parcial,
faltante o no verificable.

# **9. Paquete documental esperado por sistema en el contexto previo del proyecto**

En el trabajo previo se adoptó como referencia un paquete de siete
documentos por sistema. Esta regla pertenece al contexto del proyecto y
debe verificarse contra el alcance administrativo vigente antes de
tratarla como obligación contractual. Para los 11 sistemas equivaldría a
77 documentos si el estándar se mantiene sin cambios.

- Manual de Usuario.

- Informe de Contenido / alcance funcional.

- Informe Técnico.

- Documento de Requisitos.

- Arquitectura Técnica.

- Diccionario de Datos.

- Manual Técnico de Instalación y Administración.

| **Criterio de auditoría documental:** cada documento debe corresponder al sistema realmente implementado. Un manual genérico copiado entre aplicaciones, tablas inexistentes en el diccionario o arquitectura distinta al código deben marcarse como inconsistencia documental. |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|

# **10. Lista final de comprobación**

| **Área**            | **Pregunta de cierre**                                                                             |
|---------------------|----------------------------------------------------------------------------------------------------|
| Identidad           | ¿El sistema auditado corresponde al nombre/objetivo correcto y no a otro prototipo renombrado?     |
| Objetivo sustantivo | ¿Ejecuta la función principal contratada, más allá del CRUD?                                       |
| Datos               | ¿Las entidades y relaciones necesarias existen y se usan realmente?                                |
| Flujo               | ¿Se puede completar de inicio a fin el proceso principal?                                          |
| Estados             | ¿Existe seguimiento/historial cuando el proceso requiere ciclo de vida?                            |
| Roles               | ¿Los permisos reflejan responsabilidades y separan administración/consulta?                        |
| Evidencia           | ¿Las fotos, documentos, GPS, logs o métricas están vinculados y persistidos?                       |
| Reportes/KPI        | ¿Se calculan con datos reales y son reproducibles?                                                 |
| Integraciones       | ¿Las integraciones declaradas son reales y manejan errores?                                        |
| Trazabilidad        | ¿Se sabe quién hizo qué y cuándo en acciones sensibles?                                            |
| Datos demo          | ¿Los seeds/mocks están claramente separados de producción?                                         |
| Documentación       | ¿Manual, arquitectura, diccionario y requisitos coinciden con el software?                         |
| Operación           | ¿El sistema puede usarse con datos reales sin editar el código?                                    |
| Respaldo/seguridad  | ¿Existen controles técnicos razonables y configuración administrable?                              |
| Brechas             | ¿Las decisiones institucionales aún pendientes están explícitamente parametrizadas o documentadas? |

# **Conclusión de referencia**

La verificación de los 11 sistemas debe centrarse en la capacidad de
cada solución para resolver el proceso real de UDA/UGRF, conservar datos
y evidencias confiables, integrarse con el ecosistema institucional
cuando corresponda y generar resultados útiles para seguimiento y
decisión. La existencia de interfaces visualmente completas no demuestra
por sí sola cumplimiento. La evidencia debe ser trazable desde el
requisito hasta el comportamiento, el dato persistido y el resultado
generado.

Cuando el material disponible no formaliza una regla específica —por
ejemplo responsables exactos, SLA, estados internos definitivos, campos
de una ficha o integración con SISGED— la auditoría debe declararlo como
pendiente de validación institucional y evitar convertir una propuesta
técnica en hecho.