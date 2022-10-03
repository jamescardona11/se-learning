/// https://refactoring.guru/es/design-patterns/factory-method
/// Objetivo: Crear objetos de una superclase, usando subclases cambiar el tipo de objeto.
///
/// -> Clase que se puede reutilizar y usar de forma polimorfica
/// -> En vez de usar `new` para crear un tipo de objeto invoquemos una clase `Factory`
/// -> Los objetos devueltos por la clase `Factory` se denominan `Productos`
/// -> La clase creadora su principal responsabilidad no es crear puede tener alguna logica de negocio adicional
///
/// {`@Ejemplo`}
/// Vas a crear una app para hacer el transporte de mercancia
/// Creas la clase de transporte terrestre
///
/// `Problema1`: ¿Qué pasa quieres ampliar a transporte maritimo? R/ Ahora tu app depende(acoplada) mucho de la clase camion
/// `Problema2`: ¿Si más adelante queremos añadir otros tipos de transporte ?
///
/// Usemos Factory:
/// -> RandomEnemyFactory, DifficultyEnemyFactory
///
/// Cada vez que quiero implementar una nueva forma de creación de transporte solo basta con implementar `LogisticsFactory`
///

abstract class Transport {}

abstract class LogisticsFactory {
  Transport createTransport();
}

class RoadLogistics implements LogisticsFactory {
  @override
  Transport createTransport() {
    // TODO: implement createTransport
    throw UnimplementedError();
  }
}

class SeaLogistics implements LogisticsFactory {
  @override
  Transport createTransport() {
    // TODO: implement createTransport
    throw UnimplementedError();
  }
}

class TransportApp {
  void createDelivery(LogisticsFactory lFactory) {
    //Code

    final transport = lFactory.createTransport();

    //Code
  }
}
