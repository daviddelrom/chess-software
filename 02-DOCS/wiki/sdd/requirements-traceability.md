---
type: article
title: Matriz de trazabilidad de requisitos IS2
description: Requisitos, criterios de aceptación y evidencias derivados del enunciado oficial de IS2.
tags: [sdd, requirements, testing]
timestamp: 2026-11-09T14:10:00Z
topic: sdd
status: draft
sources:
  - ../../raw/is2/proyecto_ajedrez.pdf
score: 0.0
---

# Matriz de trazabilidad de requisitos IS2

## Fuente y método

Fuente oficial: [proyecto_ajedrez.pdf](../../raw/is2/proyecto_ajedrez.pdf), «Proyecto — Sistema de salas para jugar al ajedrez», Escuela de Ingeniería Informática, ULPGC. El PDF se conserva como fuente; esta matriz resume sus requisitos sin sustituirlo. La huella SHA-256 comprobada al incorporarlo es `f997d18bc2a11d9db35424fa665aaaa4846f380efac7efa30ae911f426c82cfc`.

Las referencias de página siguientes usan la numeración impresa dentro del PDF. Los criterios de aceptación convierten el texto del enunciado en comprobaciones observables; no eligen tecnologías ni añaden comportamientos no indicados por la fuente. Las alternativas que el documento presenta como ejemplos no son requisitos acumulativos.

Todavía no existen especificaciones funcionales ni pruebas de la aplicación. Por tanto, todas las relaciones con esos artefactos y toda evidencia de ejecución figuran como **pendientes**. Los identificadores de esta matriz son estables; si cambia su significado, se añadirá un identificador nuevo en lugar de reutilizar el anterior.

## Objetivos y requisitos funcionales

| ID | Referencia en el enunciado | Requisito oficial resumido | Criterio de aceptación verificable | Especificación / prueba / evidencia |
|---|---|---|---|---|
| IS2-F-01 | p. 1, §1 Objetivos; p. 1, §2 Enunciado | El sistema tiene, como mínimo, frontend y backend coordinados, con separación clara. | Se puede identificar y ejecutar frontend y backend como partes diferenciadas; el README describe cómo se coordinan. | Pendientes |
| IS2-F-02 | p. 1, §2 Enunciado; p. 2, Requisitos funcionales 1 | El frontend ofrece un tablero visible, permite crear o seleccionar/entrar en una sala y ofrece interacción mínima para mover o reproducir una partida. | En el frontend se observa el tablero y se puede demostrar el flujo de crear o seleccionar una sala y realizar la interacción admitida por la entrega. | Pendientes |
| IS2-F-03 | p. 2, Requisitos funcionales 2 | El backend puede ejecutarse de forma independiente. | El backend arranca siguiendo la documentación sin requerir que el proceso del frontend esté ejecutándose. | Pendientes |
| IS2-F-04 | p. 1, §2 Enunciado; p. 2, Requisitos funcionales 3–4 | Frontend y backend se comunican mediante una alternativa documentada y tienen un contrato de comunicación documentado. | Se identifica el mecanismo usado y se documentan sus rutas, eventos, mensajes, cuerpos o protocolo, según corresponda. | Pendientes |
| IS2-F-05 | p. 2, Requisitos funcionales 7 | Las partidas se registran persistentemente con identificador de sala o partida, jugadores, movimientos y fecha o estado. | Tras registrar una partida, una consulta permite comprobar su identificador, jugadores, movimientos y al menos uno entre fecha y estado. | Pendientes |
| IS2-F-06 | p. 1, §1 Objetivos; p. 1, §2 Enunciado; p. 2, Requisitos funcionales 8 | Existe un mecanismo para poner en contacto a dos usuarios y compartir una partida. | Se demuestra el mecanismo elegido con dos usuarios conectados a una sala o partida compartida. | Pendientes |
| IS2-F-07 | p. 2, Requisitos funcionales 9 | Se puede consultar el estado de una partida o su histórico. | Una consulta de una partida registrada devuelve su estado o su histórico, según la funcionalidad implementada y documentada. | Pendientes |
| IS2-F-08 | p. 2, Requisitos funcionales 10 | Se gestionan errores por partida inexistente, movimiento inválido según las reglas implementadas, usuario desconectado y datos incompletos. | Se provocan los cuatro casos enumerados y se observa una respuesta de error definida en cada uno, sin presentar ninguno como una operación exitosa. | Pendientes |
| IS2-F-09 | p. 2, Requisitos funcionales 11 | Se documentan configuración de puertos, base de datos y ejecución. | El README identifica los puertos y la configuración de base de datos necesarios, y explica cómo ejecutar los componentes. | Pendientes |
| IS2-F-10 | p. 2, Desarrollo de la entrega; p. 2, Requisitos funcionales 5–7 | El proyecto representa usuarios, partidas, movimientos y estados de partida; el resultado se incluye si procede. | El modelo y la documentación muestran usuarios, partidas, movimientos y estado; aclaran si se representa resultado y por qué aplica o no. | Pendientes |
| IS2-F-11 | p. 2, Desarrollo de la entrega e ideas propias; p. 5, Evaluación | La entrega incorpora una idea propia dentro del alcance y la justifica en el README. | El README identifica la aportación propia, explica su relación con el objetivo y permite localizarla en la entrega. | Pendientes |

