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
-> Guardar un zip con cada versión nueva.
-> Acordarte de como erá la versión anterior al error.
-> Iniciar de nuevo.

Hagamos esto más complejo, ¿qué tal si trabajarás con 10 personas en el mismo proyecto?
-> ¿Qué pasa si dos personas modifican un mismo archivo?
-> ¿Qué pasa si el error lo introdujo otra persona, cómo devolver el código anterior si no tienes un historial de versiones?

Para resolver todas estás preguntas y más se creo Git.

### ¿Cómo funciona?

Esto es una explicación muy básica.
Todos las personas involucradas en un proyecto con git actualizan el código en un servidor central y luego de que se sube el código, cada persona en el equipo sincroniza sus cambios para poder tener la misma "versión" todos.

### Usos de GIT

-> Historial del código
-> Almacenar código
-> Trabajo en equipo
-> Controlar con más eficiencia donde se introducen errores

### Vamos a inicar con cosas básicas

'' Si nunca lo has instalado sigue los pasos del siguiente [link](https://git-scm.com/downloads)

Pasos para iniciar con GIT, primero vamos a hacer una configuración global usando

```git
git config --global user.name "tu nombre"
git config --global user.email tu-email

# el siguiente paso es opcional, es para indicarle a Git que mi editor por defecto es vscode
git config --global core.editor "code --wait"
```
