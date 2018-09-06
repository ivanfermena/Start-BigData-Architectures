# Tablas internas y externas de la base de datos de Hive

En Hive existen dos tipos de tablas, en este documento se veran con detalle asi como sus diferencias.

## Definiciones y diferencias

Las tabla interna es aquella en la que todo el ciclo de la tabla, informacion que contiene y determinados comandos los gestiona el Hive, por ejemplo, si desde Hive borrar unos ficheros se borran esos fichero asociados. Determinados datos en los cuales Hive tiene mayor control.

Si la tabla es externa se tienen datos que se tienen de manera separada de Hive, por tanto, es incluso usada por otros servicios y tiene que ser usada tambien por Hive. No es Hive el que controla el ciclo de vida de esa tabla.

## Ejemplos de ambas

### Tablas internas

Creamos un fichero sencillo que tenga varios nombres con una edad separado con comas.

    $ vi empleados.txt    

Y le escribimos por ejemplo el siguiente texto:

    Rosa,50
    Pedro,43
    Raul,24

No volvemos una vez creado el archivo, a lanzar Hive oaa lanzar este fichero ejemplo.

    $ Hive

    > use ejemplo;
    >
    > create table empleados
    > (
    > nombre string,
    > edad integer
    > )
    > row format delimited
    > fields terminated by ',';

Ahora lo que vamos a hacer es que asociar el archivo creado antes de empleados con la tabla de empleados generada. Se podria hacer un "insert" de cada valor pero esta forma es mas correcta y tarda menos ya que como hemos dicho lanza mapreduce por debajo. Para ello lanzamos el siguiente comando Hive:

    > load data local inpath 'tmp/empleados.txt' into table empleados;

Internamente lo unico que ha hecho es asociar la direccion de empleados en la base de datos con el fichero creados anteriormente, lo carga pero siempre desde texto y no como se conoce como una base de datos relacional comun. Te carga ademas con cada "load" un fichero diferente aunque estos tengan lo mismo repetido y si es igual lo duplica. Lee todo el contenido hdfs y le da el formato especifico.

Si hacemos un "drop" de empleados al ser interna borra todo el ciclo de vida de este, sus tablas y asociaciones a ficheros.

### Tablas externas

Primero lo que hacemos es cargar el fichero de empleado al sistema de ficheros de HDFS.

    $ hdfs dfs -mkdir /prueba
    $ hdfs dfs -put empleados.txt /prueba

Creamos una tabla determinada expecificando que es externa a Hive (El simbolo ">" significa que se lanza en Hive)

    > create external table empleados
    > (
    > nombre string,
    > edad integer
    > )
    > row format delimited,
    > fields terminated by ','
    > location '/user/hive/datos/empleados';

Ahora lo que hacemos es cargar los datos al directorio creado, pero no se pone local de esten modo se especifica que es externo.

    > load data inpath '/prueba/empleados.txt' into table empleados;

Cone esto ya se tendrian los datos en a tabla empleados. Con esto si hacemos una "DROP" nos se borran los archivos que estan en hdfs ya que es externo y apunta a una direccion de memoria determinada.