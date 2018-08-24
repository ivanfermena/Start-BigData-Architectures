# Practica de MapReduce con el cluster de dos nodos

En esta practica lasnzaremos el proceso MapReduce de conteo de palabras probado en otras practicas pero sobre el cluster con varios nodos. Como hemos hecho en otras practicas lo primero es creara un directorio y traerse el archivo a probar a este directorio:

    $ hdfs dfs -mkdir /prueba
    $ hdfs dfs -put access_log /prueba

El archivo "access_log" se encuentra en el directorio. A continuacion se lanza el proceso de hadoop para lanzar el jar, este jar se encuentra en la carpeta de "/practicas/" generado en otras practicas.

    $ hadoop jar ContarPalabras.jar ContarPalabras /prueba/access_log /prueba_cluster_salida

El resultado se ve igual que el resto de acciones, ya que entrando en el administrador de navegador se puede ver toda la informacion de los nodos o del cluster.
