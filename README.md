# chess-software

Proyecto académico de Ingeniería del Software II (IS2). La aplicación aún no está implementada.

## Preparar GitHub Copilot y rsc-harness

Requisitos: Node.js 18 o posterior, Git, Visual Studio Code y GitHub Copilot.

Desde la raíz del clon, ejecuta:

```sh
npx @ericrisco/rsc@4.1.0 sync
```

El comando reconstruye la configuración de rsc declarada en `.rsc.json`. Después, recarga Copilot en Visual Studio Code. Esto prepara el harness; todavía no hay comandos para construir o ejecutar la aplicación.

El perfil `02-DOCS/wiki/harness/user-profile.md` es personal y local; no se versiona. Si falta en un clon limpio, Copilot inicia `init` para crear un perfil local durante el primer uso. No se necesita ese archivo para ejecutar `rsc sync`.
