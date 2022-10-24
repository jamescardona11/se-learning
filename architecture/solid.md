# SOLID

BUENA REF
https://github.com/LSIND/SOLID-principles


![](images/solid_gola.jpeg)

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
"Las clases de alto nivel no deberían depender de las clases de bajo nivel, ambas deberían depender de abstracciones" y "Las abstracciones no deberían depender de los detalles, sino  que los detalles deberían depender de los abstracciones"

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


## TIP SUELTO
Aprendo primero OPEN CLOSE ¿Por qué partimos tanto?
Liskov, asegura que lo polimorfico cumple OpenClose
Cuando ves Liskov, ves interfaces


REF Adicional
https://www.youtube.com/watch?v=2X50sKeBAcQ


## PORQUE NO USO SOLID
http://qualityisspeed.blogspot.com/2014/08/why-i-dont-teach-solid.html
Si pudiera usar una palabra para representar estos problemas, sería ininteligible . Los desarrolladores (incluido yo mismo) que aplican SOLID con frecuencia producen bases de código que son ininteligibles. Estas bases de código SOLID tienen bajo acoplamiento. Y son comprobables. Pero son ininteligibles. Y a menudo no tan adaptable como esperaban los desarrolladores.


Contraparte: Elegir el menor de los males
https://stackoverflow.com/questions/2997965/are-solid-principles-really-solid

Escoge tus batallas
Cada vez que introduce una nueva técnica de ingeniería de software, debe considerar qué obtengo y cuánto cuesta

## Why the design patterns fails
Objetivos de SOLID
Uno para hacer que el código sea comprensible.
Uno para hacer el código flexible
Uno para hacer que el código sea mantenible

¿Recuerda las pautas de codificación de los grandes proyectos de código abierto? Cómo lo único real que los unifica es que son sorprendentemente relajados para proyectos con cientos o miles de desarrolladores trabajando en el mismo monolito.

Prohiben y recomiendan cosas, pero no te dicen "cómo" hacer cosas... porque si supieran el "cómo" ese código ya estaría allí, el trabajo del programador (y de cualquier ingeniero en realidad) es averiguar fuera el cómo.

Tal vez estoy predispuesto a que no me gusten los principios de diseño. Ciertamente no creo que esto sea un derribo definitivo del concepto, es más una visión que trata de explicar por qué el concepto podría ser malo, ya que los principios de diseño son una de esas cosas que siempre "suenan bien" pero en realidad nunca veo funcionan bien en la práctica.

Los patrones deben surgir, no deben crearse. Si vemos un patrón que surge mucho en su dominio, agréguelo a las bibliotecas y la jerga específicas del dominio. Si vemos un patrón que surge en todas partes, agréguelo a nuestros lenguajes y bibliotecas estándar.

Einstein dijo algo así como: "Todo debe hacerse lo más simple posible, pero no más simple". ¡Ese es un muy buen principio de ingeniería de software!

## SOLID MODERNO
REF = https://stackoverflow.blog/2021/11/01/why-solid-principles-are-still-the-foundation-for-modern-software-architecture/

¿Qué no ha cambiado?
- El código es escrito y modificado por personas. El código se escribe una vez y se lee muchas, muchas veces. Siempre existirá la necesidad de un código bien documentado, particularmente API bien documentadas, ya sean internas o externas.

- El código está organizado en módulos . En algunos idiomas, estas son clases. En otros, pueden ser archivos fuente individuales. En JavaScript, pueden ser objetos exportados. Independientemente, existe alguna forma de separar y organizar el código en unidades delimitadas distintas. Por lo tanto, siempre será necesario decidir cuál es la mejor forma de agrupar el código.

- El código puede ser interno o externo. Parte del código está escrito para que lo use usted mismo o su equipo. Otro código está escrito para ser utilizado por otros equipos o incluso por clientes externos (a través de una API). Esto significa que debe haber alguna forma de decidir qué código es "visible" y qué está "oculto".

Modulo = clase o grupo de código

### SOLID MODERNO

#### * S: 
Definición original: "Nunca debe haber más de una razón para que una clase cambie".
**Nueva definición:** “Cada módulo debe hacer una cosa y hacerlo bien”.
Este principio esta relacionado con el tema de alta cohesion

#### * O: 
La razón para cerrar las clases para la modificación es que es posible que no confiemos en que todos los consumidores intermedios entiendan todo el código "privado" que usamos para que nuestra función funcione, y queremos protegerlo de manos no calificadas.


Definición original: "Las entidades de software deben estar abiertas para la extensión, pero cerradas para la modificación".

**Nueva definición:** "Debería poder usar y agregar a un módulo sin tener que volver a escribirlo".

