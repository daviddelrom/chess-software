---
type: constitution
title: chess-software — Constitution
description: Reglas aprobadas para el desarrollo verificable de chess-software.
tags: [sdd, constitution]
timestamp: 2026-11-09T13:28:03Z
topic: sdd
version: v1.0.0
---

# chess-software — Constitución

> Versión: v1.0.0 · Ratificada: 2026-11-09 · Última modificación: 2026-11-09
> Estas reglas guían las fases SDD. Las elecciones técnicas aún abiertas se mantienen
> pendientes; el enunciado oficial de IS2 será la fuente de trazabilidad exacta.

## Principios obligatorios

1. **Trazabilidad con IS2.** Incorporar el enunciado y los criterios oficiales al repositorio en una ubicación acordada. Enlazar cada requisito aplicable con su especificación, criterios de aceptación y evidencia de verificación. Registrar ambigüedades como preguntas; no completarlas por suposición.
2. **Alcance funcional conocido.** La línea base incluye registro e inicio de sesión con nombre de usuario y contraseña; creación y unión a salas; partidas de dos jugadores; tablero interactivo; comunicación entre frontend y backend; persistencia de jugadores, partidas y movimientos; gestión de errores; y consulta del histórico propio. El reproductor de partidas propias, que permite recorrer movimientos y posiciones anteriores, es la aportación funcional diferenciadora. El enunciado puede precisar este alcance.
3. **Stack aprobado.** Backend Java/Maven; frontend TypeScript puro con Vite, sin React; PostgreSQL; backend y base de datos mediante Docker Compose; REST para operaciones y consultas, WebSocket para eventos. Cambiar estos elementos requiere aprobación humana. Las versiones y frameworks no especificados siguen pendientes.
4. **Arquitectura y dependencias.** Aplicar arquitectura hexagonal en backend (dominio, casos de uso, puertos y adaptadores) y arquitectura hexagonal ligera en frontend. Mantener separación de responsabilidades, bajo acoplamiento e inversión de dependencias en ambos sistemas.
5. **Especificación e incremento.** Cada funcionalidad debe tener una especificación delimitada y criterios de aceptación aprobados antes de implementarse. Desarrollar por incrementos; no generar la aplicación completa de una sola vez.
6. **Aprobación de cambios importantes.** Antes de cambiar stack, límites arquitectónicos, persistencia, autenticación o contratos principales REST/WebSocket, presentar alternativas, impactos y recomendación, y obtener aprobación humana.
7. **Autenticación y autorización.** La autenticación aprobada usa nombre de usuario y contraseña. El servidor debe autorizar cada acceso a partidas y movimientos; solo sus participantes pueden consultar o reproducir una partida. Las decisiones de sesiones, cookies y almacenamiento seguro de contraseñas siguen pendientes y requieren aprobación antes de implementarse.
8. **Calidad verificable.** Mantener pruebas unitarias, de integración y funcionales. Ejecutar las pruebas pertinentes para cada cambio y verificar la entrega desde una instalación limpia siguiendo el README. Herramientas, cobertura mínima y checks automatizados siguen pendientes.
9. **Git y documentación proporcional.** Desarrollar cada funcionalidad en una rama e integrarla mediante Pull Request. Documentar cada funcionalidad con especificación y criterios de aceptación; reservar ADR para decisiones arquitectónicas relevantes, sin exigir documentación extensa para cambios triviales. Mantener un README que permita configurar, ejecutar y verificar el proyecto desde cero.

## Definition of Done

Un cambio está listo para integrar cuando:

- [ ] Su requisito está trazado al enunciado disponible y tiene especificación y criterios de aceptación aprobados.
- [ ] Los errores y los casos de acceso permitido/denegado pertinentes están definidos y verificados.
- [ ] Pasan las pruebas unitarias, de integración y funcionales aplicables.
- [ ] La documentación afectada está actualizada, sin crear ADR para cambios triviales.
- [ ] Está en una rama y se revisa mediante Pull Request.
- [ ] La entrega final puede verificarse desde una instalación limpia siguiendo el README.

## Recomendaciones

- Para decisiones arquitectónicas relevantes, registrar contexto, alternativas, decisión, consecuencias y estado en el registro de decisiones.
- Relacionar los flujos principales —registro, salas, partida, histórico y reproducción— con pruebas funcionales; añadir pruebas unitarias e integración para reglas y adaptadores afectados.
- Al elegir almacenamiento de contraseñas, evaluar una solución no reversible y mantener secretos fuera del repositorio. No se prescribe algoritmo ni biblioteca.
- Automatizar en CI los checks acordados para Pull Requests, una vez seleccionada la plataforma.

## Decisiones técnicas pendientes

- Incorporar el enunciado oficial y confirmar su ubicación en el repositorio y los criterios exactos.
- Versión de Java, framework backend y herramientas concretas para REST y WebSocket.
- Gestión de sesiones y cookies; biblioteca y estrategia de almacenamiento seguro de contraseñas.
- Acceso a PostgreSQL y, si se requieren migraciones, herramienta y política.
- Contratos REST/WebSocket, formato de errores, ciclo de vida de salas y partidas, reglas de tiempo y representación de movimientos, según el enunciado.
- Herramientas de pruebas, formato/linter, cobertura, estructura concreta del frontend, accesibilidad, rendimiento, CI y reglas detalladas de revisión de Pull Requests.

## Registro de enmiendas

| Fecha | Versión | Cambio | Motivo |
|---|---|---|---|
| 2026-11-09 | v1.0.0 | Ratificación inicial de la constitución revisada. | Aprobación humana de los principios, recomendaciones y decisiones pendientes. |
