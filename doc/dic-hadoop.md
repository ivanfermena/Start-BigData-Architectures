## Explicacion sencilla de archivos de Hadoop

### Distribucion:
El directorio de Hadoop una vez instalado queda separado en los siguientes directorio en arbol:

![Distrobucion arbol de archivos](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/tree-hadoop.png)

De manera menos visual y conla funcion que cada uno quedaria representado asi:

   - **bin** -> Contiene los principales ejecutables de hadoop, para la utilizacion de cada funcionalidad de este programa. Los mas importantes son: hadoop, hdfs, mapred y yarn.
   - **etc** -> Contiene los ficheros de configuracion para poder modificar las preferencias de hadoop.
   - **include** -> Pocos archivos que contienen utilidades que puedes ser necesarias en la compilacion o uso de hadoop.
   - **lib** -> Contiene librerias nativas necesarias necesarias en hadoop/
   - **libexec** -> Configuraciones mas detallas de hadoop.
   - **sbin** -> Scripts que nos permiten controlar el ciclo de vida o de ayuda en la ejecucion de hadoop (como por ejemplo parar hdsf)
   - **share** -> Se encuentra toda la paqueteria de hadoop, ejemplos, librerias, pruebas, control de errores...
   - **LICENCE.txt - NOTICE.txt - README.txt** -> Fichero como la licencia, noticias o el tipico readme con una ayuda.
