## Practica con ficheros en dfs HDFS

En esta practica tras la instalacion de HDFS empezaremos en el uso de HDFS insertando los primeros archivos en el sistema de ficheros (dfs) y manipulandolos.

Los comandos son muy parecidos a los commandos linux, por tanto, si se conocen es muy intuitivo.

### Practica 1

Inserccion de fichero prueba.txt en el sistema de ficheros. Para hacer la practica se tienen que lanzar los siguienets comandos:

* Iniciamos nuestro sistema HDFS:

    $ ./start-dfs.sh 

* Creamos un archivo con cualquier mensaje llamado prueba.txt:

    $ echo Hola >> prueba.txt

* Creamos un directorio para introducir nuestro archivo:

    $ hdfs dfs -mkdir /temporal

* Insertamos ese archivo dentro del sistema de ficheros:

    $ hdfs dfs -put prueba.txt /temporal

Se puede comporbar su exsitencia con el comando **ls** indicado abajo o desde el navegador lanzando el enlace [localhost:50070](localhost:50070).

### Practica 2

En este caso lo que haremos es usar un archivo mucho mas grande y asi que use mas bloques de nuestro sistema de ficheros. Para eso usaremos el archivo .zip que se encuentra en el mismo directorio de este documento llamado: "access-log.gz".

Lo primero que hacemos es descargarlo y descomprimirlo. Por comandos seria: 

    $ gunzip access_log.gz

Una vez descomprimido lanzaremos el mismo comando que antes para insertarlo en nuestro sistema de ficheros:

    $ hdfs dfs -put /home/hadoop/Descargas/access_log /temporal/access_log

Cambiar el path del archivo en donde lo hayais descomprimido.

Un vez hecho solo queda comprobar que al ser demasiado grande y debido a que hdfs separa en bloques de **128MB**, crea 4 bloques. Accedemos al enlace [localhost:50070](localhost:50070) "en version 2" y en Browse Directory buscamos el archivo, si pinchamos en este podemos ir seleccionando los diferentes bloques que hay, son el size y el ID de bloque.

![Bloques hdfs](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/blocks-dfs.png)

### Comandos utiles

* Comando para ver si hay archivos en el directorio indicado:

    $ hdfs dfs -ls /

* Comando para saber si esta el dfs arrancado correctamente:

    $ jps

* Comando para crear un directorio en nuestro sistema de ficheros:

    $ hdfs dfs -mkdir temporal

* Borrar ficheros del sistema de ficheros:

    $ hdfs dfs -rm /temporal/prueba.txt

Hay muchos comandos y para muchisimas utilidades con archivos, si se quiere ver una lista de todos ellos se puede lanzar cualquiera de estos dos comandos:

    $ hdfs
    $ hdfs dfs