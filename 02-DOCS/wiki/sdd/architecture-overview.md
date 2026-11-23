---
type: article
title: Esquema mínimo de arquitectura hexagonal
description: Límites conceptuales provisionales del backend y frontend sin seleccionar frameworks ni bibliotecas.
tags: [sdd, architecture, hexagonal]
timestamp: 2026-11-23T09:16:51Z
topic: sdd
status: draft
sources:
  - constitution.md
  - requirements-traceability.md
score: 0.0
---

# Esquema mínimo de arquitectura hexagonal

Este esquema fija responsabilidades conceptuales aprobables sin seleccionar frameworks, bibliotecas, rutas, eventos, formatos ni paquetes concretos.

## Arquitectura de sistema

```text
Usuario
  -> Frontend
      -> casos de uso de interacción
      -> puerto de servicio
      -> adaptador de comunicación
  -> Backend
      -> adaptador de entrada
      -> casos de uso
      -> dominio
      -> puerto de persistencia
      -> adaptador de persistencia
  -> PostgreSQL aprobado como persistencia proyectada
```

La comunicación concreta entre frontend y backend sigue pendiente; el proyecto aprobó REST para operaciones y WebSocket para eventos, pero no fija contratos en este documento.

## Backend mínimo

| Capa | Responsabilidad conceptual | Elementos iniciales |
|---|---|---|
| Dominio | Reglas independientes del transporte | Usuario, credencial conceptual y reglas mínimas de identidad; modelo de partida puede crecer en incrementos posteriores. |
| Casos de uso | Orquestar operaciones del dominio | Registrar usuario e iniciar sesión. |
| Puertos de entrada | Expresar operaciones requeridas por el exterior | Operaciones conceptuales de registro y autenticación. |
| Puertos de salida | Expresar dependencias externas | Persistencia de usuario y consulta de credenciales, sin fijar tecnología. |
| Adaptadores de entrada | Conectar transporte externo | Adaptador a elegir más adelante para operaciones REST. |
| Adaptadores de salida | Implementar dependencias externas | Adaptador de persistencia sustituible por PostgreSQL o doble de prueba. |

Los casos de uso no importarán ni referenciarán HTTP, WebSocket, SQL ni componentes visuales.

## Frontend mínimo

| Capa | Responsabilidad conceptual | Elementos iniciales |
|---|---|---|
| UI | Presentar formularios y resultados | Registro e inicio de sesión. |
| Casos de uso de interacción | Coordinar acciones de usuario | Preparar registro, enviar credenciales e interpretar el resultado. |
| Puerto de servicio | Definir operaciones de comunicación necesarias | Operación conceptual de registro y operación conceptual de inicio de sesión. |
| Adaptador de comunicación | Implementar el puerto | Adaptador REST o doble sustituible; el contrato concreto sigue pendiente. |

La UI delegará la comunicación al puerto de servicio. No escribirá directamente en PostgreSQL ni contendrá lógica de persistencia.

## Límites y dependencias

- El modelo de partida permanecerá separado de tipos o mensajes de transporte.
- La persistencia se encapsulará detrás de un puerto de salida.
- Los adaptadores podrán sustituirse por dobles de prueba sin modificar casos de uso.
- La persistencia, autenticación y comunicación tendrán pruebas unitarias o de integración aplicables según su responsabilidad.

## Requisitos IS2 relacionados

- `IS2-A-01`: arquitectura de sistema reconocible.
- `IS2-A-02`: backend hexagonal.
- `IS2-A-03`: frontend hexagonal ligero.
- `IS2-A-04`: el frontend no accede directamente a la base de datos.
- `IS2-A-05`: el backend no depende de componentes visuales.
- `IS2-A-06`: el modelo de partida separado del transporte.
- `IS2-A-07`: persistencia detrás de puerto y adaptador.
- `IS2-A-08`: casos de uso independientes del transporte.
- `IS2-A-09` y `IS2-A-10`: puerto y sustituibilidad en frontend.

## Tecnologías aprobadas

| Área | Tecnología aprobada | Alcance de la aprobación |
|---|---|---|
| Backend | Java y Maven | Lenguaje y herramienta de construcción aprobados; no se fija versión. |
| Frontend | TypeScript puro con Vite | Tecnología de desarrollo aprobada; no se fija React ni otras bibliotecas de UI. |
| Persistencia | PostgreSQL | Sistema de base de datos aprobado; no se fija herramienta de migración ni esquema. |
| Operaciones y consultas | REST | Mecanismo aprobado para operaciones y consultas; rutas y formatos siguen pendientes. |
| Eventos | WebSocket | Mecanismo aprobado para eventos; mensajes y ciclo de vida siguen pendientes. |

## Decisiones pendientes

Sin aprobar todavía quedan las versiones de Java y herramientas, el framework HTTP backend, las bibliotecas concretas de acceso a datos y autenticación, los contratos REST, los eventos y formatos WebSocket, las migraciones PostgreSQL y las herramientas de pruebas.

Estas elecciones deberán someterse a análisis y aprobación antes de implementarse.
