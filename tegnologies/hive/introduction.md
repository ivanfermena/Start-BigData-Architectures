# Introduccion a Hive

![Foto de logo de Hive](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bb/Apache_Hive_logo.svg/245px-Apache_Hive_logo.svg.png)

Es una de las tecnologias asociadas a Hadoop y una que suele estar en todos los clusters o proyectos, por su gran popularidad y utilidad muy buena. Sirve para acceder a HDFS como si fuera una base de datos convencional. Es otra manera de encarar el trabajo en Hadoop, pareciendo que estas trabajando con una base de datos relacional.

Es importante saber con esto una cosa muy importante **HDFS NO ES UN BASE DE DATOS RELACIONAL** y **HIVE NO CONVIERTE HDFS A UNA BASE DE DATOS RELACIONAL**.

Lo que hace realmente es ponerle un frontal o interfaz, con el que se puede ejecutar comandos parecidos a SQL, llamado **HiveSQL**. Con esto se simplifica mucho el desarrollo y analisis de los datos.

## Funcionamiento de HIVE

Hive tiene un Metastore que es un repositorio central para contener todos los metadatos de Hive. Hay varias maneras de trabajar con Hive:

* **Embebido**: siempre en Hive hay una base de datos relacional por debajo, algo curioso cuando trabajamos con sistemas Hadoop. Esta base de datos relacional es debido a que Hive cuando hace una consulta o tabla pasa a programas map-reduce para obtener los datos y despues los convierte a base de datos relacional, por eso tiene un almacen de estas consultas. Por eso es una base de datos embebida, ya que no es una base de datos tradicional si no un conector.

    Se suele usar poco esta manera de trabajar ya que al tener un Driver y una JVM (Java Virtual Machine) solo permite la utilizacion de un usuario, poco realista en un sistema real de un cluster. 
    
    ![Foto de Hive embebido](https://3.bp.blogspot.com/-Gn2y6RTLMz0/Wam0qbThWkI/AAAAAAAAH6s/x6muHd2PQ50z5sI2KFyrgc0_20rrvYYPACLcBGAs/s1600/Screenshot%2Bfrom%2B2017-09-01%2B12%253A27%253A11.png?w=600)

* **Local**: En este caso se sigue una filosofia muy parecida pero hay muchos JVM que contienen el "Driver" y "MetaStore", y apartir de este conjunto se ataca a la base de datos con JDBC (Java Data Base Connector). Nos permite tener multiple usuarios. Aunque mucho mejor que la manera embebida, ya que elimina la limitacion de JVM, tampoco se suele usar.
    
    ![Foto de Hive local](https://www.cloudera.com/documentation/enterprise/5-9-x/images/xhive_localmetastore.jpg.pagespeed.ic.UewlMpJNYV.jpg)

* **Remoto**: Esta es la manera mas usada a la hora de usar Hive, ya que es mucho mas comoda, segura y con multiples conexiones. Esta tiene un componente llamado **HIVESERVER** con el que se conecta con determinados clientes, para asi acceder al metastore de hive y con este a la base de datos.

    Con esto tambien se puede acceder con la version local, a partir del "Hive CLI".

    ![Foto de Hive remoto](https://itsnirmal.files.wordpress.com/2016/08/hadoop1.png?w=600)