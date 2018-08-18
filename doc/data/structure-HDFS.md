## Estructura de fichero de HDFS

A la hora de usar HDFS se tiene que conocer como este administra los metadatos de los nodos para poder administrar los datos correctamente.

Primero debemos saber que HDFS tiene unos ficheros que gestionan los cambios que se producen en el cluster de HDFS y tienen informacion de cuando/donde se han realizado dichos cambios.

### Archivos de gestion de cambios HDFS

* **Edits_000xxxxxx** -> Almacena todos los cambios que se van produciendo en la base de datos de HDFS, es decir, todos los metadatos de las diferentes escrituras de datos.

* **Edits_inprogresss_xxxxxx** -> Donde se estan escribiendo los datos en este momento.

* **Fsimage_00000xxxx** -> Contienen una copia o foto en un momento en el tiempo del sistema de ficheros.

### Filosofia de trabajo

![Estructura ficheros metadatos HDFS](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/hdfs-metadatos.png)

La manera de trabajar se ve muy clara a partir de la imagen superior. Primero cuando se arranca el sistema de fichero se le el ultimo "Fsimage" y lo que se hace es que se carga en memoria. Este archivo que se carga en memoria no se toca, si no que se construye a partir de este un "Edits_inprogress".

El edits_inprogress va actualizandose en memoria ya que seri amuy poco eficiente guardarlo en el Fsimage cada vez que hubiera una actualizacion.

Dentro del edits_inprogress se van alamacenando los bloques y cada cierto tiempo se sincroniza, a traves del proceso **secundarynamenode**. Este tiene la funcion de ir sincronizando lo que se va grabando en el momento y unirlo a lo que habia en el "Fsimage".

Este sistema de archivos **no se toca** ya que es propio de HDFS. No se toca manualmente.