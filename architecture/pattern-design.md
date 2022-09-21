# Patrones de diseño
https://www.youtube.com/watch?v=yKXNPWxWx9o&t=8s


Diseño es dibujar y dar forma(Forma correcta), que un conjunto de piezas estén enlazadas entre si.
Para hacer patrones diseños debo saber diseñar.
"Un proyecto de software es un problema de comunicación". Cliente con Product owners con project manager, developers con maquina, developers con ellos mismos.

Los lenguajes están orientados a que diseñes bien.

Patrón de diseño y patrón de arquitectura.
Es lo mismo con palabras diferentes, si lo ves con otra mirada tienes que contar cosas novedosas o no te escuchan.

Una clase solo con get y set, no tiene responsabilidad y cohesión.
ver en code smells -> Clase datos (anemicas)

La excusa de rendimiento para defender ***

### Patron de diseño
Es una forma metódica y probada de resolver un problema acotado/en un contexto sobre como manipular objetos.
Primero detectar/conocer el problema.

Patrones son bisagras y los patrones generalmente no vienen aislado.
Patrones hablan de como resolver problemas.



## CommandQuerySeparation

- Queries: Regresa valores y no hace cambios en el estado del sistema(No tiene side effects)
- Commands: Cambia el estado del sistema pero no retorna valores

Because the term 'command' is widely used in other contexts I prefer to refer to them as 'modifiers', you also see the term 'mutators'.

La idea realmente valiosa de este principio es que es extremadamente útil si puede separar claramente los métodos que cambian de estado de los que no lo hacen. 


## Parameter Object
Encapsular una llamada de una o muchas cosas en un objeto contenido.