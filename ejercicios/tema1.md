# Ejercicios de autoevaluación tema 1 - Cloud Computing.

### 1- Buscar una aplicación de ejemplo, preferiblemente propia, y deducir qué patrón es el que usa. ¿Qué habría que hacer para evolucionar a un patrón tipo microservicios?
La aplicación que se encuentra en [jscoba/pycmic-server](https://github.com/jscoba/pycmic-server) usa una arquitectura por capas ya que es una aplicación de tipo cliente-servidor donde todo el código del servidor se encuentra acoplado en una única aplicación Flask.
Incluso la base de datos es un fichero de tipo sqlite3. Para adaptar esta app a un patrón de microservicios sería dividir el servidor en varias aplicaciones: un servicio de base de datos SQL,  un servicio que se dedique a obtener los datos de las impresoras (broker) y otro microservicio que se dedique a responder las peticiones REST de los clientes a partir de los datos disponibles en la base de datos.

### 2- En la aplicación que se ha usado como ejemplo en el ejercicio anterior, ¿podría usar diferentes lenguajes? ¿Qué almacenes de datos serían los más convenientes?

La aplicación está actualmente escrita en Python pero esto no quita que se pueda reescribir en otros lenguajes como JavaScript o Ruby. Los datos almacenados son de tipo estructurado, por lo que una base de datos SQL resulta completamente válida para este caso de uso. Un almacén clave valor podría usarse utilizando como clave lo que es ahora mismo la clave primaria de la BD y como valor una cadena json con el resto de registros, pero no sería posible obtener un campo específico sin consultar todo el valor almacenado.