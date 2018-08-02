## Ejemplo sencillo MapReduce - Grep

![Map reduce](https://i.stack.imgur.com/199Q1.png)

Ejemplo muy sencillo del uso de hadoop de manera distribuida aprovechando los ejemplo que trae hadoop por defecto en la instalacion.

### Archivos y directorios usados
- /opt/hadoop/share/hadoop/mapreduce/hadoop-mapreduce-examples-2.7.7.jar

### Finalidad
La finalidad del ejemplo es comprobar el correcto funcionamiento de hadoop y contar palabras de un determinado directorio (El tipico primer programa de mapreduce).

### Pasos previos
Antes de nada creamos los directorios donde preparemos los archivos a tratar. Copiaremos varios archivos de tipo xml en un directorio a parte para localizarlos rapidamente y lanzar el programa.

    $ mkdir /tmp/entrada
    $ cp /opt/hadoop/etc/hadoop/*.xml /tmp/entrada/


### Ejecucion de programa
Vamos al directorio donde se encuentra el "jar" en donde estan los ejemplos:

    $ cd /opt/hadoop/share/hadoop/mapreduce

Lanzamos el ejemplo de map reduce con grep en los fichero copiados:

    $ hadoop jar hadoop-mapreduce-examples-2.7.7.jar grep /tmp/entrada/ /tmp/salida 'kms[a-z.]+'

Explicacion de cada argumento del comando:
- **hadoop** -> Lanzamiento de hadoop, se puede lanzar desde cualquier sitio del usuario gracias la configuracion de variables de entorno.
- **jar** -> Dictas que se va a lanzar un .jar como script
- **fichero .jar** -> Fichero a lanzar que contiene todos los scripts lanzables. Se puede ver el contenido previamente con: $ jar tf Nombre_archivo.jar
- **grep** -> Programa a ejecutar que este contenido dentro del .jar
- **/tmp/entrada/** -> Directorio o archivo de entrada.
- **/tmp/salida** -> Directorio de salida (se crea automaticamente).
- **'kms[a-z.]+'** -> Que palabra quieres buscar en los archivo. En este caso buscamos todos las veces que aparece palabras empezadas por "kms".

### Comprobacion de exito
No iriamos al directorio de salida que se ha creado y comprobamos si hay dos archivos: part-r-00000 y _SUCCESS.

Si en vez del archivo _SUCCESS aparece otro diferente significa que se ha producido algun error.

Abrimos el fichero donde esta la salida de la ejecucion:

    $ cat part-r-00000

Nos debe aparecer el numero de veces que aparece una determinada palabra con los terminos lanzados anteriormente (en orden decreciente).

### Salida

9	kms.acl.

2	kms.keytab

1	kms.keystore

1	kms.key.provider.uri

1	kms.current.key.cache.timeout.ms

1	kms.cache.timeout.ms

1	kms.cache.enable

1	kms.authentication.type

1	kms.authentication.signer.secret.provider.zookeeper.path

1	kms.keystore.password

1	kms.authentication.signer.secret.provider.zookeeper.kerberos.keytab

1	kms.authentication.signer.secret.provider.zookeeper.connection.string

....