#### * L: 
Definición original: "Si S es un subtipo de T, entonces los objetos de tipo T pueden reemplazarse con objetos de tipo S sin alterar ninguna de las propiedades deseables del programa".
**Nueva definición:** debería poder sustituir una cosa por otra si se declara que esas cosas se comportan de la misma manera.

#### * I: 
Definición original: "Muchas interfaces específicas del cliente son mejores que una interfaz de propósito general".
**Nueva definición:** “No muestres a tus **clientes** más de lo que necesitan ver”.



#### * D: 
Definición original: “Depende de abstracciones, no de concreciones”.
**Nueva definición:** “Depende de abstracciones, no de concreciones”.

Para reafirmar "SÓLIDO moderno" una vez más:

- No sorprenda a las personas que leen su código.
- No sorprenda a las personas que usan su código.
- No abrumes a las personas que leen tu código.
- Use límites sensatos para su código.
- Use el nivel correcto de acoplamiento: mantenga juntas las cosas que pertenecen juntas y manténgalas separadas si pertenecen separadas.


## Conoce SOLID y diseña software de calidad
REF https://www.kabel.es/conoce-solid-y-disena-software-de-calidad/
#### * S: 
Junto a la definición original, muchas personas interpretan: Cada clase dentro de su código debería tener una única tarea que realizar.

Pero más que una sola tarea, es única responsabilidad, entendiendo responsabilidad como un conjunto de tareas relacionadas

#### * L: 
Para aplicar este principio simplemente hay que preguntarse: ¿Es siempre un?

Un empleado siempre es programador:  NO
Un empleado siempre es director:     NO
Un director siempre es empleado:     SI
Un programador siempre es empleado:  SI

#### * I: 
El principio de segregación de la interface nos indica que no se debe implementar interfaces con métodos que no se usan.

Este principio nos está recomendando que no debemos definir interfaces con muchos métodos sino con pocos y muy relacionados.


## SOLID principles can go wrong
REF = https://medium.com/@arpytoth/solid-principles-can-go-wrong-cc0bab8ec660

Sin experiencia(o poca) esto puede ser un desastre,

Como puede ver, el código es realmente agradable, tiene todas las cosas sofisticadas, herencia, patrón de fábrica, etc. El autor probablemente esté muy orgulloso de su diseño SÓLIDO.

**TIP** Bueno, creo que esto es una basura sobredimensionada 💩. Creo que siempre debemos implementar lo más simple que funcione, nada más y nada menos.


----
## Wrong Solid
https://www.entropywins.wtf/blog/2017/02/17/why-every-single-argument-of-dan-north-is-wrong/



## Putting SOLID in Perspective
Muchos han puesto solid como "SOLID as rules"

Critica Externa: https://dannorth.net/2021/03/16/cupid-the-back-story/

describiría los principios SOLID como una heurística que a veces resulta útil .

Las heurísticas son métodos o estrategias que a menudo conducen a la solución de un problema pero no se garantiza que tengan éxito .

**Principio de responsabilidad única (SRP)**
Subjetivo

**Principio abierto cerrado (OCP):**
demás, diría que OCP aparece más o menos mucho tiempo como "capacidad de conexión", que es una espada de doble filo que ha ayudado y obstaculizado a cualquiera que haya sido desarrollador durante un período de tiempo prolongado.

**Principio de sustitución de Liskov (LSP):**
Una lectura casual de eso solo lo llevará a una reformulación del polimorfismo , lo cual está bien, supongo, pero en realidad no nos ayuda necesariamente a escribir un mejor código.

**Principio de segregación de interfaces (ISP):**
Veo que el ISP surge mucho más a menudo cuando se crea código de infraestructura, pero ocasionalmente en otro código donde es valioso separar la interfaz para mutar un objeto y una interfaz separada para los consumidores de datos.

**Principio de inversión de dependencia :**



Para resumir los principios y su utilidad:

SRP : la separación de preocupaciones es importante en el código, pero el SRP está demasiado vagamente redactado por sí mismo para ser de gran ayuda.
O CP: ocasionalmente es útil para pensar en una arquitectura prevista o ajustar una arquitectura que está resultando difícil de cambiar. No creo que realmente surja con demasiada frecuencia.
L SP: las abstracciones con fugas pueden ser dañinas, por lo que no tengo ningún argumento aquí, pero como todas las cosas, el impacto es bastante variable y no necesariamente convertiría esto en una regla estricta.
I SP: importante aquí y allá si está creando API para otros desarrolladores, pero probablemente no se aplique a diario.
DIP : exagerado, y probablemente causa un poco más de daño que bien a las personas que aplican esto en exceso




## CUPID
Los principios son como las reglas: o se cumple o no se cumple. Esto da lugar a **“conjuntos acotados”** de seguidores y ejecutores de reglas en lugar de “conjuntos centrados” de personas con valores compartidos.

