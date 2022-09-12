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

* **Primary Adapters**: 