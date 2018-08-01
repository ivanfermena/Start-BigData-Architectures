## Instalacion de Hadoop

### Descarga e instalacion base de Hadoop

Procederemos a la instalacion y configuracion de Hadoop en la maquina virtual de Nodo1 Maestro.

1. **Descargamos Hadoop** -> Accedemos a la web de [Hadoop de descargas](http://hadoop.apache.org/releases.html). Como consejo es interesante mirarse la web debido a que aparece informacion de distribuciones que se pueden usar con soporte de Hadoop e informacion de estas.

2. **Seleccionamos la version de Hadoop** -> En el curso se ha usado la 2.7.7, debido a que es muy estable y la version 2.X.X esta mas establecida, pero no deberia dar problemas en versiones mas nuevas. Seleccionamos el HTTP que queramos y automaticamente se inicia la descarga.

3. **Instalacion de paquete** -> Abrimos un terminal: "cd" para ir a la raiz y despues vamos a la carpeta descargas "cd descargas" (downloads si esta ne ingles). Como root tenemos que hacer un nuevo directorio en /opt para el hadoop.

    ```
    $ su - root
    $ cd /opt
    $ mdir hadoop
    $ chown hadoop /opt/hadoop
    $ exit
    ```

Entendiendo mas a fondo se crea como root un directorio, se da permisos al usuario hadoop para su uso y se sale de root. Ahora descomprimimos el zip en el /opt:

    $ cd /opt/hadoop
    $ tar xvf /home/hadoop/Descargas/hadoop-X.X.X.tar.gz
    $ mv hadoop-X.X.X/* .
    $ rmdir hadoop-X.X.X

Con esto estaria la instalacion de hadoop propiamente dicho.

### Instalar JDK

!(JDK)[http://somebooks.es/wp-content/uploads/2017/06/Instalar-JDK-en-Windows-10-025.jpg]

Antes de nada comporbamos que version de java tenemos instalada, esto se puede hacer abriendo un terminal y lanzando uno de los dos comandos siguiente:

Para pocos detalles:
```
    $ java -version 
```

Para mas detalle:
```
    $ alternatives --config java
```

Una vez lanzado esto si no tenemos la version "1.8" de java, necesitamos instalarla. Y el JDK para poder compilar determinadas funciones de las practicas siguientes. Para instalar el JDK vamos a la [pagina de Oracle de java](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html), seleccionamos la version "Java SE Development Kit 8u73" o la primera que se encuentre. 

Tras eso hay dos opciones para linux: 
    - XXXX...XXX.rpm -> La extension que usaremos nosotros debido a la mayor facilidad de instalacion al estar en CentOS.
    - XXXX...XXX.tar.gz -> Version mas global de instalacion (Si se escoge esta hay que seguir los mismos paso que cuando se ha instalado Hadoop).

Como root lanzamos los siguientes comandos (Adaptado a la version que se descargue en el momento):

    ```
    $ su - root
    $ rpm -ivh jdk-8uXX-linux-x64.rpm 
    $ exit
    ```

Si volvemos a lanzar el comando "java -vesion" vemos que seguimos teniendo la version 1.7 seleccionada, por ello se tiene que cambiar con lso siguientes comandos:

    ```
    $ alternatives --config java
    $ *
    ```
* Seleccionando la version que acabamos de instalar.