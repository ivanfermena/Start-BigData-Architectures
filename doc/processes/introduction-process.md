## Introduccion a los procesos en Hadoop

Hasta ahora hemos visto el uso de datos en Hadoop con HDFS, ahora veremos los procesos de Hadoop. Dentro de los procesos en Hadoop se tienen dos tipos:

1.  **MapReduce V1**
2.  **MapReduce V2 - Conocido como YARN**

Hoy en dia en proyectos nuevos siempre se usa YARN. Aunque la version V1 de MapReduce se sigue usando y YARN amplia esta.

![Hadoop v1 y Hadoop v2](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/yarn.png)

### MapReduce V1

Estaba pensado sobre todo para procesos Batch y se encarga de procesos de los datos como la gestion del cluster.

![Hadoop v1](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/mapreduce1_architecture.png)

En esta version se tiene dos procesos el JobTracket y el TaskTracker. El primero gestiona la planificacion del cluster y la gestion de recursos. El segundo gestiona el esclavo, recursos del nodo... Es decir, gestionaba tareas qu eno tenian nada que ver entre si.

### YARN

Admite otro tipo de productos y procesos que no sean solo Batch. Tiene procesos distintos para el proceso de datos y para la gestion del cluster. Es decir que separa la gestion de la del proceso, consiguiendo con ellos mejor rendimiento.

Por tanto, en conclusion, con YARN se tiene una capa intermedia que gestiona el cluster y conceta el MapReduce o otros procesos con el HDFS, no se hace directamente como pasaria con version 1.

![Hadoop v2](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/mapreduce2_architecture.png)

Tenemos mas procesos:

* **ResouceManager(RM)** -> Gestiona todos los recursos de todo el cluster. 
* **NodeManager(NM)** -> En cada nodo hay un proceso de este tipo y se encarga de gestionar los recursos de cada nodo de manera independiente.
* **ApplicationMaster(AM)** -> Se encarga de gestionar los recursos de la aplicacion, su ciclo de vida y la planificacion de esta, ademas va a arrancar determinado **CONTAINER** que van a permitir que se mejore el tratamiento de los nodos del cluster.

Es decir, ya se tienen procesos no solo para la gestion de procesos batch, si no para todo tipo de procesos.
