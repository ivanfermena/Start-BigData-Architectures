## Introduccion a Hadoop
Hadoop es casi sinonimo del termino "Big Data". Big Data es el termino que se quiere implementar y Hadoop es la propia tegnologia necesaria para implementar ese termino.

![Tegnologies BigData](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0e/Hadoop_logo.svg/500px-Hadoop_logo.svg.png)

Es un entorno distribuido de:
- Datos (informacion)
- Procesos

Lo bueno que tiene es que se basa en una estructura de cluster, por tanto se colocan varios ordenadores que funcionan como uno solo. Ademas tiene una gran ventaja respecto al uso de grande servidores (tegnologia usada anteriormente) y es que es "Commodity Hardware", es decir, que es muy barato insertar nuevos ordenadores al cluster y hacer mas potente tu estructura Hadoop.

La estrategia que usa el big Data es la de "divide y venceras", como se divide el trabajo entre varias maquinas en vez de usar solo una: 
- 1 maquina = 10 min -> 10 maquinas = 1 minuto 

### Es muy tolerante a fallos
En Hadoop la regla general es que se piense que en algun momento algun nodo va a fallar y no se puede parar el procesamiento, esto no es problema debido a la distribucion en nodos que tiene. Si se pierde un nodo se pasa su trabajo a otro.

Si no se tienen estos dispositivos siempre se puede usar el "cloud".

### HADOOP

Se trata de un entorno que suministra librerias de open source para la computacion distribuida usando:
- **Hadoop Common** -> Todas las librerias comunes necesarias para el uso normal de esta estructura Big Data.
- **MapReduce y YARN** -> El el procesamiento y tratamiento de datos para su posterior almacenado. Son algortimos de procesamiento de datos que implementan procesos en paralelo.
- **Hadoop Distributed File System (HDFS)** -> Sistema de almacenamiento tolerante a fallos que almacena gran cantidad de datos, escalar incremental (nuevos nodos) y sobrevive a fallos. Redistribuye el trabajo y almacenamiento entre los diferentes nodos.

### Productos asociados a BigData
Hadoop por si solo es muy duro y complica las tareas a realizar, por ello se usan gran cantidad de tegnologias asociadas a Hadoop como:

![Tegnologies BigData](https://blogs.informatica.com/wp-content/uploads/2017/04/Big-Data-Stack-2.jpg)

- **Hive** -> Permite acceder a HDFS como si fuera una Base de datos. Commandos parecidos a SQL. Funciona por debajo con MapReduce pero simplifica el desarrollo.
- **HBase** -> Sistema de almacenamiento no relacional para Hadoop. Por defecto la usada po Hadoop. Es ta proporciona un sistema para el tratamiento de HDFS.
- **PIG** -> Es un lenguaje de scripting para analizar grandes cantidades de datos y permite trabajar en paralelo. Genera comando MapReduce.
- **Sqoop** -> La forma sencilla detranferir datos estructurados (como Bases de datos relacionales) con Hadoop a partir de comandos simples. 
- **Flume** -> Es muy parecido a Sqoop pero con grandes de cantidades de datos, especidalizado en "Texto". Por ejemplo, twitter o logs.
- **Zookeeper** -> Nos permite mantener la configuracion de nuestro cluster, como la conexion entre nodos o versiones en toda la estructura. Eslimina la complegidad de la gestion de la plataforma.
- **Spark** -> Es un motor muy diferente de procesamiento de datos a gran escala. Como ventaja trata procesamiento a tiempo real y no usa el MapReduce (mucho mas rapido que Hadoop). Usa la memoria Ram y no en disco mejorando la velocidad de procesamiento.
- **Flink** -> Es un motor de procesamiento muy potente en streaming de datos masivos. Actualmente esta siendo aumentando su uso debido al falso streaming de Spark y la mayor velocidad de Flink en comparacion con sus competidores. 
- **Otros** -> Kafka, Avro, Cassandra, Mohout...

