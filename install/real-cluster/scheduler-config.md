# Configuracion basica del scheduler

El planificador se puede configurar como deseemos, dando a determinadas colas de procesos la cantidad de procesamiento que queramos. Para cambiar la configuracion de nuestro scheduler, se tiene que modificar:

```
    /opt/hadoop/etc/hadoop/capacity-scheduler.xml
```

Destacar como se ha dicho en la explicacion del scheduler de hadoop, hay dos planificadores dependiendo de la version que se use de hadoop. Si usaramos la version 1.* seria "Fair scheduler".

## Modificacion de parametros

Este archivo xml tiene una gran cantidad de propiedades que son muy interesantes, pero las que mas nos interesan a nosotros son las siguientes etiquetas:

* La primero etiqueta a modificar es en la que dictas que colas tendras debajo de root, como se ve por defecto esta "default", pero se puede insertar las que queramos separandolas por "," como se ve a continuacion:

    ```
    <property>
        <name>yarn.scheduler.capacity.root.queue</name>
        <value>default,prod,desa</value>
        <description>...<description/>
    </property>
    ```

Con este dictas que tienes dos hojas mas en el arbol que salen de root, llamadas "prod" y "desa". Ahora se les tiene que definir una cantidad de procesamiento, esto se hace con las siguientes etiquetas, modificando la "default" e insertando una nueva por cada nueva rama que se haga:

    ```
    <property>
        <name>yarn.scheduler.capacity.root.default.capacity</name>
        <value>30</value>
        <description>...<description/>
    </property>
    ```

    ```
    <property>
        <name>yarn.scheduler.capacity.root.prod.capacity</name>
        <value>50</value>
        <description>...<description/>
    </property>
    ```

    ```
    <property>
        <name>yarn.scheduler.capacity.root.desa.capacity</name>
        <value>20</value>
        <description>...<description/>
    </property>
    ```

Como se ve en las propiedades, la capacidad todas de procesamiento no debe superar el 100%, ya que puede dar error o que no funcione el cluster correctamente. COn esta configuracion tambien se tiene que hacer hijos de los hijos, es decir, se pueden insertar todos los hijos que queramos y hacer un arbol completo, segun nuestras necesidades.

## Reconfigurar scheduler

Para que las modificaciones se actualicen y hagan efecto hay que refrescar el planificador:

    $ yarn rmadmin -refreshQueue

Con esto, si no hay ningun error, se deben haber actualizado las colas del planificador.

## Lanzar trabajo a un determinado scheduler

A veces queremos que se lance un determinado proceso a una unica cola del planificador, puede ser que su configuracion sea mejor para esa tarea en concreto o por ejemplo que la otra cola este en una seccion del cluster en mantenimiento. Esta tarea se hace con el siguiente comando:

    $ haddop jar $PROCESO.jar $PROCESO -Dmapred.job.queue.name=$NAME_QUEUE $INPUT $OUTPUT

Se lanza igual que cualquier aplicacion de hadoop, con una atributo mas especificando el nombre de la queue.