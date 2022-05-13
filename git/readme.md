# GIT

La idea principal es aprender de git más allá de lo que se ahora.

### Content

- Basic
-

### ¿Qué es Git?

Es un control de versiones, pero en palabras simples es la forma de mantener un historial de todo el código que hemos desarrollado en nuestra app.
En palabras mías: Git nos va ayudar que el historial sea una "versión" sobre otra "versión", algo como.
v0 => código inicial
v1 => código con el feature #1
v2 => código con el feature #2

Mantenemos el historial y adicional podemos crear estrategías más optimas para trabajo en equipo, resolución de problemás y algunas cosas más.
Realmente cada versión (v0, v1, v2) de mi ejemplo anterior se conoce como commits.

Entonces para que nos es útil GIT, imaginate en en la v2 de tu código cometiste un error, ¿cómo haces para devolverte si no usarás Git?
Soluciones obsoletas:

- Guardar un zip con cada versión nueva.
- Acordarte de como erá la versión anterior al error.
- Iniciar de nuevo.

Hagamos esto más complejo, ¿qué tal si trabajarás con 10 personas en el mismo proyecto?

- ¿Qué pasa si dos personas modifican un mismo archivo?
- ¿Qué pasa si el error lo introdujo otra persona, cómo devolver el código anterior si no tienes un historial de versiones?

Para resolver todas estás preguntas y más se creo Git.

### ¿Cómo funciona?

Esto es una explicación muy básica.
Todos las personas involucradas en un proyecto con git actualizan el código en un servidor central y luego de que se sube el código, cada persona en el equipo sincroniza sus cambios para poder tener la misma "versión" todos.

### Usos de GIT

- Historial del código
- Almacenar código
- Trabajo en equipo
- Controlar con más eficiencia donde se introducen errores

### Vamos a inicar con cosas básicas

'' Si nunca lo has instalado sigue los pasos del siguiente [link](https://git-scm.com/downloads)

Pasos para iniciar con GIT, primero vamos a hacer una configuración global usando

```git
git config --global user.name "name"
git config --global user.email email

# el siguiente paso es opcional, es para indicarle a Git que mi editor por defecto es vscode
git config --global core.editor "code --wait"

#si quieres ver tu configuración puedes darle el siguiente comando
git config --global -e
```

'' Algo que recomiendo mucho es crear alias para no tener que copiar tanto en consola, dejo el [link](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases) para aprender más sobre ellos.

### Comandos básicos

- **git init**: Iniciar un nuevo historial de tracking (Solo se debe hacer una vez)
- **git status**: Nos dice en todo momento como esta el estado actual de nuestro workspace
- **git add**: Agregar un nuevo estado (agregar/eliminar/modificar) nuestra etapa de stage (Es como el paso previo antes de llevar algo al historial)
- **git commit**: Agregar nuevos/modificados al historial de git

Situaciones:

1. ¿Cómo descartar los cambios de un archivo y volver a su 'versión' anterior ?
   git checkout _file-name_

2. ¿Cómo descartar **todos** los cambios ?
   git checkout .

3. ¿Cómo agregar **todos** los nuevos estados a la etapa de stage ?
   git add .

4. ¿Cómo "remover" un archivo de la etapa de stage?
   git restore --stage _file-name_

5. ¿Cuáles son los pasos para eliminar un archivo y actualizar el estado de la etapa de stage?

   - Eliminar el archivo
   - git add _file-name_

   Tambien puedes usar

   - git rm _file-name_

6. ¿Cuál es el comando para recuperar un archivo que he eliminado ?
   git restore _file-name_

### Git branches

#### MISC

1. ¿Cómo ignorar archivos para que nunca sean incluidos en los repositorios de Git?
   Usa el [.gitignore](https://git-scm.com/docs/gitignore), básicamente es un archivo para poner extenciones, archivos o carpetas que quieres que sean ignorados.
   **Útil para:** Credenciales, archivos del editor o datos sensibles.

2.
