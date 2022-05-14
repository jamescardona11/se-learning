# Git Merge vs Rebase vs Squash

# merge

Varios padres

Mezcla los commits en un nuevo commit y conserva el historial
Integra lo "mejor" rebase y squash porque puedes ver la granularidad de rebase pero la limpieza de squash

# rebase

Unico padre un historial

Replica los commits en la rama principal

# squash

Unico padres 0 historial

Agrupa todos los cambios de la rama b en la rama a en un nuevo commit
para hacer esto en consola debemos hacer lo siguiente

-> `git merge --squash <branch-name>`

-> `git rebase -i HEAD~#`
-> marcar todas las acciones como _squash_ menos la primer en la lista de acciones

---

Cuando estemos trabajando y se han introducido cambios a la rama principal una buena estrategia es hacer un rebase para no hace mucho merge commit
