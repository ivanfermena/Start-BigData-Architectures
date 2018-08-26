# Comandos Yarn utiles para nuestros porcesos

## Commnand "Application"

Comandos para gestionar las aplicaciones que se han ejecutado y se estan ejecutando en el cluster hadoop:

* **yarn application -list** -> Listado de las aplicaciones actualmente activas.
* **yarn application -status $APP_NAME** -> Muestra informacion de una aplicacion, como el estado de esta, donde puedes comprobar ese estado, recursos...
* **yarn application -kill $APP_NAME** -> Sirve para parar una aplicacion cuando se quiera forzar que se detenga.

## Command "Container"

Ver y gestionar informacion sobre los distintos contenedores que se han ejecutado en nuestras aplicaciones:



## Container "Node"

Nos permite ver la informacion de los nodos con los que estamos trabajando:

* **yarn node -list** -> Devuelve una lista con todos los nodos del cluster. Asi como informacion de estos, como el nodo-ID. Este nodo-ID sera pedido en muchos comandos.
Si queremos mas detalle de los nodos, se pone despues "-showDetails".

* **yarn node $APP_NAME** -> Muestra informacion de los nodos de una aplicacion y que contenedores se estan lanzando en cada nodo.