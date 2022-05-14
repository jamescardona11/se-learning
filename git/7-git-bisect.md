# Git Bisec

Intentar encontrar un commit que ha dañado nuestra aplicación.
Cómo se usa
-> `git bisect start`
-> `git bisect bad` (current)
-> `git bisect good <hash>`
-> ir marcando como bad or good cuando fucione
-> `git bisect reset` cuando encontremos el commit malo

Podemos ver el commit con: `git show <hash>`
Luego podemos revertir ese commit con -> `git revert <hash>`