## Criterios de diseño y arquitectura

| ID | Referencia en el enunciado | Requisito oficial resumido | Criterio de aceptación verificable | Especificación / prueba / evidencia |
|---|---|---|---|---|
| IS2-A-01 | p. 1, Competencias trabajadas; p. 2, Criterios de diseño | La arquitectura de sistemas muestra frontend, backend, base de datos y contratos. | El README contiene un diagrama o descripción equivalente en que aparecen esos componentes y sus contratos. | Pendientes |
| IS2-A-02 | p. 1, Competencias trabajadas; p. 2, Requisitos funcionales 5; p. 4, README | El backend aplica arquitectura hexagonal: dominio, casos de uso, puertos de entrada/salida y adaptadores. | La estructura y el README permiten reconocer esos elementos y sus responsabilidades. | Pendientes |
| IS2-A-03 | p. 1, Competencias trabajadas; p. 2, Requisitos funcionales 6; p. 4, README | El frontend usa arquitectura hexagonal ligera: UI, casos de uso de interacción, puerto de servicio y adaptador de comunicación. | La estructura y el README permiten reconocer esos elementos y sus responsabilidades. | Pendientes |
| IS2-A-04 | p. 2, Criterios de diseño | El frontend no escribe directamente en la base de datos. | La inspección del diseño y del flujo de persistencia muestra que las escrituras pasan por el backend. | Pendientes |
| IS2-A-05 | p. 2, Criterios de diseño | El backend no depende de componentes visuales del frontend. | El dominio, los casos de uso y adaptadores de backend no importan ni referencian componentes visuales del frontend. | Pendientes |
| IS2-A-06 | p. 2, Criterios de diseño | El modelo de partida está separado de la capa de transporte. | El modelo de partida puede usarse sin depender de tipos o mensajes propios del transporte escogido. | Pendientes |
| IS2-A-07 | p. 2, Criterios de diseño | La persistencia se encapsula en un adaptador de salida que implementa un puerto de la aplicación. | La implementación de persistencia se accede mediante un puerto definido por la aplicación; una prueba o inspección del diseño identifica esa relación. | Pendientes |
| IS2-A-08 | p. 2, Criterios de diseño | Los casos de uso de backend no dependen del framework HTTP, WebSocket o socket elegido. | Los casos de uso pueden probarse sin iniciar ni importar el framework de transporte escogido. | Pendientes |
| IS2-A-09 | p. 2, Criterios de diseño | La UI delega la comunicación de red en un puerto de servicio cuando puede hacerlo. | Las acciones de UI relevantes usan el puerto de servicio para comunicarse, en lugar de construir directamente mensajes o peticiones de red. | Pendientes |
| IS2-A-10 | p. 2, Criterios de diseño | El adaptador de comunicación del frontend se puede sustituir por un doble de prueba. | Una prueba puede conectar un doble de servicio/adaptador sin cambiar el caso de uso de interacción. | Pendientes |
| IS2-A-11 | p. 2, Criterios de diseño; p. 2, Requisitos funcionales 10 | La política de validación de movimientos queda documentada como reglas completas, subconjunto o límites explícitos. | La documentación declara cuál de esas políticas se implementa y las pruebas de movimientos inválidos concuerdan con ella. | Pendientes |

## Verificación esperada

