---
type: article
title: Modelo conceptual mínimo del dominio
description: Conceptos provisionales de usuario, sala, partida y movimiento para el diseño inicial de chess-software.
tags: [sdd, domain, model]
timestamp: 2026-11-23T09:16:51Z
topic: sdd
status: draft
sources:
  - constitution.md
  - requirements-traceability.md
score: 0.0
---

# Modelo conceptual mínimo del dominio

Este documento describe una interpretación conceptual provisional. No constituye una decisión sobre cardinalidades, almacenamiento, persistencia física, ciclo de vida ni contratos.

## Relación con la constitución y la matriz

La [constitución SDD](constitution.md) aprueba usuarios con nombre y contraseña, partidas de dos jugadores, persistencia de usuarios, partidas y movimientos, control de acceso y el reproductor propio. La [matriz IS2](requirements-traceability.md) vincula este modelo con los identificadores `IS2-F-05`, `IS2-F-10`, `IS2-A-06` y `IS2-A-11`.

## Entidades propuestas

| Concepto | Naturaleza propuesta | Responsabilidad conceptual | Decisiones aún abiertas |
|---|---|---|---|
| Usuario | Entidad | Representa una identidad registrada; participa en salas y partidas. | Identidad técnica, nombre visible, unicidad exacta y atributos mínimos. |
| Sala | Entidad provisional | Reúne participantes antes de iniciar o compartir una partida. | Creación, ciclo de vida, afinidad a partidas, capacidad exacta y mecanismo de unión. |
| Partida | Entidad | Relaciona participantes con movimientos y estado; permite consulta autorizada e histórica. | Representación del estado, creación, resultado, identificación persistente y ciclo de vida. |
| Movimiento | Registro conceptual | Representa una acción realizada dentro de una partida y su orden. | Contenido mínimo, validación, representación serializada y reglas aceptadas. |

## Relaciones conceptuales

- Un usuario participa en cero o más salas.
- Una sala se relaciona conceptualmente con una partida para compartir el contexto de juego. El número exacto de partidas asociadas a una sala y su duración siguen pendientes de decisión.
- Una partida relaciona exactamente dos participantes en el alcance conocido.
- Una partida contiene una secuencia ordenada de movimientos.
- Solo los participantes pueden consultar o reproducir una partida propia.

Estas relaciones son propuestas de trabajo, no cardinalidades aprobadas ni un esquema de datos.

## Identidad y autorización

Usuario, sala y partida necesitan una forma estable de identificarse dentro del dominio. El formato y las operaciones concretas de identidad no se fijan aquí.

La autenticación usa nombre de usuario y contraseña según decisiones aprobadas. El mecanismo de sesión, la forma de transportar la identidad autenticada y el almacenamiento seguro de credenciales siguen abiertos. Ninguna decisión de este documento autoriza una elección técnica.

## Límites explícitos

Este modelo no fija:

- columnas, tablas, claves foráneas o migraciones;
- endpoints, mensajes, eventos o formatos de transporte;
- bibliotecas, frameworks o estructuras de paquetes;
- reglas completas de ajedrez, enroque, jaque, jaque mate o tablas;
- temporizadores, puntuaciones, emparejamiento o desconexiones;
- representación exacta de posiciones anteriores o del reproductor.

## Criterios de revisión

El modelo se podrá considerar válido para avanzar a especificación cuando se apruebe:

1. Qué atributos mínimos son necesarios para usuario.
2. Qué relación existe entre sala y partida.
3. Qué datos mínimos identifica una partida.
4. Qué representa un movimiento en la primera implementación.
5. Qué casos de acceso denegado deben verificarse.
