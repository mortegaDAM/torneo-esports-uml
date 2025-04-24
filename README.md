# Sistema de Gestión de Torneos de eSports

## Autor

Mario Ortega Navarro
mortegaDAM@github.com

## Descripción del Proyecto y justificación del diseño

https://github.com/mortegaDAM/torneo-esports-uml

Este proyecto implementa un sistema de gestión de torneos de eSports, en concreto de Fifa. 


En el sistema que yo he modelado, he entendido como actores que interactúan con él a jugadores, entrenadores, espectadores, y el administrador del sistema. 
En esta plataforma existe el administrador, persona o personas encargadas de manejar la plataforma, actualizarla y realizar el mantenimiento de esta. Es el único con capacidad de gestión en él.
Esta plataforma podrá ser usada por tanto jugadores como entrenadores y espectadores. Estos tres actores utilizarán la plataforma para consultar y realizar el seguimiento de la competición. En el caso específico de los jugadores y entrenadores podrán realizar alguna operación extra como interactuar entre ellos solicitando entrar a un equipo etc.

## Diagrama de Casos de Uso

(diagrams/DiagramaCasosDeUso.png)

1. En el caso de los jugadores, las acciones que pueden realizar serían las de consultar los resultados de los partidos, tanto de sus equipos como de los demás equipos del torneo; consultar las clasificaciones, consultar la lista de equipos inscritos en el torneo y por supuesto también podrían solicitar entrar en otro equipo. A la hora de solicitar entrar en otro equipo este caso de uso esta relacionado con el de consultar los equipos inscritos, ya que para saber a que equipo quiere solicitar unirse hay que saber si está inscrito primero.
2. En el caso de los espectadores están los casos de uso de consultar los resultados, consultar las clasificaciones y consultar los equipos inscritos. Es un actor que tiene la participación en el sistema muy restringida, son simplemente casos de uso de consulta, nada más.
3. En el caso de los entrenadores, estos podrán aceptar o rechazar las solicitudes de los jugadores de unirse a sus equipos, solicitar el registro de un nuevo equipo, y por supuesto tendrán tambien acceso a consultar las clasificaciones, resultados y equipos inscritos.
4. Por último y como actor primario y más importante del sistema, está el administrador. Este actor puede realizar acciones diferentes a los demás actores, aunque alguna de ellas sea común a todos. El administrador podrá registrar en la plataforma los resultados de los partidos, podrá entregar los premios a los ganadores, consultando antes la clasificación final. También podrá realizar el primer sorteo de emparejamiento para los partidos, consultando previamente los equipos que hay inscritos. Será también el único actor capaz de crear torneos, verificando previamente si ya existe ese torneo o un torneo con ese nombre, y también inscribir equipos en esos torneo, consultando los equipos ya registrados y las solicitudes por parte de los entrenadores para este registro.

## Diagrama de Clases

(diagrams/DiagramaClases.png)

Para este diagrama tenemos la siguiente estructura y relaciones entre clases.

En primer lugar, una clase Torneo, con atributos como idTorneo(PK), y tres listas de equipo, partido, y clasificación. En cuanto a sus métodos, tenemos métodos como crearTorneo(), inscribirEquipo(), generar consultar o modificar la clasificación, e inscribirEquipo().

Relacionadas con esta clase principal Torneo, con una relación de composición, es decir, un torneo esta compuesto de: 

. Equipo: Cada torneo tiene muchos o varios equipos, y esta clase tiene atributo como idEquipo(PK), nombreEquipo, nombreEntrenador y una lista con sus jugadores. Sus métodos son mostrarJugadores(), añadir o eliminar un jugador, y cambiarEntrenador().
. Clasificación: Cada torneo tiene una clasificación única, con atributos como una lista con los equipos que la componen, los puntos de clasificación de cada equipo, y la posición de cada equipo. En cuanto a los métodos tenemos los de mostrar o modificar la clasificación, y sumar o restar puntos a los equipos dentro de ella, lo cual ira modificando su posición dentro de la clasificación.
. Partido: Cada torneo tiene muchos partidos, con los atributos de idPartido(PK), y luego guardaría la fecha, resultado y los equipos de cada uno de los partidos. Sus métodos serían registrarResultado(), asignarPuntos() o generarEstadisticas().
. Administrador: Cada torneo tiene un administrador, con solamente el atributo idAdmin(PK), el cual tendrá los métodos de consultar equipo, jugador y clasificación y entrega de premios.

Dentro de equipo, el equipo está compuesto de dos clases, que son:
. Jugador: con atributos como idJugador(PK) y nombreJugador. Sus métodos son solicitarEquipo y consultarEquipo().
. Entrenador: con atributos como idEntrenador(PK), y nombreEntrenador. Sus métodos son inscribirJugador(), solicitarJugador(), consultarEquipo(), y registrarEquipo().

A raíz de la clase partido, tenemos:
. Estadísticas: que guarda estadísticas de los partidos como los goles marcados por un equipo o un jugador, goles por partido, asistencias o tarjetas por jugador. Sus métodos son de consulta de estas estadísticas.
. Resultado: Clase con depencia de Partido, ya que si no hay partido no hay resultado. Esta clase guarda atributos como ganador o perdedor de este. Sus métodos son establecer ganador o perdedor, y asignarPuntos().

## Conclusiones 

Esta idea de plataforma podría desarrollarse de mil maneras diferentes, pudiendo ser todas ellas correctas. Además, podría ser también más amplia, pero como la he plasmado en los diagramas es como yo me la imagino si tuviera que realizarla. Creo que todos los actores importantes están plasmados, y que no hay casos de uso olvidados. 
Creo que estos diagramas otorgan una planificación y una claridad muy importante a la hora de introducirnos en la fase de desarrollo, en este caso de la plataforma, ya que te aporta una visión global de lo que quieres hacer y el fin al que quieres llegar. 
