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

### Comandos utiles

* Comando para ver si hay archivos en el directorio indicado:

    $ hdfs dfs -ls /

* Comando para saber si esta el dfs arrancado correctamente:

    $ jps


