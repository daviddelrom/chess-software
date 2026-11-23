---
type: article
title: Catálogo inicial de casos de uso
description: Inventario de casos de uso funcionales y su relación con los requisitos IS2.
tags: [sdd, use-cases, requirements]
timestamp: 2026-11-23T09:16:51Z
topic: sdd
status: draft
sources:
  - constitution.md
  - requirements-traceability.md
score: 0.0
---

# Catálogo inicial de casos de uso

Los casos de esta lista son un inventario de trabajo. Solo registro e inicio de sesión tendrán una especificación detallada en este incremento. Los demás no deben interpretarse como implementaciones ya aprobadas.

## Casos detallados en esta fase

| Caso | Propósito | Requisitos IS2 relacionados | Estado |
|---|---|---|---|
| CU-01 Registrar usuario | Crear una identidad con nombre de usuario y contraseña. | `IS2-F-10`; `IS2-F-08`; `IS2-A-02`; `IS2-A-08`; `IS2-V-05` | Especificación detallada propuesta; pendiente de aprobación |
| CU-02 Iniciar sesión | Validar credenciales y establecer una sesión autenticada según el mecanismo aprobado. | `IS2-F-10`; `IS2-F-08`; `IS2-A-02`; `IS2-A-08`; `IS2-A-09`; `IS2-A-10` | Especificación detallada propuesta; pendiente de aprobación |

La especificación de ambos casos está en [Especificación de registro e inicio de sesión](specifications/authentication.md).

## Inventario pendiente de especificación detallada

| Caso | Propósito | Requisitos IS2 relacionados | Estado |
|---|---|---|---|
| CU-03 Crear sala | Crear un contexto para compartir una partida. | `IS2-F-02`; `IS2-F-06`; `IS2-A-01`; `IS2-V-02` | Inventariado; alcance y ciclo de vida pendientes |
| CU-04 Unirse a una sala | Permitir que un segundo participante acceda a una sala. | `IS2-F-02`; `IS2-F-06`; `IS2-A-01`; `IS2-V-02`; `IS2-V-03` | Inventariado; mecanismo de unión y acceso pendientes |
| CU-05 Crear o iniciar partida | Asociar participantes, estado inicial y primer registro de movimientos. | `IS2-F-05`; `IS2-F-10`; `IS2-A-06`; `IS2-A-07` | Inventariado; creación y estado pendientes |
| CU-06 Realizar movimientos | Registrar una acción de juego y reflejar el estado según las reglas seleccionadas. | `IS2-F-02`; `IS2-F-08`; `IS2-A-11`; `IS2-V-05` | Inventariado; reglas completas y representación pendientes |
| CU-07 Consultar partida o histórico | Obtener estado o movimientos de una partida propia y autorizada. | `IS2-F-07`; `IS2-F-10`; `IS2-V-04`; `IS2-E-03` | Inventariado; contrato y alcance pendientes |
| CU-08 Reproducir partida propia | Recorrer posiciones o movimientos anteriores de una partida propia. | `IS2-F-11`; `IS2-E-04`; `IS2-E-03` | Inventariado como aportación propia; interacción concreta pendiente |
| CU-09 Gestionar desconexión o error | Registrar y comunicar situaciones de usuario desconectado, datos incompletos o operación inválida. | `IS2-F-08`; `IS2-V-05`; `IS2-A-08` | Inventariado; categorías y respuestas pendientes |

## Dependencias conceptuales

- `CU-01` y `CU-02` requieren una identidad de usuario y una decisión sobre autenticación persistente.
- `CU-03` y `CU-04` dependen del modelo aprobado de sala y del mecanismo de contacto entre usuarios.
- `CU-05` y `CU-06` dependen del modelo de partida y de la política de reglas de movimiento.
- `CU-07` y `CU-08` dependen de persistencia y de autorización por participante.
- `CU-09` se aplica a todos los casos y requiere criterios de error definidos por cada especificación.

## Verificación futura

El catálogo no sustituye criterios de aceptación ni pruebas. En incrementos posteriores, cada caso aprobado deberá enlazar su especificación y evidencia:

- pruebas unitarias de reglas y casos de uso;
- pruebas de integración de adaptadores pertinentes;
- comprobaciones funcionales para flujos visibles;
- pruebas de acceso permitido y denegado.

Las herramientas y formatos concretos siguen pendientes según la constitución.
