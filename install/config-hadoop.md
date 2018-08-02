## Configuracion de Hadoop

### Variables de entorno
Para que podamos lanzar actualmente hadoop desde el usuario creado de nuestra maquina es necesario insertarlo en el PATH del sistema. Nosotros lo configuraremos para solo el usuarui "hadoop" para mayor seguridad.

Como es conocido los archivos de un directorio que estan ocultos son los que empiezan en punto (por ejemplo: ./bash), estos se pueden ver lanzando el commnando en un directorio:

    $ ls -a

En el directorio de home del usuario hadoop tenemos un archivo que gestiona que commandos tenemos disponibles cuando arrancamos un determinado usuario, este es el ".bashrc", lo abreiremos con:

    $ cd /home/hadoop
    $ gedit ./bashrc

Se nos abrira el editor de texto gedit, perfecto para modificar archivos sencillos. **Al final de este archivo insertaremos las siguientes lineas**:

    export HADOOP_HOME=/opt/hadoop
    export JAVA_HOME=/usr/java/jdk1.8.0_181-amd64
    export PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin

Estas lineas lo que hacen es crear variables con las direcciones de hadoop y java home (necesario para el uso de hadoop) y añadirlas al PATH del sistema (despues de las que ya estaban).

Tras guardar el archivo, tenemos que lanzar estos comandos y si no sale ningun error es que la configuracion esta correcta:

    $ . ./.bashrc
    $ hadoop version