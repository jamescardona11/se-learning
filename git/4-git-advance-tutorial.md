# Git advance tutorial

Esté notas fueron tomadas del siguiente [video](https://www.youtube.com/watch?v=qsTthZi23VE).

### Interactive Rebase

Es una herramienta para optimizar y hacer una limpieza de tu historial de commits.

- Cambiar mensajes de los commit
- Delete commits
- Re-ordenar commits
- Combiar varios commits en uno solo
- Editar/ separar un commit en multiples

### Paso a paso

1. ¿Qúe tan lejos quieres ir? ¿Cuál sera tu commit "base" ?
2. `git rebase -u HEAD~3`
3. En el editor, solo determine que acciones(actions) vas hacer, no cambies el commit en este step
   Ex: **reword** cambiar el mensaje de un commit
   **squad** combinar dos commits en uno solo (donde se marque con squad - se combina con el superior a ese)

### Cherry pick

Cuando haces un merge generalmente combinas todos los commits en una rama cómo se muestra en la siguiente imagen.

![](/git/cherry-pick-issue.png)

Pero que pasa si no quiero tomar todo el historial de la rama b y solo quiero un commit en especifico, entonces es donde entra en acción el cherry pick

![](/git/cherry-pick-solution.png)

#### Alerta

- Cherry pick es para situaciones muy especificas, recuerda que esto reescribe el historial de Git, no se debe usar como reemplazo del merge.

Ex: cuando es una buena idea usar cherry-pick

- Supongamos que hiciste commit en una rama erronea
  ![](/git/cherry-pick-example.png)

Steps:

- Nos pasamos para la rama correcta
- Hacemos cherry-pick del commit con el hash
- Luego podemos hacer un reset `git reset --hard HEAD~1`

## Reflog

Pensemos en esto como un diario(journal) de todos los logs de git.

![](/git/reflog-issue.png)
El Reflog tiene el historial y puedo rescatar el commit anterior

Otro uso restaurar ramas.

## Submodulos

Buscar más sobre esto luego

## Search & Find

1- by date --before / --after
2- by message --grep
3- by author --author
4- by file --filename
5- by branch _branchA_

`git log --after-"2021-7-1"`

https://www.git-tower.com/learn/git/advanced-git-kit/
