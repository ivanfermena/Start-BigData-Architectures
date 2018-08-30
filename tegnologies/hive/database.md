# Creacion de Base de datos y tablas
 
En este documento se expresa la configuracion de Hive para la creacion de la base de datos en la cual se va a sorportar esta tegnologia como vimos en la introduccion. En este caso lo haremos a nivel local y que aunque sea mejor de manera remota no es el objetivo del aprendizaje. 

* Primero configuramos el directorio de "hive-site.xml" insertando unas nuevas lineas en las que describimos donde esta java y el usuario que accede:

    ```
    $ vi /opt/hadoop/hive/hive-site.xml
    ```

    Insertamos **los primeros** estas propiedades nuevas:

    ```
    <property>
        <name>system:java.io.tmpdir</name>
        <value>/tmp/hive/java</value>
    </property>
    <property>
        <name>system:user.name</name>
        <value>${user.name}</value>
    </property>
    ```

* Creamos el directorio donde va a estar la base de datos de Hive y accediendo a el, inicializamos el directorio "derby" para poder arracar la base de datos:

    ```
    $ mkdir bbdd
    $ cd bbdd
    $ schematool -dbType derby -initSchema
    ```

* Abrimos el gestor de comandos de Hive con el siguiente comando y si no hay ningun problema se nos debe abrir un editor de comandos parecido al de sql/python...

    ```
    $ hive
    ```

* Lanzamos los comandos para crear la base de datos y tablas que queramos, en este caso se trata de un ejemplo sencillo para ver el corrector funcionamiento de Hive.    
    ```
    > create database ejemplo;
    > use ejemplo;
    > show databases;

    > create table if not exists t1
    > (
    > name string
    > );

    > show tables;
    ```

Como conlusion se puede sacar dos cosas muy interesantes del uso de HIVE en este momento y a falta de mas ejemplos. El primero es que Hive permite gracias a comandos parecidos a SQL facilitar mucho la interaccion con HDFS, evitando hacer programas elavorados y lanzando simples comandos. El segundo punto a tener en cuenta es como permite una integracion de los datos a HDFS de manera mucho mas simple, por ejemplo, cuando hablas de una tabla en HiveSQL en realidad tratas un texto plano de MapReduce.