| ID | Referencia en el enunciado | Requisito oficial resumido | Criterio de aceptación verificable | Especificación / prueba / evidencia |
|---|---|---|---|---|
| IS2-V-01 | p. 2, Verificación esperada; p. 5, Checklist | Frontend y backend se ejecutan desde una copia limpia del repositorio. | Una persona sigue las instrucciones documentadas desde una copia limpia y arranca ambos componentes. | Pendientes |
| IS2-V-02 | p. 2, Verificación esperada | Se crea una sala, se unen dos usuarios y se registran varios movimientos. | La prueba o comprobación documentada realiza el flujo completo y permite consultar la sala y los movimientos registrados. | Pendientes |
| IS2-V-03 | p. 2, Verificación esperada | Se conectan dos frontends o se simulan dos usuarios en una misma sala. | Se documenta y ejecuta una de las dos alternativas indicadas y ambos participantes comparten la sala. | Pendientes |
| IS2-V-04 | p. 2, Verificación esperada | Se consulta el histórico de una partida registrada. | La comprobación recupera una partida registrada y muestra su histórico disponible. | Pendientes |
| IS2-V-05 | p. 2, Verificación esperada | Se prueba un movimiento o petición inválida y se documenta la respuesta. | Se ejecuta al menos un caso inválido y el README o evidencia enlazada registra la respuesta observada. | Pendientes |
| IS2-V-06 | p. 2, Verificación esperada | Se sustituye un adaptador por un doble de prueba o se demuestra cómo hacerlo sin tocar el caso de uso. | Una prueba ejecuta esa sustitución, o la documentación muestra el punto de sustitución sin modificar el caso de uso. | Pendientes |
| IS2-V-07 | p. 2, Verificación esperada | Se comprueba tras reiniciar el backend si la persistencia conserva partidas, si esa opción está implementada. | Si la persistencia sobrevive al reinicio en la solución elegida, se registra una partida, se reinicia el backend y se consulta de nuevo; si no se conserva, se documenta ese límite. La implementación y la evidencia de esta comprobación siguen pendientes. | Pendientes |

## Entregables y README

| ID | Referencia en el enunciado | Requisito oficial resumido | Criterio de aceptación verificable | Especificación / prueba / evidencia |
|---|---|---|---|---|
| IS2-D-01 | p. 1, Tipo de entrega; p. 3, §3.1 | Proyecto individual, una sola entrega, en repositorio público llamado `chess-software`; la rama principal contiene la versión final. | El repositorio conserva el nombre y visibilidad exigidos y, al entregar, la rama principal contiene la versión evaluable. | Pendientes |
| IS2-D-02 | p. 2, Desarrollo de la entrega; p. 3, §3.1 | La construcción es progresiva y los commits muestran avance real; no se entrega como kata repetida ni requiere vídeo explicativo. | El historial del proyecto muestra incrementos con cambios reales; la entrega no depende de repetir katas ni de un vídeo. | Pendientes |
| IS2-D-03 | p. 3–4, §3.1 | El repositorio excluye binarios y resultados de compilación, incluye un `.gitignore` adecuado para Java e IntelliJ IDEA y contiene los archivos necesarios para reproducir la entrega. | La inspección del repositorio no encuentra los tipos de binarios enumerados por el enunciado; `.gitignore` cubre Java/IntelliJ y el repositorio contiene los archivos realmente necesarios para ejecutar y verificar la solución. | Pendientes |
| IS2-D-04 | p. 4, §3.1; p. 2, Criterios de diseño | No se versionan credenciales, tokens, claves de API, datos personales de bases de datos, rutas absolutas ni configuración fija de una máquina local. | La revisión del repositorio y su configuración no encuentra esos datos o referencias personales. | Pendientes |
| IS2-R-01 | p. 1, Tipo de entrega; p. 4, §3.2 | El README explica objetivo, compilación/ejecución, dependencias y versión de JDK, estructura y clases principales. | Cada elemento aparece documentado y coincide con los archivos del proyecto. | Pendientes |
| IS2-R-02 | p. 1, Tipo de entrega; p. 4, §3.2; p. 5, Aspectos README | El README explica arquitectura de sistemas e interna, contrato de comunicación, modelo de datos, ejecución, puertos y mecanismo para conectar usuarios. | Una persona puede identificar componentes, límites, comunicación, datos y pasos de ejecución a partir del README y sus diagramas/documentación enlazada. | Pendientes |
| IS2-R-03 | p. 4–5, §3.2 y Aspectos README | El README justifica la idea propia y declara límites conocidos de reglas de ajedrez, persistencia, concurrencia o comunicación. | La aportación y los límites aplicables están enumerados y concuerdan con el comportamiento entregado. | Pendientes |
| IS2-R-04 | p. 1, Tipo de entrega; p. 4–5, §3.2 y Elementos finales | El README incluye capturas obligatorias del tablero funcionando, una sala y una partida o histórico registrado. | Las capturas existen en el repositorio y muestran los tres contextos solicitados. | Pendientes |
| IS2-R-05 | p. 4, §3.2 | El README documenta la verificación automatizada o manual realizada. | Los pasos de verificación, resultados y evidencia enlazada permiten repetir o revisar las comprobaciones. | Pendientes |

## Rúbrica de evaluación

Los pesos se transcriben del enunciado; no son umbrales de aprobación.

