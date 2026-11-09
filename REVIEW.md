# Guía de revisión — chess-software

## Qué sería un fallo importante

- Un requisito del enunciado no está trazado a especificación, aceptación y evidencia.
- Un usuario que no participa en una partida puede consultar o reproducirla.
- El histórico o el reproductor muestran movimientos o posiciones que no corresponden a la partida persistida.
- El frontend y backend gestionan de forma contradictoria errores o contratos REST/WebSocket aprobados.
- Un cambio importante altera el stack o los límites arquitectónicos sin aprobación humana.

## Rutas que se omiten

No hay rutas generadas, vendorizadas ni fixtures identificadas todavía. Añadir exclusiones solo cuando la estructura del proyecto las establezca.

## Límite de nits

No se ha aprobado un límite numérico. Priorizar hallazgos verificables y accionables; no fabricar hallazgos ni reportar preferencias de estilo cubiertas por herramientas acordadas.

## Revisión siempre humana

Requieren aprobación humana antes de integrarse los cambios importantes de arquitectura o stack, autenticación y autorización, persistencia, contratos principales REST/WebSocket e infraestructura de ejecución.

Esta regla es una instrucción de revisión, no una regla `risk.raise` aplicada por rutas. No existe aún estructura de aplicación que permita definir patrones de rutas sin especular; revisar esa configuración cuando exista el esqueleto del proyecto.

## Formato del resumen

Empezar cada revisión con el recuento: `N hallazgos: X bloqueantes, Y por corregir, Z nits`.
