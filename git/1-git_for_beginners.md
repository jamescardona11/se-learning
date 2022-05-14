# GIT para principiantes

Esté tutorial hace parte del siguiente [blog-post]().
El tutorial es muy fácil de seguir, solo debes tener Git instalado y tener una cuenta de Github para la última parte del tutorial.

Sigue los pasos para que creemos nuestro primer repositorio, lo modifiquemos y lo subamos github

### Lo básico:

1. Crea una carpeta y abrir está carpeta en tu editor de código favorito.
2. Si ya tienes configurado git puedes salarte este punto.
   - `git config --global user.name "name"`
   - `git config --global user.email email`
3. Empecemos inicializando
   - `git init`
4. Vas a crear dos archivos **file1.txt**, **file2.txt**
5. Veamos como está nuestro workspace
   - `git status`
   * Debería aparecer que tenemos dos archivos en color rojo en nuestra consola.
6. Agreguemos los archivos a la etapa de stage
   - `git add .`
7. Veamos como está nuestro workspace nuevamente
   - `git status`
   * Debería aparecer que tenemos dos archivos en color verde en nuestra consola.
8. Hagamos nuestro primer commit
   - `git commit -m`
   * Después del _-m_ coloca el mensaje para guardar tu primer commit
9. Modifiquemos el **file1.txt**
   - Agreguemos algunos textos acá
10. Vuelve a agregar el archivo a la etapa de stage y haz un commit.

### Git branch:

1. Vamos a crear una nueva rama llamada **b1**
   - `git branch b1`
2. Modifiquemos el **file2.txt**, **file1.txt**
   - Agreguemos algún texto al file2 y agreguemos nuevo texto al file1
3. Veamos las diferencias de lo que hemos modificado
   - `git diff file1.txt`
4. Hagamos commit
5. Cambiémonos a la rama principal
   - `git checkout master`
6. Hagamos un merge
   - `git merge b1`
   - Ya tenemos los cambios de la rama b1 en nuestra rama principal
7. Borremos la rama b1
   - `git branch -d b1`

### Github:

1. Creemos un nuevo proyecto
2. Usemos el paso a paso que nos da github
   - `git remote add origin ...`
3. Subamos la rama a github
   - `git push -u origin master`

¡Felicitaciones!
Creaste tu primer proyecto y usaste diferentes estrategias para modificar, crear ramas, subir a github.
