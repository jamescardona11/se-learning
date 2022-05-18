# Tipos de Flow

Todo lo tome de un alista de reproducción que inicia con este [video](https://www.youtube.com/watch?v=M_3VeKPFi5U&list=PLZVwXPbHD1KM5oLAmhz-HHRIMhaOEXku5)
Complemente con este [video](https://www.youtube.com/watch?v=U_IFGpJDbeU)
Complemente con estos posts: [Post-1]()

¿Qué es un estrategia en git?
Es la manera en la que se administran los branches y releases, en otras palabras como se integra y se hace que el código de desarrollo llegue al branch de producción.

# 1 Git Flow

Simplemente, se van creando feature desde una rama long-term y se van integrando a develop o master
Entonces se van creando features y features

Master, develop, release
Features, hotfix

Desarrollo: Features branches
Pre-prod: Develop
Prod: Releases branches

El estado de algunos hotfix a veces no es consistente porque no se integran.

---

Development branch

- Muchas ramas para muchas cosas
- Mergin problems

---

Complemente con estos posts: [Post-1](https://www.atlassian.com/es/git/tutorials/comparing-workflows)

### ¿Qué es?

Es un flujo para trabajos de equipos distribuidos, parte de la idea que creamos una rama principal, es nuestra rama segura y de acá derivamos la estrategia creando ramas de soporte.
Es útil para proyectos que tienen un ciclo de publicación programado, así como para practicas de CD en DevOps.

![](https://wac-cdn.atlassian.com/dam/jcr:cc0b526e-adb7-4d45-874e-9bcea9898b4a/04%20Hotfix%20branches.svg?cdnVersion=346)

### ¿Cómo funciona?

Vamos a establecer las dos ramas principales Main y Develop para llevar el historial del proyecto.
La rama main se usa para almacenar el historial de publicación.
La rama develop se usa para la integración de nuevos features.

### Ramas de features

Las ramas de features nuevas deben partir de la rama develop y cuando la feature esta terminada se debe integrar nuevamente a develop.

[comment]: ![](https://wac-cdn.atlassian.com/dam/jcr:34c86360-8dea-4be4-92f7-6597d4d5bfae/02%20Feature%20branches.svg?cdnVersion=346)

### Ramas de release

Cuando se acerque la fecha de release o tengamos suficientes caracteristicas integradas debemos bifurcar las caracteristicas en una rama de **release**, cuando se crea esta rama ya no pueden añadirse nuevas funcionalidades a la rama de **release** y esta rama solo deben producirse la solución de errores(hotfix).

Cuando el release esta listo se debe enviar a la rama main y adicional a la rama develop.

### Ramas de hotfix

Son ramas que sirven para reparar errores en producción siempre deben salir de la rama main.
Cuando se termine la corrección debe integrarse a main y a develop.(o la rama de release)

### Conclusión

Este flujo de trabajo es ideal para los flujos de trabajo de software basados en publicaciones.
Gitflow ofrece un canal específico para las correcciones de producción.

Pros:

- Alienta el uso de pull request.
- Control estricto de los cambios, porque normalmente solo algunos desarrolladores esta autorizados para aprobar los pull request.
- Después de entender como funciona, es simple de utilizar.

Contras:

- Los primeros 2 beneficios también se convierten en contras, porque el tener tanto control del proceso alienta y crea dependencia de una persona o varias personas encargadas al momento revisar los cambios, en algunos casos puede llegar a convertirse en micro-management.

- El crear branches de larga vida (long-living branches), puede provocar que cuando necesitemos unificar (mergear) el código se creen muchos conflictos sobre todo en equipos que están desarrollando una misma sección. Ej. Supongamos que se va a crear el branch de release para que se le empiecen a realizar pruebas, por otra parte, el equipo debe seguir desarrollando funcionalidades que no son parte del release y se continua integrando código al branch de develop, creando así 2 lineas de "tiempo" (develop y release).

- No permite hacer un release de código rápido. Imaginemos que por error, reparamos un bug en el branch equivocado o se se integro al brach equivocado (siguiendo el flujo normal) vamos a tener que volver a crear un pull request, esperar al review, el build, correr los tests, etc., tiempo tiempo tiempo ⏳. O bien simplemente si queremos agarrar lo que se ha desarrollado y hacer un release inmediatamente, no es posible, es muy probable que el código no se encuentre listo para hacerlo.

---

# 2 Github Flow / Feature branching

Complemente con estos posts: [Post-1]()

Es muy simple.
Solo se tienen dos ramas master y features
Lo que deployean es las ramas features.
Se integra a master es después de que se pasó pruebas

Desarrollo: Features branches
Pre-prod: features
Prod: Features o master

Se entregan más funcionalidades más rapidas.
Master es deployable siempre

- Una rama per feature
- Las features son deployables
- CD
- Short delivery
- Pull request para unir cógio y dar feeback

---

![](https://www.flagship.io/wp-content/uploads/github-flow-branching-model.jpeg)

# 3 Git release Flow: Microsoft Git

Partimos de master
Tenemos es topic branches (no features)
Se integran los topic a releases
Se deployean releases

Desarrollo: topic branches
Pre-prod: features
Prod: Features o master

Si hay fallos se hace una rama hot fix y cherry-pick para integrrar

# 4 Gitlab flow / Enviroment branching

Tenemos master se deployea desde staging
Tenemos feature/hotfix y hacemos merge-request para integrar a master
Tenemos diferentes entornos pre-prod y producción que parten desde master

Se usan cherry-picks para hotfix

---

- Cada enviroment esta encima de otro
- todos los cambios se pasan por todos los enviroments

![](https://www.flagship.io/wp-content/uploads/gitlab_flow_environment_branches.png)

# 5 Trunk-Based-Development

Master
features branches
Se integan las features a master y se deployean por medio de una rama llamada release branch

Desarrollo: features
Prod: master o Tag

-> Puede tener releases branches
-> Puede tener tags
-> Master siempre es deployable

Una sola rama donde se sacan features de esta y se van integrando para generar releases

- Solo una rama
- Debe ser un equipo maduro
- Es orientado a deploys
- CI/CD

---

Complemente con estos posts: [Post-1](https://dev.to/marianocodes/por-que-trunk-based-development-i5n) [Post-2](https://dev.to/marianocodes/que-son-los-feature-flags-kc7) [Post-3](https://medium.com/@TEvolvers.dev/trunk-based-development-una-sola-rama-un-solo-objetivo-6f8beb6cb231) [Post-4](https://devcycle.com/blog/transitioning-to-trunk-based-development)

### ¿Qué es?

Es una estrategia donde se usa una rama principal main, en esta rama todo el equipo se integra haciendo push a esta rama. La rama trunk es promovida donde se requiera, como por ejemplo a ambientes de pre-productivos, local, etc. Su veracidad y respaldo la dan los tags o etiquetas. Se dice que las ramas de features solo deben durar un día.

¿Qué se requiere que un equipo trabaje con TBD?, madurez sin esto esta estrategia se verá impactada por múltiples conflictos que a su vez se evidencia en fallos de la aplicación.
Madurez personal como técnica.

![](https://uploads.toptal.io/blog/image/129304/toptal-blog-image-1551794413174-f4139c4be533dc592d49f9a0bcc330f0.png)

- No existen ramas de larga duración. No se le da mantenimiento a ningun branch.
- Se deben hacer commits al menos una vez al día (no es que vamos a subir cualquier cosa)
- Todo commit es un código funcional, donde se hicieron pruebas necesarias y lo necesario para asegurarnos de no introducir un bug
- El trunk siempre debe estar en un estado optimo para release

Pros:

- Release por demanda
- Evitamos grandes conflictos y merge extras. No tiene sentido que despues de que un código ya paso a producción debamos integrarlo nuevamente hacia otras ramas
- Los desarrolladores siempre trabajan en código más reciente
- El equipo se vuelve más efeciente a la hora de entregar código

Cuando usarlo:

- Si la frecuencia de release es alta, trunk based development es la estrategia adecuada.
- Equipos maduros y productos establecidos, con sus tiempos y fechas de release bien definidios es probable que no lo necesiten.

¿En trunk based development no se hace revisión de código o pull request?
Si, pero principalmente se anima que haya más pair programming y no tener que hacer pull requests. En la versión escalada (sclaed trunk based development) para equipos más grandes, se permite la creación de branches de tiempo corto, hacerles code review y sean integradas rápidamente.

¿Qué rama se despliega a QA o release?
En TBD se usa el trunk para todos los ambientes, está debe conllevar un tag o etiqueta con la versión de los cambios importantes que se están promoviendo.

### Riesgos

1- Los desarrolladores deben ser responsables de su código y hacer su mayor esfuerzo para subir código de calidad, a su vez darles confianza que lo puedan hacer.
2- La automatización es clave para el exito de esta metodología, unittesting, CI.
3- Si bien sabemos que se espera que agreguemos funcionalidades completas, esto no implica que una lógica este lista para ser presentada al usuario final. Podemos usar features flags.

### ¿Qué son los feature flags?

Se usan cuando vamos a desarrollar algo y luego de integrarlo la tarea aun esta incompleta o tiene alguna dependencia no integrada aun.

#####  ¿Qué son?

Son valores boleanos que dicen si muestan o no el código.

##### ¿Cómo los puedo definir?

- Utilizar un servicio de features flags, ejemplo Bullet Train o Launch Darkly.
- Utilizar un lenguaje de back-end y crear un servicio, en el que el app pueda consumir y obtener los valores de los flags.
- Utilizar archivos locales dentro el app.

##### ¿Cómo los puedo definir?

# 6 Master-only flow / Single branch

Solo tenemos master

Debe ser código de calidad y con buenos test

# Conclusiones:

- Gitlab flow: No gusta, que haya una rama por entorno, agrega complejidad.
  Las build son 'inmutables'
- Release flow: No gusta, porque se espera mucho para hacer deploy.
- Git flow: No, permite con poca inversión de tiempo se aprenda.
  Pero se empieza a complicar la integración de ramas
  Si tenemos test y aumentamos la confianza para que se requiere pre-prod
- Trunk-based develoment: Si, se puede integrar rápido con master y se va deployment
- Github flow: Si, se pueden los entornos dinámicos por features. Se debe tener mucho CI/CD
- Master-only-flow: Si, simplificar para poder entregar más valor.

---

- Trunk-based: Automatización, tu equipo es maduro. Confias en test y tus acciones previas.
- Git flow: Si trabajas en equipos pequeños, equipos autosuficientes, aplicaciones pequeñas.
