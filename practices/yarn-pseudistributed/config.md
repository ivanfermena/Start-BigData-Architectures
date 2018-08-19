## Configuracion basica de YARN

Para la correcta configuracion del gestor de procesos de hadoop se tiene que modificar dos archivos de nuestro directorio de configuracion: **"/opt/hadoop/etc/hadoop"**

Los archivos a modificar estan disponibles en este directorio, con una breve explicacions en comentarios de que expresa cada linea de codigo. Los archivos a modificar son los siguientes:

**IMPORTANTE** - "Si no estan los archivo indicados y si esta el mismo *.template, crea uno nuevo, **NO MODIFIQUES EL TEMPLATE**"

* **yarn-site.xml** -> Configuracion del gestor de procesos, dictando en que nodo se encuentra del cluster, que proceso se va a usar (en este caso Map Reduce) y de donde se obtiene.
* **mapred-site.xml** -> Configuracion basica de que framework se va a usar, dictando el nombre de este, en este caso YARN.

Una vez configurados los dos archivos se debe iniciar el HDFS y YARN. Tener en cuenta que es muy **IMPORTANTE** arrancar antes el hdfs que el gestor de procesos Yarn.
Por ello se lanzan los comandos con el siguiente orden:

    $ start-dfs.sh
    $ start-yarn.sh

Si se produce algun error en el arranque comprueba que los archivos esten bien escritos, por ejemplo, surge un problema en cuanto se tenga una etiqueta mal cerrada o un nombre con alguna letra erronea. Acuerdate de cerrar la etiqueta despues -> <></>