| ID | Referencia | Criterio y peso | Evidencia esperada según la rúbrica | Estado |
|---|---|---|---|---|
| IS2-E-01 | p. 5, §4 Evaluación | Cumplimiento funcional — 25 % | Flujos principales para usar el tablero, conectar usuarios y registrar partidas. | Pendiente |
| IS2-E-02 | p. 5, §4 Evaluación | Arquitectura de sistema y hexagonal — 25 % | Separación reconocible de frontend, backend, contratos, puertos, casos de uso y adaptadores. | Pendiente |
| IS2-E-03 | p. 5, §4 Evaluación | Persistencia y trazabilidad — 15 % | Partidas, usuarios y movimientos registrados, consultables y reproducibles. | Pendiente |
| IS2-E-04 | p. 5, §4 Evaluación | Aportación propia — 15 % | Idea propia justificada, visible en el software y coherente con el objetivo. | Pendiente |
| IS2-E-05 | p. 5, §4 Evaluación | README — 15 % | Instalación, ejecución, arquitectura, capturas obligatorias y prueba del sistema explicadas. | Pendiente |
| IS2-E-06 | p. 5, §4 Evaluación | Verificación — 5 % | Pruebas automatizadas o comprobaciones manuales documentadas para frontend, backend y errores. | Pendiente |

## Decisiones de proyecto ya aprobadas (no atribuidas al PDF)

Estas reglas proceden de la [constitución SDD v1.0.0](./constitution.md) y de decisiones del usuario. Se incluyen para distinguirlas de los requisitos citados:

- Backend Java/Maven y frontend TypeScript puro con Vite; arquitectura hexagonal en ambos, ligera en frontend.
- PostgreSQL; backend y base de datos con Docker Compose; REST para operaciones/consultas y WebSocket para eventos. El PDF admite otras alternativas documentadas; este stack es una decisión específica del proyecto.
- Dado que se aprobó PostgreSQL persistente, verificar que las partidas sobreviven al reinicio del backend. Esto concreta para el proyecto la comprobación condicional `IS2-V-07` del enunciado.
- Registro e inicio de sesión con nombre de usuario y contraseña. El PDF habla de usuarios o sesiones, pero no exige este mecanismo de autenticación.
- Solo los participantes pueden consultar o reproducir sus partidas.
- El reproductor de partidas propias es la aportación diferenciadora aprobada para el proyecto. El PDF acepta la reproducción de partidas registradas como variante y exige una idea propia; la selección concreta procede del usuario.
- Las decisiones de versiones, frameworks, sesiones/cookies, biblioteca y almacenamiento seguro de contraseñas, contratos concretos, reglas de movimiento, herramientas y umbrales de pruebas continúan pendientes según la constitución.

## Ambigüedades y seguimiento

1. **Reglas de ajedrez:** el enunciado no exige motor completo, pero sí que se documenten las reglas validadas, los movimientos registrados y sus límites. La política concreta debe fijarse al especificar esa funcionalidad.
2. **Contacto entre usuarios:** el enunciado admite sala, invitación, emparejamiento, código compartido u otra variante indicada; no selecciona una. La constitución ya aprueba salas para dos jugadores; detalles adicionales quedan pendientes.
3. **Usuarios o sesiones:** el enunciado permite coordinar usuarios o sesiones y no define autenticación. El proyecto ya aprobó usuario/contraseña, pero sesiones, cookies y almacenamiento seguro siguen pendientes.
4. **Persistencia tras reinicio:** el enunciado condiciona esta comprobación a la opción implementada. En este proyecto, PostgreSQL persistente ya está aprobado; por tanto, se verificará que las partidas sobreviven al reinicio del backend.
5. **Resultado de partida:** el modelo mínimo lo incluye “si procede”; decidir y justificar aplicabilidad al definir el modelo de partida.
6. **Protocolos y formatos:** el enunciado permite varias formas de comunicación y no fija contratos concretos. Se mantienen los protocolos aprobados por la constitución, pero eventos, rutas, mensajes y formatos concretos no se infieren aquí.
7. **Capturas:** son obligatorias, pero no se fija formato, tamaño ni herramienta para producirlas.
8. **Enunciado y stack:** el documento pide versión de JDK y archivos reproducibles, mientras que la constitución deja versiones/frameworks abiertos. Deben acordarse antes de la especificación técnica y no se resuelven en esta matriz.

## Próximos enlaces de trazabilidad

| Artefacto | Estado |
|---|---|
| Enunciado oficial | Disponible: `../../raw/is2/proyecto_ajedrez.pdf` |
| Especificaciones de funcionalidad | Pendientes; se crearán y aprobarán antes de planificar o implementar funcionalidades. |
| Pruebas automatizadas y comprobaciones manuales | Pendientes; se enlazarán cuando existan y se ejecuten. |
| Evidencia de verificación | Pendiente; no se marca ningún criterio como satisfecho por intención. |
