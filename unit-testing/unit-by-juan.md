# Unit Testing

### ¿Qué es?
-> Prueba automatizada y **controlada** a una unidad de trabajo

### Unidad de trabajo
-> Parte del sistema que será probada
  -  Función
  -  Método de un objeto
  -  Sistema completo

->  Suma de acciones que tiene invocación de un punto de entrada y un resultado final(de esas acciones).


### Punto de entrada
Firma usada para iniciar el proceso en la **unidad de trabajo** 

### Punto de salida
Resultado generado por la **unidad de trabajo**
  - Valor de retorno
  - Cambio de estado verificable (Efecto secundario)
  - Llamada a dependencia externa


### ¿Cómo debe ser?
- Muy rápida
- Todo debe correr en RAM
- Legible, replicable y confiable
- Solo debe verificar un punto de salida


### Estructura de AAA

-> Arrange (preparar)
-> Act (invocar el punto de entrada)
-> Assert (verificar punto de salida)


### ¿Cómo nombrar? USE
-> Unit of work under test (unidad de trabajo a probar)
-> Scenario (scenario o parámetros enviados a la unidad)
-> Expect behavior (comportamiento esperado)


### Dependencias externas
Módulos externos a una unidad de trabajo requeridos para su funcionamiento.
Puede estar bajo nuestro control, o no.

Pueden ser: 
- De salida: punto de salida (servicio de login, guardar en DB, notificar webhook)
- De entrada: leemos información (db, externo)

#### Dobles de Prueba
- Objetos falsos que simulan dependencias requeridas por una unidad de trabajo
- Es muy importante saber que tipo de dependencia

  ###  STUB
   -  Simular dependencias de entrada
   -  Como son de entrada, NO SON DE SALIDA
   -  Como no son de salida, NO SE VALIDA SU COMPORTAMIENTO (No assert)

  ###  MOCK
   -  SOLO DE SALIDA
   -  Como solo debe haber un único punto de salida por prueba, SOLO UN MOCK POR PRUEBA


### STUBS
**Simular datos específicos**
Podemos simular cualquier escenario

- Valor muy especifico: Fecha de un día
- Error: Simular un error
- Casos extremos
- Múltiples stubs por prueba

### MOCKS
**Simular sistemas externos**
Podemos simular puntos de salida

- Servidor externo
- Librería externa
- Permite mantener todo en RAM


### Inversión de control

La unidad de trabajo NO debe crear o tener acceso directo a las dependencias.
Estas deben ser obtenidas desde un agente externo.
Esto permite que se pueda cambiar a voluntad.(Tener el poder)

### ¿Por qué hace pruebas?
- Brinda confianza a la hora de hacer cambios
- No requiere un gasto económico ni de tiempo significativo y su beneficio es infinito
- Solo cambia cuando la solución cambia
- Permite descubrir posibles falencias en el diseño de software

### TIPS:
- Solo API Pública
- Resistente (Falsos positivos y falsos negativos)
- Aisladas (Una prueba no debe depender de otra)
- Sin lógica (No tener lógica que deba ser probada)
- Dominio (Debe tener cobertura cercana al 100%)
  
  