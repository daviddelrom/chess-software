---
type: article
title: Roadmap del proyecto
description: Hitos de seguimiento incremental de la preparación, especificación, implementación y verificación de chess-software.
tags: [roadmap, sdd, project-management]
timestamp: 2026-11-23T09:04:59Z
topic: project
status: draft
sources:
  - sdd/constitution.md
  - sdd/requirements-traceability.md
score: 0.0
---

# Roadmap del proyecto

Este roadmap permite seguir el progreso de `chess-software` desde su preparación hasta la entrega. Es orientativo: los hitos pueden ajustarse por aprendizaje técnico, revisión de requisitos o decisiones aprobadas antes de avanzar.

La constitución SDD y la matriz de trazabilidad siguen siendo la referencia para requisitos, criterios de aceptación y decisiones pendientes. La especificación, la implementación y las pruebas se harán por incrementos. Las pruebas se diseñarán y ejecutarán junto con cada incremento aplicable; no se reservarán todas para la fase final.

No se consideran completadas ninguna especificación, tecnología, implementación o prueba que aún no tenga una decisión o evidencia aprobada.

## Hitos

| Hito | Objetivo | Estado | Resultado demostrable | Referencias |
|---|---|---|---|---|
| 1. Preparación del repositorio | Establecer documentación inicial, configuración del repositorio y flujo SDD básico. | Completado | Repositorio preparado con constitución, índice documental, configuración versionada y rama principal integrada. | `main`; [Constitución SDD](sdd/constitution.md) |
| 2. Análisis de requisitos y trazabilidad | Incorporar el enunciado oficial y transformar sus requisitos en identificadores, criterios de aceptación y ambigüedades visibles. | Completado — PR #1 integrado | El PDF oficial y una matriz de 44 identificadores están disponibles en `main`; el índice enlaza la matriz y las categorías distinguen requisitos oficiales de decisiones aprobadas. | [PR #1](https://github.com/daviddelrom/chess-software/pull/1); [Matriz de trazabilidad IS2](sdd/requirements-traceability.md) |
| 3. Especificación y diseño inicial | Delimitar los primeros comportamientos y elementos de diseño mediante especificaciones aprobadas antes de implementarlos. | En curso — borradores pendientes de aprobación | Modelo conceptual, catálogo de casos de uso, esquema hexagonal mínimo y especificación detallada de registro e inicio de sesión preparados para revisión; no se consideran aprobados ni implementados. | [Constitución SDD](sdd/constitution.md); [Matriz de trazabilidad IS2](sdd/requirements-traceability.md); [modelo](sdd/domain-model.md); [casos de uso](sdd/use-cases.md); [arquitectura](sdd/architecture-overview.md); [autenticación](sdd/specifications/authentication.md) |
| 4. Base técnica ejecutable | Preparar la estructura mínima que permita ejecutar y verificar los componentes acordados. | Pendiente | El repositorio contendrá una base ejecutable desde una instalación limpia y documentada, con la separación mínima necesaria para desarrollar incrementos posteriores. | Especificaciones y pruebas de este hito aún pendientes |
| 5. Usuarios y autenticación | Incorporar registro, inicio de sesión y autorización conforme a las especificaciones aprobadas. | Pendiente | Una persona podrá registrar e iniciar sesión con usuario y contraseña, y el sistema denegará el acceso no autorizado a partidas según el acceso definido. | Constitución SDD, requisitos IS2 y especificación propia pendientes de aprobación |
| 6. Salas y conexión de dos jugadores | Implementar la creación y unión a salas para conectar a dos participantes. | Pendiente | Una sala podrá crearla un usuario y puede demostrarse la unión de dos jugadores mediante el flujo documentado, incluidos los errores aplicables. | Especificaciones y pruebas de salas pendientes |
| 7. Tablero, movimientos y comunicación | Presentar el tablero y completar el flujo incremental de movimientos y comunicación. | Pendiente | El frontend mostrará el tablero y la interacción definida podrá comunicarse con el backend; movimientos válidos e inválidos tendrán el resultado esperado y documentado. | Especificación de reglas y contrato de comunicación pendientes |
| 8. Persistencia e histórico de partidas | Registrar y recuperar partidas y movimientos con autorización entre participantes. | Pendiente | Podrán consultarse partidas y movimientos registrados por sus participantes, y el comportamiento tras reiniciar el backend podrá verificarse según la persistencia aprobada. | [Matriz de trazabilidad IS2](sdd/requirements-traceability.md), sección de persistencia y ambigüedades |
| 9. Reproductor de partidas propias, verificación y entrega final | Completar la aportación propia, consolidar la trazabilidad y preparar la entrega reproducible. | Pendiente | El reproductor permitirá recorrer posiciones o movimientos propios con la interacción aprobada; las pruebas aplicables, capturas, README y comprobación desde instalación limpia estarán disponibles. | README y evidencias finales pendientes |

## Principios de seguimiento

- No se incluye una estimación temporal porque no está aprobada y podría imponer compromisos prematuros.
- Un hito cambia de estado únicamente cuando existen cambios revisados, criterios aceptados y evidencia demostrable.
- Los detalles técnicos pendientes no se resuelven en este roadmap; se someterán a especificación y aprobación antes de implementarlos.
- Las pruebas unitarias, de integración y funcionales pertinentes acompañarán a los incrementos que las requieran. Antes de integrar cada cambio se comprobará la matriz y la documentación afectada.
