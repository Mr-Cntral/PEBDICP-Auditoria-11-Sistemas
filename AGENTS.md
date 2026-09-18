# AGENTS.md — PEBDICP Auditoría de 11 Sistemas

## Instrucción prioritaria para Codex

Antes de analizar, editar o generar código, lee completamente:

1. `docs/auditoria/00_LEER_PRIMERO.md`
2. Todos los demás archivos `.md` de `docs/auditoria/` en el orden indicado por el índice.

Este repositorio funciona como **fuente maestra de requisitos y criterios de auditoría** para 11 sistemas PEBDICP: 6 UDA y 5 UGRF.

## Reglas de trabajo

- No modificar código ni documentación durante la primera etapa.
- Primero generar un diagnóstico de comprensión de los 11 sistemas.
- Diferenciar: Confirmado, Confirmado por flujo institucional, Inferencia técnica y Pendiente.
- No inventar requisitos.
- No declarar CUMPLE por la sola existencia de UI o CRUD.
- Para futuras auditorías de código, citar archivo, función, endpoint, tabla, prueba o evidencia.
- Estados permitidos de auditoría: CUMPLE, CUMPLE PARCIALMENTE, NO CUMPLE, NO IMPLEMENTADO y NO VERIFICABLE.
- Cuando la documentación indique una decisión institucional pendiente, conservarla como pendiente y no fijar valores arbitrarios.

## Primera respuesta esperada

Al terminar la lectura, resume para cada sistema:
objetivo, flujo principal, actores, datos, reglas, integraciones, funciones críticas, requisitos confirmados, inferencias y aspectos no verificables.

No hagas cambios hasta recibir una instrucción posterior.