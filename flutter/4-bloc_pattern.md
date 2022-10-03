# BLoC Pattern

Business Logic Component, consiste en separar la lógica de la interfaz.
La idea es usar algo que reciba 'eventos' y se procesen a estados.

- Logica de negocio agnostica
- Entradas Sinks
- Salidas Streams
- Dependencias inyectables
  
UI:
- Cada page tiene un bloc
- Los componente deben enviar las entradas tal como son al BLoC
- Los componentes deben mostrar salidas lo más cerca del bloc

Stream: es una fuente de eventos
- Single subscriptions
- Broadcast subscriptions

StreamController, tiene sink y stream

-> 
Sink agregaremos eventos
Stream emitiremos estados

Observable:
Subject: