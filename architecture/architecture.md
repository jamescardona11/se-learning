# Architecture

Notas de estudio sobre arquitectura de software cosas que me han ido gustando y quiero plasmar acá.

### Arq para aplicaciones React

[REF](https://www.youtube.com/watch?v=bFcUj-7VEho)

Citando un poco a Khalil Stemmler, la lógica de negocio no pertenece al frontend. Nuestros frontend deberían ser tontos a nivel de lógica y mantenerlos simples a nivel de arquitectura es uno de los mayores desafíos. A través de estos patrones de diseño transformamos react en una especie de angular, con código verboso y difícil de leer. Si bien hay casos de uso para la aplicación de esta arquitectura, no creo que sea recomendable para el 90% de los casos, ya que nuestro foco debería ser hacer software más pequeño, eficiente y por sobre todo, simple. El fondo, lo comparto totalmente (Depender de contratos y no de implementaciones, desacoplamiento, sustitución, testeabilidad), pero creo que podemos encontrar arquitecturas más simples para aplicarlo.


### ¿Qué es la clean Arq, Cómo aplicarlo a Frontend?
[REF VIDEO](https://www.youtube.com/watch?v=vRGVnqylO68)
las arquitecturas tienen un propósito similar con un enfoque/orientación diferente.
"Separación responsabilidades/componentes/usos"

Domain - Core
1- Todo lo que toca el sol depende de dominio
2 ¿De que depende el dominio?
- Nada, el dominio no se toca
- Entidades, Reglas de negocios

Application/Presentation
- Casos de uso
- "Todo lo que modifica las entidades"
  
Adapters: Comunica con servicios externos y adapta todo con nuestra app.
Convertir información antes de ir al dominio - DTO

Dependency Role:
Domain <- Application <- Adapters

--- 
"Acortar bordes (Quitar cosas para llegar)"
Evitar Dependencias circulares
Bajamente acoplado |
Altamente cohesivo | Reusable, sin efectos secundarios


Ventajas: Dominio separado
Casos de uso independientes
Servicios externos intercambiables

Desventajas: 
Lleva tiempo
Overlay verbose (demasiado detallado)
Onboarding más difícil
Incrementa el tamaño del código

¿Cómo cortar caminos de forma correcta?
-> Extrae el dominio. "Puedes saltar otras capas"
-> No acortar el dependency role


### Clean Architecture
REF: Dev experto -  Antonio Leiva

Conceptos:
1- ¿Por qué todo en capas?
2- ¿Tienes reglas flexibles e interpetables?

### Clean para aplicaciones en React
REF: Osma CEA

- A medida que crece podemos crear más capas
- Capas nos ayudan a evitar dependencias circulares
  

### Desarrollo Web -  Arq de software vs Arq Hexagonal
REF: Javier velez Reyes - "Ni nueva, Ni arquitectura, Ni exagonal"

Cryptal clear - Rup XP
La arq son la vuelta de tuerca de MVP
"Controladores y modelos" deben tener el mismo comportamiento, si se usan con vista

**Heragonal** Tambien se llama puertas y adaptadores
- Controladores y modelos no acoplados a ningun framework
- Vistas -> Atacan comunicación -> Dependiendo de la interfaz que publique los controladores

Cualquier mantenimiento adaptativo debería ser open-close, podemos añadir cosas sin que afecte lo actual
**Tip** Una forma de no usar Inyección, es con Prototype y Abstract Factory

Puerto = Plugin = Interfaz
Actores = Son los que atacan(interacción)

Una app debe comportase igual sin importar quien la ataque (ej: usuarios, test, otro sistema)


### ¿Qué cambio mi forma de ver la arq?
REF = CODELY

- Retos de escalabilidad
- Composición vs herencia
- Contenedor de dependecias
- Modelo adaptadores
- Hexagonal
- Value Objects (DDD)
- Testing
- Integración continua
- DTO vs GET
- Programación reactiva
- Agile


### Introducción a Arq de software 
REF = Codely

-> Reglas que definimos para mejorar nuestro entendimiento de una APP
-> Evitar el acoplamiento

Común entre todas las arq:
-> Distintas capas
-> Regla de dependencia (fuera hacia adentro)

Estructura de carpetas:
-> mooc "Bundle context"


### Arquitectura Android:
REF: Dev Experto

- Patrones de arquitectura MVC, MVVM
Definen como se organiza la capa de presentación

Estructura

View <-  Mediador  -> Model
Mediador: Diferente MVC, MVP, MVVM

MVC = Domain - xml - Activity
MVP = Domain - Activity - Presenter
MVVM = Domain - Activity - Observables




