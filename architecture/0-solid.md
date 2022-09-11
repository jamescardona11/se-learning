# SOLID

## Principios SOLID - 5 + 1 
REF1 = https://www.youtube.com/watch?v=E_mSr-VFd3g

un conjunto de reglas a programar software de calidad.

* S: Single responsibility principle o Principio de responsabilidad única
* O: Open/closed principle o Principio de abierto/cerrado
* L: Liskov substitution principle o Principio de sustitución de Liskov
* I: Interface segregation principle o Principio de segregación de la interfaz
* D: Dependency inversion principle o Principio de inversión de dependencia

Beneficios
1- Software más flexible, ya que mejora la cohesión y el acoplamiento
Las clases puedan trabajar de forma independiente y cuando modifiquemos una clase esta no afecte a otra

2- Te van hacer entender mejor las arquitecturas

3- Los principios SOLID simplifican el testing

Los principios SOLID estan relacionados entre si, un principio no se puede existir sin los otros
* A veces cuando cumples un principio te ves en la necesidad de cumplir otro
* A veces pasa lo contrario a lo anterior, incumples uno al implementar otro

Aceptar que no siempre vamos a cumplir todos los principios en nuestro código



#### * S:
Una entidad/clase/modulo debería tener una responsabilidad única.
-> "Una única razón para cambiar" X
-> "Se cumple si hace una única cosa"

Tips: Cuando se incumple
* Cuando en una clase están involucradas dos capas de la arq
* Una clase tiene muchos métodos públicos (puedes separarlo)
* Numero de imports
* Mucho hacer test
* Si cada vez que se escribe algo nuevo esa clase se ve afectada, algo pasa
* Muchas lineas

#### * O:
Una Entidad/clase/modulo debería estar abierta a extensión pero cerrada a modificación
-> "Poder extender el comportamiento de esa clase sin modificar su código"
-> Se resuelve en muchos casos: Usando polimorfimos
* Delegamos ciertas responsabilidades en objetos que utiliza

A veces la complejidad que añade no compensa
- Protegernos en partes del código donde es propenso a cambiar mucho

#### * L:
Si tenemos clases hijas y en una parte estamos usando la clase padre, entonces yo puedo sustituir la clase padre con un hijo y debería seguir funcionando tal cual

Tips: Cuando se incumple
- Creas una clase que extiende de otra y un método que extiende no tiene sentido, si necesitas dejarlo vacio o lanzas una excepción probablemente no estas cumpliendo con el principio de Liskov

"Si parece un pato, hace como un pato pero necesita pilas probablemente estas haciendo la abstracción incorrecta"

- Si algunos test valen para la clase padre, pero no valen para clase hija estas violando el principio

Ejemplo:
Animal que salta y caminan pero los Elefante no saltan


Elegir abstracciones correctas para resolver
Pero otra forma de hacerlo es usar composición

#### * I:
"Una clase no debería depender de métodos que no usa"
-> Si es necesario dividir la interfaz en más pequeñas para que puedan ajustarse
-> Nos ayuda a desacoplar

"Las FAT interfaces, que una clase hija tenga cosas que no sabe que hacer"

Segregar interfaces
Puedes implementar el patrón de diseño adapter para las FAT interfaces

#### * D:
Que el código que tenemos no dependa de factores externos
"Las clases de alto nivel no deberían depender de las clases de bajo nivel, ambas deberían depender de abstracciones" y "Las abstracciones no deberían depender de los detalles, sino  que los detalles deberían depender de los detalles"

El código sufre mucho acoplamiento
Muy complicado de hacer test

Tips: Cuando se incumple
Cualquier instanciación de clases complejas o módulos es una violación del principio

-> Injector de dependecias
-> Invertirlas, pasarlas por constructor


#### Regla personal de Antonio Leiva (LEY de DEMETER)
- Encadenamiento de dependencias (Acoplamiento)

Mecanismo detección de acoplamiento
"Un objeto no debería conocer el interior de un objeto con el que interactua" (acceder a propiedades internas)
-> Esto es más una alarma


"La sobre-ingeniería es tan mala cómo la carencia de ella"