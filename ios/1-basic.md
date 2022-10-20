# APRENDE a PROGRAMAR SWIFT
(https://www.youtube.com/watch?v=Dk1wLbTh4Fo)

- var => variables
- let => constantes
- typealias => sinonimo como typedef
- tuples => (x, y)

### enum
```
enum CustomOptional<Int>{
  case none
  case some(Int)
}

let a = CustomOptional<Int>.none
let myInt: CustomOptional<Int> = .none

```

### interpolación
\()

### Colecciones
array: <String>()
array: [String]()
Set: Set<V>()\
dictionary/Map: Dictionary<K, V>, [K:V]()


### funciones
func myFunction(x:Int)
func myFunction(x:Int)-> Int{}
valores por default => func myFunction(x:Int = 1)

#### Closures
let c = {
  (param) -> return-type **in**
}


### OOP
struct -> estructuras
```
  struct Square {
    var ancho = 10
    var alto = 10
  }

  var s = square()
```

```
  class Car {

  }
```

### manejo de errores
do, catch

### extensiones
extension Double {

}

### protocolos es como las interface/ abstract class

### inout es & referencia de c++

### ARC
Garbage collector
Swift lleva un contador interno de las instancias
Memory leak: cuando hay referencias circulares
weak => Palabra reservada para indiciar que la referencia es circular y débil

### Control de acceso
open, public => desde cualquier parte
internal => dentro del modulo/app
fileprivate => solo dentro el fichero
private => solo al contexto