# Contador de palabras basico en Java

Esta practica esta orientada al uso de un programa que cuenta las palabras de un archivo txt, el tipico programa que suele aprenderse cuando se inicia en el proceso mapReduce.

## Objetivo

Como se ha nombrado antes el objetivo de esta practica es ver como ejecutar una clase de java que tiene implementada la funcion de tipo MapReduce, de manera sencilla. Este proceso de map reduce realiza un conteo de palabras sencillo.

## Proceso

1. **Preparado de proceso** -> Antes de lanzar el ejemplo hay que preaparar todo el sistema para que se lance el proceso de manera correcta:

    *   Creamos una nueva carpeta en /home para esta practica, descargamos y copiamos el ContarPalabras.java a la carpeta creada (esta se encuentra en el repositorio):
        
        ```
        $ mkdir practicas
        $ cd /practicas
        $ cp /tmp/ContarPalabras.java .
        ```

    *   Es necesario antes de compilar nuestro .java que exportemos las herramientas necesarias para ello a nuestro path de hadoop.

        ```
        $ export HADOOP_CLASSPATH=/usr/java/jdk1.8.0_181-amd64/lib/tools.jar 
        ```

    *   Compilamos la clase java para obtener los .class necesarios, tras esto generamos un .jar ya que hadoop lanza los procesos con extensiones ".jar".

        ```
        $ hadoop com.sun.tools.javac.Main ContarPalabras.java
        $ jar cf ContarPalabras.jar Contar*.class
        ```

    *   Es interesante tambien iniciar el historial de hadoop para los procesos, de este modo podemos seguir todo el proceso de manera detallada:

        ```
        $ mr-jobhistory-daemon.sh start historyserver
        ```

2. **Lanzamos ejemplo** -> Antes de lanzar el comando que ejecutaria el .jar generado en el punto uno, es aconsejable mirar el "ContarPalabras.java" donde se ven clases llamada map y reduce, muy curiosas de analizar detenidamente.

    *   Comando para lanzar el proceso:

        ```
        $ hadoop jar ContarPalabras.jar ContarPalabras /temporal/acces_log /salidaLog
        ```

    * Esperamos a que se termine y lleguen al 100% tanto el proceso map como el reduce.

3. **Ver resultado** -> Para ver el resultado hay que irse a nuestro directorio /salidaLog y ahi debe haber generado un archivo donde esta un txt con el conteo de palabras.

Peor lo interesante de este ejercicio es ver el proceso de ejecucion en el administrador de yarn [http://nodo1:8088](http://nodo1:8088). Aqui gracias a activar el historial, los logs y toda la informacion que aparece se puede saber cada uno de los procesos por los que ha pasado nuestro mapReduce.

Llegando a conclusiones como que se han lanzado 4 map y 1 reduce, el tiempo que han tardado y en que nodo se han lanzado.

## Conclusion

Como conclusion en esta practica hemos tratado como introducir como lanzar un proceso java en hadoop, ademas de ver en el administrador como gestionar toda la informacion que surge. Ademas se ha aprendido la gran carga de trabajo que produce en el ordenador realizar un proceso en hadoop, dejando la maquina virtual varias veces bloqueada.
