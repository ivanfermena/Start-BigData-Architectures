# Practica de MapReduce con el cluster de dos nodos

hdfs dfs -mkdir /prueba
hdfs dfs -put access_log /prueba
hadoop jar ContarPalabras.jar ContarPalabras /prueba/access_log /prueba_cluster_salida
