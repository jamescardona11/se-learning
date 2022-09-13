# Hexagonal

## Hexagonal Architecture for Dummies

REF https://medium.com/codex/clean-architecture-for-dummies-df6561d42c94


La arquitectura hexagonal junto con Clean, son **Domain Centric**, son fundamentalmente DDD pero no lo único.

- Step 0: Una app es un conjunto de cosas que responde a "ataques/interacciones"
- Step 1: Dominio e Infraestructura

**Dominio**: Core Logic, Business Logic, algoritmos esenciales para el propósito.
Implementa casos de uso que son el corazón de la aplicación, cuando tu cambias el dominio cambias la esencia.

**Infrastructure**: La infraestructura representa la tecnología, es todo lo que no es business domain.

**Domain vs Infrastructure**: Core code no depende de sistemas externos, ni depende del código escrito para interactuar con un tipo específico de sistemas externos.
El dominio es el centro, porque es más estable que la infraestructura. Una arquitectura centrica pone el dominio en el centro y lo protege.
Por último tu puedes cambiar la infraestructura sin impactar el dominio.

- Step 2: adapters, use cases, entities
Estamos listos, para una segunda etapa para madurar nuestra app.

**Adapters**: Consideremos la idea de tener un SUB-LAYER dentro de infraestructura, Es como tu app interactua con el mundo. Adapters tienen relación con Adapter Pattern, ya que envuelve la comunicación con un I/O device.
Ej: GUI controllers, Loggers, Monitors, Email/SMS, API Gateways, REST controllers.

Los adaptadores, se suponen que son ligeros. Ellos solo deberían contener data-conversion, error handling, y validación de reglas sintácticas. NUNCA coloques business logic en adaptadores.



**Use cases and entities**: Volviendo al dominio, podemos separar un poco más.

**Casos de uso** son las piezas funcionales que mapea las historias de usuario en código, son la razón para crear la app.
Representan user-driven operations. (View debts, Checkout cart). Por lo tanto su nombre debe empezar con un verbo.

- Un caso de uso puede ser una query, si queremos un output
- Command si queremos cambiar el estado, no devuelve valor

**Entidades** Son objetos de negocio, estos reflejan los conceptos que tu app maneja. (Account, Deal, Movie, Debts). Es un error pensar que las entidades no tiene lógica. Si tiene relacionada a ellas.
Tampoco la confundas con DTO. Que solo transportan información y no contienen lógica.

Entidades, no dependen de nada. No son database tables o GUI conceptos.


Dominio puede contener otras cosas, ValueObjects, Eventos

- Stage 3: Adapter son los mediadores entre el mundo exterior y el dominio.
Categoricemos en:

* **Primary Adapters**: Son "Entry points" (delivery mechanisms, controllers) de tu app. Son "driving adapters"(adaptadores de conducción) ya que activan el código de dominio.
Ex: API Servers, GUI controllers

* **Secondary Adapters**: Son puntos salientes de su aplicación, que se conectan a secondary actos ("agentes externos"), Son "driven adapters"(adaptadores de controlados): el dominio desencadena su uso.
Ex: API Clients, System clock, ID generators, Database, loggers, monitors.

Step 4: Ports and dependency rule
Recordemos, Lo de adentro no depende del exterior
En otras palabras el Dominio/Core no pueden depender de ningún adaptador

Cómo podemos resolver las posibles dependencias de los casos de uso con adapters
- Definir interfaces e inyectar concrete implementations
- Inyectar compatible lambdas ???
- Inyectar compatible objects

La primera opción:
Esto define una lenguaje de comunicación con el adaptador. Esto se conoce como **puerto**.
En términos prácticos, eso es una interfaz, los tipos de entrada y salida(DTO) y posibles errores.
Dado que los adaptadores pertenecen a la infraestructura y los puertos los abstraen, lo que los convierte en parte del dominio.

Don’t confuse the flow of control with the dependency rule: the flow of control describes how the program flows: user → device (e.g. browser)→ input port (e.g. web handler) → use case → output port (e.g. repository)→ device (e.g. database) → and back to the user. The dependency rule states that dependencies should point inwards.

Stage 5: error handling
https://medium.com/codex/pragmatic-exception-handling-3831f7ce0980


Stage 6: testing
Do testing.

- a use case in isolation (focusing on variations);
- an adapter with some deployed testing service (e.g. testing a data repository with a testing database, testing a REST client);
- a use case through an adapter;
- a user task (full-stack), using a primary adapter, passing through the domain, and using the necessary secondary adapters.

Stage 7: requests and responses
Podemos usar valores primitivos para llamar casos de uso y otras cosas.
Sin embargo, esa opción puede convertirse en un problema. 
Una solución es crear [PARAMETER OBJECT](https://wiki.c2.com/?ParameterObject)

Stage 8: composition root
Que tipo de carpetas usamos para ordenar