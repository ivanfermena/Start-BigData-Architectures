# Instalacion de Hive en el cluster

La instalacion de Hive es muy sencilla y parecida a Hadoop. A continuacion dictaremos que pasos se deben realizar para su instalacion, hay que tener en cuenta que version hemos instalado de hadoop para saber que version instalar de Hive, nosotros hemos instalado 2.3.3.

1. **Descargamos Hive** -> Para ello accedemos al enlace de descarga [hive.apache.org](http://hive.apache.org/) y nos vamos a la pestaña de "Downloads". Tras esto le damos al enlace "Download a release now!", dictamos el servidor de descarga, en nuestro caso HTTP (cualquiera de ellos) y seleccionamos la version que queramos descargar (en nuestro caso 2.3.3). Hay que seleccionar la opcion "bin.tar.gz" para mayor comodidad.

2. **Descomprimimos el archivo y movemos a opt** -> Descomprimimos el comando descargado y lo movemos a etc, donde tenemos instalado hadoop (no es obligatorio que esten en el mismo directorio):

    ```
    $ tar xvf /home/hadoop/Descargas/apache-hive-*.*.*-bin.tar.gz
    $ mv apache-hive-2.3.3-bin /opt/hadoop/hive
    ```

    Se puede querer en clusters realis tener un usuario especifico para hive y asi no se unen utilidades ni usos. 

3. **Editamos el fichero de Hadoop para insertar Hive** -> Hace falta una breve configuracion de ficheros hadoop para que funcione correctamente Hive.

    ```
    $ vi /home/hadoop/.bashrc
    ```

    Insertamos las primera linea entera y concatenamos la variable "$PATH" con la segunda linea:

    ```
    export HIVE_HOME=/opt/hadoop/hive
    export PATH=$PATH:......:$HIVE_HOME/bin
    ```

4. **Preparamos configuracion basica de Hive**

    Ahora nos centramos en la configuracion de aquellos archivos para que hive funcione correctamente. Copiamos los templates y los modificamos a nuestro gusto:

    ```
    $ cd /home/hadoop/hive/conf
    $ cp hive-default.xml.template hive-site.xml 
    $ cp hive-env.sh.template hive-env.sh
    $ cp hive-exec-log4j2.properties.template hive-exec-log4j2.properties
    $ cp hive-log4j2.properties.template hive-log4j2.properties
    $ cp beeline-log4j2.properties.template beeline-log4j2.properties
    ```

    Modificamos algunos de estos archivos:

    ```
    $ vi hive-env.sh
    ```
    
    En este archivo insertamos las siguientes variables:

    ```
    export HADOOP_HOME=/opt/hadoop
    export HIVE_CONF_DIR=/opt/hadoop/hive/conf
    ```