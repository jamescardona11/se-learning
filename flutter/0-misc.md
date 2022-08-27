---
Versión: v1.1
Última actualización: 25-may-2022
Última persona que actualizo: James Cardona
Equipo actual: James Cardona
Último cambio: Ortografía y algunas cosas varias
---


# Propuestas para Tokenpad Flutter

Es importante que vean que algunos puntos acá son solo sugerencias personales y otras son obligatorios.
Este archivo está abierto a todos para que puedan comentar posibles cosas que les parezca.

Estamos adecuando diferentes cosas, adicional todo está funcionando, entonces no cambiaré lo que funcione, voy a aportar mucho en la UI que es una parte que tiene áreas de mejora.

## Arquitectura

Por el momento la arquitectura no tiene cambios. Lo que si va a pasar es que vamos a evaluar como reducir el tiempo de desarrollo y como mejorar la productividad. Al momento de escribir esto el proyecto es grande y no tenemos muchos desarrolladores.

Una de mis propuestas es reducir las pruebas unitarias(**no está aprobada**), importante si se da algún cambio, esto **únicamente** será puntos no críticos y adicional quedaremos con deuda técnica en los lugares donde no se hagan.
**JAMAS** se quitarán del dominio.
Esto último estará siendo evaluado con JuanQuintero y JuanDavid.


## Flujo de trabajo

El flujo de trabajo seguirá siendo el mismo con unos pequeños matices.
Objetivo: 
- Reducir las ramas de larga duración.
- Reducir los PR
- Reducir el tiempo de desarrollo
- Crear tareas más atómicas.

¿Cómo lo vamos a hacer? **propuesta**
- Vamos a remover el 90% de los PR por el momento de JuanDavid y JamesCardona
- Jesús y Martello seguirán teniendo PR hasta que dominen flutter
- Vamos a hacer la reunión daily más efectiva
- Vamos a intentar hacer features más cortas. Evitando conflictos de merge.
- Vamos a descargar cambios constantemente de la rama pre-dev
- Vamos a colocar story points de las tareas
- Los test van a tener una sub-tarea