Empece a pensar en propiedades.
Las propiedades definen un objetivo o centro hacia el que moverse. Su código solo está más cerca o más lejos del centro, y siempre hay una dirección de viaje clara. Puede usar propiedades como lente o filtro para evaluar su código y puede decidir cuáles abordar a continuación

### Propiedades de las propiedades
- articulate (entender)
- Assess (evaluar)
- Adopt (adoptar)

Las propiedades deben leerse de la pespectiva humana no del código.
CUPID se trata de como se siente trabajar con código, 

### Composable
- El software es fácil de usar, se usa y se vuelve a usar.
- **Small surface area** Código pequeño es más fácil de llevar, Hay un punto dulce de cohesión "perfecta" entre fragmentado e hinchado.
- **Intention-revealing** El código revelador de intenciones es fácil de descubrir y de evaluar.
- **Minimal dependencies** El código con dependencias mínimas le da menos de qué preocuparse y reduce la probabilidad de incompatibilidades de versión o biblioteca


### Unix philosophy
La filosofía de Unix dice que hay que escribir [componentes] que funcionen bien juntos, descritos en la propiedad Composability anterior, y que hagan una cosa y la hagan bien .

#### Propósito único vs responsabilidad única 
A primera vista, esto parece el principio de responsabilidad única (SRP), y para ciertas interpretaciones de SRP hay cierta superposición

Pero “hacer una cosa bien” es una perspectiva de afuera hacia adentro; es la propiedad de tener un propósito específico, bien definido y comprensivo. SRP es una perspectiva de adentro hacia afuera: se trata de la organización del código.



### Predictable
El código debe hacer lo que parece que hace, consistente y confiablemente, sin sorpresas desagradables. Debería ser no solo posible sino fácil de confirmar esto. En este sentido, la previsibilidad es una generalización de la comprobabilidad.

**Behaves as expected**
El código predecible debe comportarse como se espera , y debe ser determinista y observable .

**Deterministic** 
El determinismo es un tema amplio. A los efectos de la previsibilidad, el código determinista debe ser robusto , fiable y resistente .

Robustez es la amplitud o integridad de las situaciones que cubrimos. Las limitaciones y los casos límite deberían ser obvios.
Confiabilidad es actuar como se espera en las situaciones que cubrimos. Deberíamos obtener los mismos resultados cada vez.
La resiliencia es qué tan bien manejamos situaciones que no cubrimos; Perturbaciones inesperadas en las entradas o en el entorno operativo.

**Observable**
El código debe ser observable en el sentido de la teoría de control : podemos inferir su estado interno a partir de sus salidas


### Idiomatic
El mayor rasgo de programación es la empatía; empatía por tus usuarios; empatía por la gente de apoyo; empatía por los futuros desarrolladores; cualquiera de los cuales puede ser usted en el futuro. **Escribir “código que los humanos puedan entender” significa escribir código para otra persona**. Esto es lo que significa el código idiomático.


### Domain-based structure
Escribimos software para satisfacer una necesidad. Esto puede ser específico y situacional, o genérico y de largo alcance. Cualquiera que sea su propósito, el código debe transmitir lo que está haciendo en el lenguaje del dominio del problema, para minimizar la distancia cognitiva entre lo que escribe y lo que hace. Esto es más que “usar las palabras correctas”.


**Límites basados ​​en dominios**
Cuando estructuramos el código de la manera que queremos y lo nombramos de la manera que queremos, los límites del módulo se convierten en límites del dominio y la implementación se vuelve sencilla. 

- Composable – “plays well with others”
- Unix – “does one thing well”
- Predictable – “does what you expect”
- Idiomatic – “feels natural”
- Domain-based – “the solution domain models the problem domain in language and structure”


## SOLID VS CUPID
SOLID tiene en mente que los productos de software evolucionan. Aplicando SOLID podemos asegurar que en el futuro updates van a ser menos dolorosos.

CUPID has the same basic philosophy as SOLID: when coding, think about the people who will come after you.

Una diferencia es:
SOLID es un conjunto de principios usados durante el desarrollo. FOCUS ON PROCESS
CUPID describe las propiedades que un código finalizado debe tener. FOCUS ON RESULT



BUENA REF
**https://itnext.io/solid-principles-sketches-a38865e771f0
https://takeoffandroid.github.io/solid-principles-flutter/
https://medium.com/flutter-community/s-o-l-i-d-the-first-5-principles-of-object-oriented-design-with-dart-f31d62135b7e
https://blog.ndepend.com/defense-solid-principles/


Desventajas
https://dev.to/victorpinzon1988eng/solid-single-responsibility-principle-48an