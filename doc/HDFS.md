## Capa de almacenamiento Hadoop - HDFS

### Definicion HDFS

HDFS es un sistema de almacenamiento muy tolerante a fallos que puede almacenar una gran cantidad de datos y es escalar incremental. Los datos los tienes replicados en varios nodos probocando que sea muy tolerante a fallos.

Por tanto, le pasas un bloque de datos a HDFS y este gestion ael alamacenamiento en el cluster, dividiendo los ficheros en bloques y almacenando copias duplicadas a traves de los nodos.

El numero de copias se puede escoger, dejando a eleccion del usuario esta configuracion. Por defecto, se duplica en 3 nodos distintos (visto que es lo mas eficiente, poner mas empeora la dificultad).

![distribucion nodos](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/hdfs.jpg)

### Distribucion de Hadoop con HDFS

Se tienen una distribucion de **nodo maestro** que solo tiene metadatos del claster y controla la gestion de este. Por otra parte se tienen los **nodos exclavos** que tienen los datos propiamente dichos.

![nodos](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/nodes.png)

