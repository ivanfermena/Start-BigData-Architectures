# Comandos Yarn utiles para nuestros procesos

Como la mayoria de las aplicaciones se pueden gestionar 100% por comandos, en este caso no es diferente. Se pued ever toda la informacion de los nodos por linea de comando en vez de como se estaba haciendo, con el administrador web.

## Commnand "Application"

Comandos para gestionar las aplicaciones que se han ejecutado y se estan ejecutando en el cluster hadoop:

* **yarn application -list** -> Listado de las aplicaciones actualmente activas.
* **yarn application -status $APP_NAME** -> Muestra informacion de una aplicacion, como el estado de esta, donde puedes comprobar ese estado, recursos...
* **yarn application -kill $APP_NAME** -> Sirve para parar una aplicacion cuando se quiera forzar que se detenga.

## Command "Container"

Ver y gestionar informacion sobre los distintos contenedores que se han ejecutado en nuestras aplicaciones:

* **yarn aplicationattempt -list $APP_NAME** -> Muestra toda la lista de contenedores que hay en una determinada aplicacion.
* **yarn container -list $APP_NAME** -> Muestra informacion de los contenedores de una determinada aplicacion que este en curso. Te da la url de los logs de los contenedores determinados.

## Command "Node"

Nos permite ver la informacion de los nodos con los que estamos trabajando:

* **yarn node -list** -> Devuelve una lista con todos los nodos del cluster. Asi como informacion de estos, como el nodo-ID. Este nodo-ID sera pedido en muchos comandos.
Si queremos mas detalle de los nodos, se pone despues "-showDetails".

* **yarn node $APP_NAME** -> Muestra informacion de los nodos de una aplicacion y que contenedores se estan lanzando en cada nodo.