# Instalacion configuracion de HUE

## **Instalacion de HUE**

Antes de poder instalar HUE necesitamos realizar una serie de instalaciones en el servidor, en concreto lo haremos en el nodo1. Para ellos nos conectamos como root y lanzamos los siguientes comenados de instalacion:

    $ yum install libffi-devel
    $ yum install gmp-devel
    $ yum install python-devel mysql-devel
    $ yum install ant gcc gcc-c++ rsync krb5-devel mysql openssl-devel cyrus-sasldevel
    $ cyrus-sasl-gssapi sqlite-devel openldap-devel python-simplejson
    $ yum install libtidy libxml2-devel libxslt-devel
    $ yum install python-devel python-simplejson python-setuptools
    $ yum install maven

Hay que tener en cuenta que a lo mejor algunos de estos paquetes ya se tienen instalados en el nodo1, por tanto, se pasa al siguiente que sea necesario sin problema.
A continuacion vamos a la [pagina de HUE](https://gethue.com), en el menu seleccionamos downloads y seleccionamos la version que queramos. Todas las versiones son validad aunque aconsejamos la mas moderna (en nuestor caso 4.2).

Desconprimimos el archivo bescargado con el siguiente comando:

    $ tar xvf hue-XXXX

Finalmente accedemos al directorio creado y lanzamos la compilacion final con make. 

    $ PREFIX=/opt/hadoop make install

Con la sentencia PREFIX se dicta donde se va a color la carpeta determinada que se obtenga de la compilacion con make.

## **Configuracion de HUE**

Aunque la instalacion esta completa es necesario que se haga unas cuantas configuraciones. Accedemos al directorio de configuración de HUE:
    
    $ cd /opt/hadoop/hue/desktop/conf

Modificamos el archivo "hue.ini" con vi o con gedit. Debemos configurar los valores para:

* HDFS
* YARN
* HIVE

Debemos poner correctamente la dirección. En nuestro caso, debería bastar con sustituir localhost por “nodo1” y cambiar el puerto de 8220 a 9000 en la parte de HDFS.

### HDFS

La parte de HDFS debe quedar similar a la siguiente:

    # Settings to configure your Hadoop cluster.
    ###############################################################
    ############

    [hadoop]

    # Configuration for HDFS NameNode
    # ------------------------------------------------------------------------
    [[hdfs_clusters]]
    # HA support by using HttpFs
    [[[default]]]
    # Enter the filesystem uri
    fs_defaultfs=hdfs://nodo1:9000

    # NameNode logical name.
    
    ## logical_name=
    # Use WebHdfs/HttpFs as the communication mechanism.
    # Domain should be the NameNode or HttpFs host.
    # Default port is 14000 for HttpFs.
    webhdfs_url=http://nodo1:50070/webhdfs/v1

### YARN

La parte de YARN debe ser similar a la siguiente:

    [[yarn_clusters]]

    [[[default]]]
    # Enter the host on which you are running the ResourceManager
    resourcemanager_host=nodo1

    # The port where the ResourceManager IPC listens on
    resourcemanager_port=8032

    # Whether to submit jobs to this cluster
    submit_to=True

    # Resource Manager logical name (required for HA)
    ## logical_name=

    # Change this if your YARN cluster is Kerberos-secured
    ## security_enabled=false

    # URL of the ResourceManager API
    ## resourcemanager_api_url=http://nodo1:8088

    # URL of the ProxyServer API
    ## proxy_api_url=http://nodo1:8088

    # URL of the HistoryServer API
    ## history_server_api_url=http://nodo1:19888Se hace con el siguiente
    comando.

### HIVE

Y por último, la parte de HIVE debe poner lo siguiente:

    [beeswax]

    # Host where HiveServer2 is running.
    # If Kerberos security is enabled, use fully-qualified domain name (FQDN).
    hive_server_host=nodo1

    # Port where HiveServer2 Thrift server runs on.
    hive_server_port=10000

    # Hive configuration directory, where hive-site.xml is located
    hive_conf_dir=/opt/hadoop/hive/conf


Por último, y muy importante, debemos activar WEBHDFS en nuestro cluster. Modificamos el fichero "hdfs-site" y añadimos la siguiente propiedad:

    <property>
        <name>dfs.webhdfs.enabled</name>
        <value>true</value>
    </property>

Y en el fichero core-site.xml añadimos la siguiente propiedad:

    <property>
        <name>hadoop.proxyuser.hue.hosts</name>
        <value>*</value>
    </property>
    <property>
        <name>hadoop.proxyuser.hue.groups</name>
        <value>*</value>
    </property>

Para arranacar y probar HUE, lanzamos el siguiente comando y ponemos en el navegador "nodo1:8888":

    $ /opt/hadoop/hue/build/env/bin/supervisor -d