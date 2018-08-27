# Planificador de procesos (Scheduler)

El planificador es una seccion de procesos de hadoop que se nombro pero no se explico con determinacion. A continuacion se explica que es y para que sirve.

## Definicion

El Scheduler sirve para dterminar los recursos que tienen cada uno de los componenetes que tienen el cluster. Podemos asimilar que a todos los nodos se les da los mismo recursos, en cierto modo es asi, pero puedes configurarlo como desees.

## Partes

El planificador de procesos se separa en dos partes:

* **Fair Scheduler** -> Usado en version 1.*. Tienen un pool de recursos y a todos los procesos los asigna de manera homogenea una cantidad de recursos. Es dificil con esto aplicar prioridades.

![Foto sceduler](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/fairscheduler.png)

* **Capacity Scheduler** -> Usado en version 2.*. Se tiene una estructura de jerarquias, a partir de colas "queue". Si no se dice nada tendra sa siguiente estructura:

![Foto capacity scheduler](https://github.com/ivanfermena/Start-BigData-Architectures/blob/master/img/capacityscheduler.png)

Puedes dividir en distintas colas o jerarquias nuestros procesos. Dictando que jerarquia o cola tiene mas prioridad (usando diferentes porcentajes de procesamiento). Siempre usando los recursos del padre. Si no se le dice nad ase usa el 100% del padre.

Podemos ver la informacion de las diferentes colas de nuestro planificador, esto se hace con el siguiente comando:

    $ mapred queue -list

Si queremos una cola en particular con mas detalle:

    $ mapred queue -info default -showJobs

En donde "default" se pone el nombre de la cola a estudiar. 