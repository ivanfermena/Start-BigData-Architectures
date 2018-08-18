## Cluester pseudodistribuido

Un cluster pseudodistribuido quiere extresar un cluster con un unico nodo, el cual actua como nodo maestro y nodo extravo al mismo tiempo. Este comportamiento es poco realista ya que en cluster reales nunca se produce (interfiere con la propia base del termino cluster).

Pero es una buena practica para apreder y/o despues duplicar los nodos para hacer un cluster con varios nodos iguales y que sepas que con uno a funcionado correctamente.

### Configuracion

Para configurar nuestro cluster tenemos que tocar una serie de archivos de formato xml. Estos archivos estaran en el repositio, en esta misma carpeta con las lineas necesarias para la correcta configuracion y con explicaciones de cada aspecto.

Sera necesario modificar los archivos:

1. **[core-site.xml](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/practices/cluster-pseudistributed/core-site.xml)** -> Archivo que compone que sistema de ficheros se usara, cual es el nod maestro... Es decir, la configuracion general y base de nuestro claster.
2. **[hdfs-site.xml](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/practices/cluster-pseudistributed/hdfs-site.xml)** -> Fichero donde se expresan donde estan los datos en los nodos exclavos y donde estan los metadatos del nodo maestro. Ademas del numero de veces que se replican los datos.

Como a la hora de configurar el fichero "hdfs-site.xml" se va poner varios directorios en /raiz que no han sido creados hay que entrar como root y crearlos para que encuentre dichos directorios en el sistema:

    $ su - root
    $ cd
    $ mkdir /datos
    $ mkdir /datos/datanode
    $ mkdir /datos/namenode
    $ chown -R hadoop:hadoop /datos
    $ exit

### Generar metadatos nodo-maestro - IMPORTANTE
Una vez hecha toda la configuracion es muy importante que esta se plasme en el sistema,esto se realiza con un comando de hadoop que lo que hace es formatear nuestro sistema y genera los metadatos del nodo maestro:

    $ hadoop namenode -format

Con esto se genera el directorio "/datos/current/" en donde estan esos metadatos de nuestro sistema de HDFS.

### Arrancar HDFS en la maquina

Una vez geenrados todos los metadatos necesarios para el inicio del uso de la seccion de datos de HDFS, es necesario arrancar el sistema. Para ello se tiene que lanzar el siguiente comando:

    $ ./opt/hadoop/sbin/start-dfs.sh 

Acordarse que el directorio sbin contenia varios ejecutable para controlar el ciclo de vida de las diferentes partes que componen hadoop (Aceptamos todo con "yes" si es necesario).

Para comprobar el correcto funcionamiento podemos ver los procesos creados con los comandos (ordenados de menos a mayor detalle):

    $ jps
    $ jps -l
    $ ps -ef | grep java

Otra manera es abriendo el navegador y lanzando el siguiente enlace:

    http://localhost:50070

Si no funciona ya que tenemos la version 3 instalada en hay que pone el puerto: 9870