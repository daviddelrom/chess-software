---
type: specification
title: Registro e inicio de sesión
description: Especificación detallada inicial para registro e inicio de sesión sin fijar contratos técnicos pendientes.
tags: [sdd, specification, authentication]
timestamp: 2026-11-23T09:16:51Z
topic: sdd
status: draft
sources:
  - ../constitution.md
  - ../requirements-traceability.md
  - ../domain-model.md
  - ../use-cases.md
score: 0.0
---

# Especificación: registro e inicio de sesión

Estado: borrador pendiente de aprobación humana. Esta especificación delimita comportamiento observable; no aprueba arquitectura concreta, endpoints, formatos de datos, tablas ni bibliotecas.

## Alcance

Incluye:

- registrar una identidad con nombre de usuario y contraseña;
- rechazar registro incompleto o duplicado;
- iniciar sesión con credenciales válidas;
- rechazar credenciales inválidas;
- preservar la contraseña fuera de respuestas y registros observables.

No incluye:

- contratos REST o WebSocket concretos;
- sesiones, cookies o tokens concretos;
- recuperación o cambio de contraseña;
- roles, permisos administrativos o bloqueo temporal;
- creación de salas o partidas;
- reglas completas de ajedrez;
- persistencia física o esquema SQL.

## Requisitos relacionados

- `IS2-F-08`: gestión de datos incompletos y errores.
- `IS2-F-10`: representación mínima de usuarios.
- `IS2-A-02`: arquitectura hexagonal del backend.
- `IS2-A-03`: arquitectura hexagonal ligera del frontend.
- `IS2-A-08`: casos de uso independientes del transporte.
- `IS2-A-09` y `IS2-A-10`: comunicación sustituible en frontend.
- `IS2-V-01`: ejecución desde instalación limpia.
- `IS2-V-05`: respuesta observable ante petición inválida.

## CU-01: registrar usuario

### Precondiciones

- Se dispone de la solicitud de registro con los datos introducidos.
- El nombre de usuario se comprobará durante el registro para determinar si está disponible.
- Existen reglas mínimas de validación aprobadas, pero su detalle sigue pendiente.

### Flujo principal

1. Se recibe una solicitud de registro con nombre de usuario y contraseña.
2. Se valida que ambos datos cumplen las reglas aprobadas.
3. Se comprueba que el nombre de usuario no existe.
4. Se crea una identidad de usuario.
5. Se devuelve un resultado de éxito que no incluye la contraseña ni información técnica innecesaria.

### Alternativas de error

- Datos incompletos: el registro falla con un resultado claramente asociado a entrada incompleta.
- Nombre de usuario ya existente: el registro falla sin crear un duplicado.
- Credencial fuera de la política aprobada: el registro falla según la política aprobada.

La política exacta de nombres y contraseñas no está aprobada.

### Criterios de aceptación

- CA-AUTH-01: con datos válidos y un nombre disponible, se crea exactamente una identidad.
- CA-AUTH-02: intentar registrar un nombre ya existente devuelve una situación de conflicto y no crea una segunda identidad.
- CA-AUTH-03: omitir nombre o contraseña produce un resultado de validación sin crear usuario.
- CA-AUTH-04: la contraseña no aparece en respuestas ni en datos visuales o registros de operación.
- CA-AUTH-05: la creación puede verificarse mediante pruebas unitarias y de integración sin fijar aún el framework de transporte.

## CU-02: iniciar sesión

### Precondiciones

- Existe una identidad registrada para las credenciales utilizadas.
- El mecanismo para representar una sesión o identidad autenticada ha sido aprobado.

### Flujo principal

1. Se recibe un nombre de usuario y una contraseña.
2. Se valida la presencia de ambos datos.
3. Se resuelve la identidad correspondiente.
4. Se verifica la credencial mediante el mecanismo seguro aprobado.
5. Ante credenciales válidas se produce una sesión o resultado autenticado conforme a la decisión aprobada.

### Alternativas de error

- Datos incompletos: el inicio falla como entrada inválida.
- Usuario inexistente o contraseña incorrecta: el inicio falla sin revelar qué parte fue incorrecta.
- El mecanismo de sesión no está disponible: se devuelve un error de sistema definido, sin tratarlo como credencial válida.

### Criterios de aceptación

- CA-AUTH-06: credenciales válidas producen una identidad autenticada según el mecanismo aprobado.
- CA-AUTH-07: ante una contraseña incorrecta, la respuesta externa es equivalente a la producida cuando el usuario no existe y no revela cuál ocurrió.
- CA-AUTH-08: ante un usuario inexistente, la respuesta externa es equivalente a la producida cuando la contraseña es incorrecta y no revela cuál ocurrió.
- CA-AUTH-09: omitir nombre o contraseña devuelve validación y no inicia sesión.
- CA-AUTH-10: el caso de uso puede probarse independientemente del adaptador HTTP o WebSocket.

## Nota de autorización futura

Una sesión o identidad autenticada no permitirá consultar partidas ajenas ni reproducir partidas en las que el usuario no sea participante. Este comportamiento no forma parte de los criterios verificables del incremento inicial de autenticación.

La autorización se especificará y verificará al incorporar salas, partidas e histórico.

## Decisiones necesarias para redactar esta especificación

La especificación ya puede revisarse sin estas elecciones técnicas:

- Alcance mínimo de nombre de usuario, longitud y caracteres.
- Alcance mínimo de contraseña, longitud y caracteres permitidos.
- Qué datos se consideran identificadores públicos frente a datos privados.
- Cómo describir y verificar los errores de registro e inicio sin revelar detalles.

Estas decisiones afectan el contenido de los criterios, pero no bloquean su aprobación estructural ni la trazabilidad.

## Decisiones necesarias antes de implementar

- Framework backend concreto y versiones.
- Estrategia de sesión o identidad autenticada.
- Biblioteca o estrategia de almacenamiento seguro de contraseñas.
- Interfaz concreta del adaptador de persistencia de usuarios.
- Contrato externo de registro e inicio de sesión.
- Herramienta y formato de pruebas aplicables.
- Persistencia física y migraciones, si se requieren.

El framework backend es una decisión que puede esperar para terminar el diseño, pero deberá aprobarse antes de programar.

## Evidencia prevista

- Pruebas unitarias del dominio y casos de uso.
- Pruebas de integración con adaptadores sustituibles.
- Comprobación funcional manual o automatizada de registro e inicio.
- Evidencia enlazada desde el README o artefacto de pruebas cuando exista.

Las herramientas y umbrales concretos no se fijan en este documento.
