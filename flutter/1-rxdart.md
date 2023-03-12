# Reactive DART

[REF](https://www.youtube.com/watch?v=xBFWMYmm9ro)

SINK is only write
STREAM: is only read
BehaviorSubject: its both because internal use StreamController


Observable: Stream
Subject: StreamController

PublishSubject: StreamController con broadcastStream
BehaviorSubject: StreamController con broadcastStream, que conserva el último estado que se emitio y lo emite como primer elemento a los nuevos listeners



- Distinct: solo cuando sean valores diferentes
- debounceTime: espera un momento para transmitir mensajes
- switchMap: Convierte items into stream
  Cada vez que tenemos un nuevo valor las subscripciones anteriores se cierran
  sincrono
- Rx.fromCallable: Convierte un future into Stream
- delay: add a delay
- map: mapea los elementos
- startWith: colocar un evento al inicio de una stream

--- Step2
merge: Mezcla dos mensajes en observables en uno solo
combineLatest: combina los últimos mensajes de un observable en uno solo
concat: cancatena
take: take some values

flatmap vs switchmap = el flatmap no cierra las subscripciones anteriores

3:29