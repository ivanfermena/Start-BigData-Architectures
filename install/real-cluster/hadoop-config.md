# Configuracion basica de hadoop en el nodo real con varios nodos

Antes de hacer cualquier configuracion con el hadoop de los diferentes nodos, se tienen que tener varias cosas muy presentes para que el funcionamiento sea correcta. Si se han seguido todas las configuraciones no se han realizado todos los pasos. Los servidores tienen que ser practicamente clones a nivel de hadoop, teniendo toda la configuracion principal igual:

* **El mismo usuario en todos los nodos**
* **Que sean accesible a traves de ssh sin contraseña**
* **Tener los mismo directorios en cada nodo, no es obligatorio peor si muy aconsejable**
* **Haber copiado el software de hadoop en todos los nodos y en el mismo sitio**
* **Haber creado el directorio de datos en todos los nodos y haberle dado el permiso correspondiente (en nuestro caso /datos/datanode)**

## Configuracion previa

Antes de nada tenemos que dejar limpio el directorio data, ya que los nodos exclavos por la clonacion contienen informacion referente al nodo maestro que no tienen que tener.
En los nodos 2 y 3 (exclavos) realizamos los siguientes pasos:

    $ cd /datos
    $ rm -rf namenode
    $ rm -rf /datanode/current

Ahora por la misma razon, en el nodo1 no se pueden tener datos ya que va a ser el nodo maestro y no es su funcion almacenar datos:

    $ cd /datos
    $ rm -rf /datanode

## Configuracion de archivos Hadoop

A continuacion vamos a configurar los archivos de hadoop portando la configuracion que teniamos de 1 nodo exclavo a dos. Aqui se dictara los archivos que se modifician, donde se encuntran y en el directorio estara el archivo con la modificacion. Asi solo se tiene que copiar y pegar o compararar con el existente:

* **hdfs-site.xml** -> Se ha cambiado la etiqueda de numero de nodos exclavos de 1 a 2.
* **slaves** -> Quitamos el "localhost" e insertamos el "nodo2" y "nodo3", en este archivo se dicta cuales de los nodos va a ser exclavo.

Por ultimo, lo que se hace es copiar el archivo "hdfs-site.xml" al resto de nodos:

    $ scp hdfs-site.xml nodo2:/opt/hadoop/etc/hadoop/
    $ scp hdfs-site.xml nodo3:/opt/hadoop/etc/hadoop/