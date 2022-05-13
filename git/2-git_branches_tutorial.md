# GIT Branches

Esté notas fueron tomadas del siguiente [video](https://www.youtube.com/watch?v=e2IbNHi4uCI).

Vamos a intentar traer algunos conceptos útiles para el manejo de ramas.
Lo primero es el HEAD branch, esta es tu rama principal.

Otra distinción importante es local and remote branches.

-> Vamos a crear una nueva rama.

- Git supone que tu quieres empezar tu nueva rama desde el current checkpoint

-> Si quiero empezar mi rama desde un commit especifico debo especificar el #id del commit

-> Cambiar de branch con git checkout

-> Para cambiar el nombre en remoto de una rama.
`git push origin --delete <old-name>`
`git push -u origin <new-name>`

-> -u es para hacer un tracking, tener enlazadas si por alguna razón creas una rama sin -u luego tienes que enlazarla si quieres hacer un tracking más efectivo

-> Descargar una rama en un repositorio que no tengo tracking en local
`git branch --track <local-name> origin/<remote-name>`
`git checkout --track origin/<remote-name>`

delete branch
-d -D

Merge vs Rebase

MERGE:

```mermaid
flowchart LR

A((c1)) --> B((c3))
B --> C((c4))
A --> D((c2))
D --> E[feature/uploader]
C --> F[C5]
F --> |C5=Merge commit|G(main/HEAD)
D --> F(C5)

```

REBASE:

```mermaid
flowchart LR

A((c1)) --> B((c3))
B((c3)) --> C[main/HEAD]
A((c1)) --> D((c2))
D((c2)) --> E((c4))
E --> F[feature/uploader]


O((c1)) --> P((c2))
P((c2)) --> L((c4))
L((c4)) --> |C4= feature/uploader|Q((c3))
Q((c3)) --> M[main/head]

```
