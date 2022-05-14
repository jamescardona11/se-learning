# ¿ Cómo deshacer errores ?

De este [video](youtube.com/watch?v=lX9hsdsAeTk)

Los errores pueden pasar, el desarrollo de software es un proceso creativo y que involucra personas, las personas cometemos errores.
Para eso es git, es nuestro helper, nuestra muralla para combatir errores.

Vamos a ver 17 casos donde git nos va ayudar a deshacer/prevenir errores.

### 1 Descartar todos los cambios en un archivo (uncommitted)

-> `git restore <file-name>` o
-> `git checkout <filename>`

### 2 Restaurar un archivo eliminado (uncommitted)

-> `git restore <file-name>`

### 3 Descartar algunas líneas de un archivo (uncommitted)

-> `git restore -p <file-name>`

### 4 Descartar todos los cambios en local (uncommitted)

-> `git restore .`

### 5 Arreglar el último commit

-> `git commit --amend -m <new-message>`

Si quieres agregar algo que olvidaste
-> `git add .`
-> `git commit --amend -m <new-message>` o `git commit --amend --no-edit`

**amend** es un comando que reescribe el historial y si lo reescribimos debemos tener cuidado con los cambios en remoto

### 6 Revertir un commit en la mitad del proceso

-> `git revert <hash>`
Cuando se hace esto git va a crear un nuevo commit con el estado del revert

### 7 Resetear a una versión anterior

-> `git reset --hard <#hash>`
Cuidado que el --hard va a eliminar los commits después del hash destino

-> `git reset --mixed <#hash>`
Mantienen los cambios descartados como cambios locales, para que puedas trabajar con ellos, modificarlos, etc.

### 8 Resetear un archivo a versión anterior

-> `git restore --source <#hash> <file-name>`

### 9 Recuperar commits borrados

-> `git reflog` search the hash o HEAD# antes del reset
-> `git branch <branch-name> <#hash>`

### 10 Recuperar una rama borrada

-> `git reflog` search the hash o HEAD# de la rama
-> `git branch <branch-name> <#hash>`

### 11 Mover un commit a una nueva rama

-> `git branch <branch-name>`
-> `git reset HEAD~1 --hard`

### 12 Mover un commit a una rama diferente

-> movernos a la rama destino `switch` o `checkout`
-> `git cherry-pick <hash>`
-> movernos a la rama origen de donde movimos el commit
-> `git reset HEAD~1 --hard`

### 13-15 Rebase interactivo

1. ¿Qúe tan lejos quieres ir? ¿Cuál será tu commit "base" ? (El commit padre)
2. `git rebase -i HEAD~#` o `git rebase -i <hash>`
3. En el editor, solo determiné que acciones(actions) vas a hacer, no cambies el commit en este step
   13: **reword** cambiar el mensaje de un commit
   14: **drop** eliminar un commit
   15: **squad** combinar dos commits en uno solo (donde se marque con squad - se combina con el superior a ese en la lista)

PD: El orden de los commits está al reves en la lista de acciones

### 16 Agregar cambios a un commit viejo

-> Implementar los cambios que vamos a introducir
-> Buscar el hash del commit destino
-> `git commit --fixup <hash>`
-> `git rebase -i HEAD~# --autosquash` o `git rebase -i <hash> --autosquash` (recordar la regla de rebase ir un commit padre)
