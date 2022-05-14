# ¿ Cómo deshacer errores ?

Los errores pueden pasar, el desarrollo de software es un proceso creativo y que involucra personas, las personas cometemos errors.
Para eso es git, es nuestro helper, nuestra muralla para combatir errores.

Vamos a ver 17 casos donde git nos va ayudar a deshacer/prevenir errores.

### 1 Descartar todos los cambios en un archivo (uncommitted)

-> `git restore <file-name>`
-> `git checkout <filename>`

### 2 Restaurar un archivo eliminado (uncommitted)

-> `git restore <file-name>`

### 3 Descartar algunas lineas de un archivo (uncommitted)

-> `git restore -p <file-name>`

### 3 Descartar todos los cambios en local (uncommitted)

-> `git restore -p <file-name>`
