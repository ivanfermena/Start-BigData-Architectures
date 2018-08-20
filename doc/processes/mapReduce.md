## Introduccion a Map Reduce

![MapReduce](https://4zy7s42hws72i51dv3513vnm-wpengine.netdna-ssl.com/wp-content/uploads/2017/07/hadoop-mapreduce-big.png)

Map Reduce es un proceso de programacion que se centra en la ejecucion paralela y distribuida, a traves de varios nodos de un cluster. Usado para grandes cantidades de datos en ordena de terabytes y petabytes.

El objetivo de Map Reduce es trabajar de manera simple, robusta, rapida, resistente a fallos y escalable de trabajar con esa elevada cantidad de datos.

 ### Funcionamiento

 Map reduce se diferencia en varios conceptos principales, los cuales hay que conocer para saber el funcionamiento basico de este proceso:

 * **Map** -> El proceso de Mapping es basico en terminos de programacion y se basa en los terminos **key-value**, donde se asocia una clave identificativa (pj: una palabra de un texto) y un valor (pj: las veces que aparece), esta clave es unica para cada proceso map de cada nodo y el valor puede ser listas, numeros... En este proceso cada nodo se encarga de un bloque de datos o de una seccion de los datos.
 * **Sort-Shuffle** -> Algoritmos de ordenacion o colocacion (union) de estas palabras, su principal funcion es unir los resultados obtenidos en los diferentes nodos.
 * **Reduce** -> Realiza un conteo de la union realizada con el reduce. Obteniendo el resultado final de nuestro porceso map-reduce.

 Como se comenta en la introduccion a procesos de yarn el que se encarga de gestionar quien realiza cada tarea, gestion de recursos y si hay problemas redirecciona el trabajo a otro nodo es el **ResourceManager**.

 ### Fases

![MapReduce](https://bigdatapath.files.wordpress.com/2018/04/12.png)

 1. **Mapping** -> Coges tu informacion y la seleccionas con la forma key-value (k,v). Este realiza las operaciones previas para la preparacion de datos con el objetivo de detar los datos correctos para su posterior procesado. Por ejemplo, separar palabras por espacios... Esto genera una lista(key-value) para cada nodo.

 2. **Shuffling** -> Coge todos los resultados de los diferentes nodos y une los estos resultados, esta union da como solucion una lista de tipo **key, list(value)**.

 3. **Reduce** -> Coge ese resultado obtenido en el shuffling y la lista que esta en el value la sintetiza, obteniendo un conteo de elementos o una operacion determinada, dejando esa estructura como una list(key, value).

