## Instalacion de Hadoop

### Descarga e instalacion base de Hadoop

Procederemos a la instalacion y configuracion de Hadoop en la maquina virtual de Nodo1 Maestro.

1. **Descargamos Hadoop** -> Accedemos a la web de [Hadoop de descargas](http://hadoop.apache.org/releases.html). Como consejo es interesante mirarse la web debido a que aparece informacion de distribuciones que se pueden usar con soporte de Hadoop e informacion de estas.

2. **Seleccionamos la version de Hadoop** -> En el curso se ha usado la 2.7.7, debido a que es muy estable y la version 2.X.X esta mas establecida, pero no deberia dar problemas en versiones mas nuevas. Seleccionamos el HTTP que queramos y automaticamente se inicia la descarga.

3. **Instalacion de paquete** -> Abrimos un terminal: "cd" para ir a la raiz y despues vamos a la carpeta descargas "cd descargas" (downloads si esta ne ingles). Como root tenemos que hacer un nuevo directorio en /opt para el hadoop.

    ```
    - su - root
    - cd /opt
    - mdir hadoop
    - chown hadoop /opt/hadoop
    - exit
    ```

Entendiendo mas a fondo se crea como root un directorio, se da permisos al usuario hadoop para su uso y se sale de root. Ahora descomprimimos el zip en el /opt:

    - cd /opt/hadoop
    - tar xvf /home/hadoop/Descargas/hadoop-X.X.X.tar.gz
    - mv hadoop-X.X.X/* .
    - rmdir hadoop-X.X.X

Con esto estaria la instalacion de hadoop propiamente dicho.

### Instalar JDK

