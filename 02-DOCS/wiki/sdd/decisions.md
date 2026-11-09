---
type: decision
title: Ratificación inicial de la constitución SDD
description: Registro de la aprobación humana de los principios iniciales de chess-software.
tags: [sdd, architecture, process]
timestamp: 2026-11-09T13:28:03Z
topic: sdd
status: stable
sources: []
score: 0.0
---

# Ratificación inicial de la constitución SDD

## Contexto

El proyecto académico parte de un repositorio sin código. Se necesitaba fijar principios de trabajo a partir de las decisiones expresamente aprobadas, sin inventar el contenido del enunciado ni cerrar elecciones técnicas pendientes.

## Decisión

Ratificar la [constitución SDD](./constitution.md) v1.0.0 con alcance funcional conocido, stack y arquitectura aprobados, desarrollo incremental, pruebas, control de acceso a partidas propias, ramas y Pull Requests, documentación proporcional y aprobación humana de cambios importantes.

La autenticación mediante nombre de usuario y contraseña queda aprobada. Las técnicas de sesión, cookies y almacenamiento seguro de contraseñas permanecen pendientes, junto con las demás decisiones enumeradas en la constitución.

## Alternativas consideradas

- Mantener solo las decisiones confirmadas y aplazar las no especificadas: elegida.
- Elegir ahora versiones, frameworks, bibliotecas y herramientas de calidad: descartada porque esas decisiones no han sido aprobadas y pueden depender del enunciado oficial.

## Motivo y seguimiento

La decisión preserva el alcance aprobado y deja explícita la incertidumbre. El siguiente paso acordado es incorporar el enunciado oficial de IS2 y preparar la primera especificación, sin implementar funcionalidades todavía.