Para poder cumplir con tener tareas atómicas dejo está pequeña estructura para hacer buenos commits, si luego toca deshacer algo será más fácil encontrarlo:
[Referencia](https://udacity.github.io/git-styleguide/)
```
fix: fix the animation for drawer

[X] Add new flag to control the state when is open
[X] Test on android and iOS
[ ] is pending interact with ....

TOK-1766 Jira

```




## Flutter - UI

### 1) ¿Cómo organizar el código?

Esto hace referencia al contenido de un archivo de código, pero es el _sentido común_ la herramienta para organizar código. ¿qué sería más fácil para todos? ¿Mi "yo" del futuro se acordará de esto?

Lo primero es establecer unos objetivos generales de porque vamos a mejorar el orden en nuestro código, estos objetivos son:
- **Código limpio:**
    La verdad es difícil decirte que es un código limpio cuando hay infinidad de casos y soluciones. Pero algunas cosas que pueden ayudar:
    1. Nombres descriptivos para variables y/o métodos/funciones
    2. Separa partes del código con la tecla 'enter' **(opcional)**
    3. Los métodos/funciones deberían solo tener máximo 7 líneas de contenido(no cuentan los enter) **(opcional)**
    4. Si requieres dividir un método/funciones en varias partes, solo deja una de estas 
    pública
    5. Si es necesario deja comentarios en las funciones divididas para entender que hacen **(opcional)**



- **Orden de los métodos y funciones**
    Algo similar en este punto, el orden de los métodos es tema de debate.
    1. Variables deben ir al inicio del código, debajo del constructor.
    2. Los métodos/funciones públicas deben ir después del constructor.
    3. Los widget no deben tener métodos públicos.
        * El estado de un widget puede tener métodos públicos(Porque el estado es un 'widget' privado)
    4. El orden para los métodos en un widget con estado debe ser:
        * initState, build, dispose
        ```dart
        // Solo usar si requiere
        @override
        void initState() {
          super.initState();
        }

        @override
        Widget build(BuildContext context) {
          return ...
        }
        
        // Solo usar si requiere
        @override
        void dispose() {
          // DISPOSE HERE
          super.dispose();
        }

        /// Métodos
        ```
    5. El orden de los métodos/funciones privadas no importan, desde que estén después del último métodos/funciones público
    6. Si es necesario, deja comentarios en las funciones divididas para entender que hacen **(opcional)**

### 2) ¿Uso del linter?

¿Qué es un linter?, simplemente son reglas que nos ayudaran a mantener un código más limpio, ordenado y son recomendaciones del mismo lenguaje o de personas con mucho conocimiento.

Al momento de escribir esta guía hay más de 2000 errores con el linter actual. Es poco práctico usar un linter y no seguirlo. Por eso yo voy a velar porque esos errores se eliminen de la app. Nada de eso va a hacer que nuestro código corra mejor, o que la app no presente un error grave. Simplemente son reglas.

Por el momento vamos a usar este [linter](https://pub.dev/packages/flutter_lints). Es recomendado por flutter y me gusta.
Acá puedes encontrar la referencia para las [reglas](https://dart.dev/tools/linter-rules) 

PD: Después de pasarme de linter los errores pasaron a cerca de 1000.

Objetivo: Tener 0 errores de linter. Cuando este objetivo se alcance no aceptaré PR con errores de linter.


### 3 ¿Cuándo hacer comentarios?

Los comentarios son para dos cosas, uno prevenir que mi memoria no me ayude en el futuro. Ayudar a los **compañeros** que entiendan parte de lo que hace un bloque de código.

La **recomendación** es hacer comentarios **cuando** una bloque de código es complejo de entender.
Cuando quiero mostrar una solución o la razón de porque se hace de una forma algo.


PD: En los módulos: domain, data_source, presentation, infrastructure es **obligatorio** comentar los métodos públicos


### 4 ¿Cómo dividir los widgets?

Hay un dicho que dice, "divide y vencerás" entonces widgets donde el método build tiene 150 líneas de código son difíciles de leer, interpretar y modificar.
Pero te voy a dejar algunos tips útiles que he usado para mejorar mis widget(esto es opinión personas de @jamescardona11 puede no estar de acuerdo y todo ok)

1. Baso mi pensamiento para construir widgets en esto: "flutter es un framework de composición"
2. Trato de hacer el widget primero antes de dividir si no tengo claro muchas cosas
3. Separo componentes comunes en un widget aparte
    - Ex: una card con un posible icono
    - Ex: Una decoración
4. Separo componentes que hacen parte del widget, pero que en sí son muy complejos
5. Decoraciones, estilos, medidas, cosas que hacen relleno(el widget se ve más grande) y no aportan mucho las coloco en un 'getter' privado. Esto no siempre se tiene que hacer, de hecho se hace poco, una guía será cuando el widget ha crecido en tamaño (+150 líneas) que esto está "estorbando". 
Lo siguiente son algunos ejemplos de lo que divido.

    ```dart
      OutlineInputBorder get _outlineInputBorder =>OutlineInputBorder(
        borderRadius: bRadius12,
        borderSide: border2.copyWith(color: primary),
      )

      DecoratedBox get _defaultDecorated => DecoratedBox(
        decoration: BoxDecoration(
          color: primary,
          borderRadius: bRadius16,
      )
    ```
    Recuerda que flutter es un framework de composición, puedes leer algunas cosas que me ha servido en estos dos post [p1](https://medium.com/flutter-community/the-layer-cake-widgets-elements-renderobjects-7644c3142401), [p2](https://stackoverflow.com/questions/53234825/what-is-the-difference-between-functions-and-classes-to-create-reusable-widgets)


6. No todos los widgets que separo me los llevo para un archivo, algunas veces los dejo en el mismo archivo. Coloco esos widget de forma privada.
7. El import hacia el widget principal lo hago por medio de la estrategia **barrel export**
    ```dart
        export 'add_wallet_text.dart';
        export 'arrow_title_widget.dart';
        export 'base_app_bar_widget.dart';
        export 'close_appbar_button.dart';
        export 'default_title_text.dart';
        export 'reset_or_close_widget.dart';
        export 'appbar_utils.dart';

    ```

### ¿Cómo estructurar las carpetas en UI?

Esto es muy de perspectiva pero, acá dejo lo que me ha funcionado.(@jamescardona11)
1. no se vuelve hacer algo como lo siguiente: 
Es una buena forma de ordenar pero, el proyecto es demasiado grande que ya es difícil sacarle el beneficio.


```dart
      library home_view;

      /// [third-packages]
      import 'package:animations/animations.dart';
      import 'package:auto_route/auto_route.dart';
      import 'package:domain/domain.dart';
      import 'package:easy_localization/easy_localization.dart';

      /// [flutter-packages]
      import 'package:flutter/material.dart';
      import 'package:get/get_instance/src/bindings_interface.dart';
      import 'package:get/instance_manager.dart';
      import 'package:get/state_manager.dart';
      import 'package:provider/provider.dart';
      import 'package:tokenpad/business_logic/services/services.dart';

      /// [app-packages]
      import 'package:tokenpad/core/base_controller.dart';
      import 'package:tokenpad/di/di.dart';
      import 'package:tokenpad/ui/common/providers/appbar_animation_provider.dart';
      import 'package:tokenpad/ui/common/providers/bottom_bar_provider.dart';
      import 'package:tokenpad/ui/pages/consolidated_tokens/tokens_view/tokens_screen.dart';
      import 'package:tokenpad/ui/pages/portfolio/default_portfolio_view/portfolio_screen.dart';
      import 'package:tokenpad/ui/pages/settings/settings_main/settings_main.dart';
      import 'package:tokenpad/ui/widgets/widgets.dart';

      import '../../../navigator/imp/pad_routes_definitions.gr.dart';
      import '../../widgets/demo_exit_button.dart';
      import '../opportunities/default_opportunities_view/opportunities_screen.dart';

      /// [lib-parts]
      part 'binding.dart';
      part 'controller.dart';
      part 'view.dart';

```

2. El orden de las carpetas van a cambiar. Esto es un ejemplo:
Busco que sea más descriptivo lo que vamos a encontrar en cada carpeta (**feature**)
    ```
    --ui/
    ----common/
    -------providers/
    -------widgets/
    -------ui_models/
    ----pages/
    -------home/
    ----------widgets/ (si existen otros widgets)
    ----------home_layout.dart
    ----------home_page.dart
    ----utils
    ```