# Practica de Map Reduce con Python

En este caso lo que haremos es lanzar el mismo ejemplo que se ha lanzado con java en el otro ejemplo (mirar para mas detalle de como funciona el ejemplo) pero con python. Dictar que en hadoop para lanzar procesos en otros lenguajes que no sean java se hace con "streaming". 

Esta herramienta permite lanzar cualquier proceso con cualquier lenguaje separando en varias partes el proceso, por ejemplo, se lanza el mapper en una clase y el reduce en otra clase, ademas de en archivos separados.

## Proceso de practica

1.  **Descargamos y preparamos el entonrno** -> Descargamos los dos archivos ".py" que hay en el directorio. Si queremos podemos crear un directorio para tenerlo todo mas ordenado y accesible.

2. **Lanzamos el streming para montar el map y el reduce** -> Ahora como hemos nombrado nates hay que insertar nuestro proceso mapReduce, pero al ser en python hay que hacerlo con la herramienta streaming:

    $ hadoop jar /opt/hadoop/share/hadoop/tools/lib/hadoop-streaming-2.7.7.jar -file pymap.py -mapper pymap.py -file pyreducer.py -reducer pyreducer.py -input /temporal/access_log -output /salidalogPy

3. **Miramos resultados** -> Al igual que con la practica en java se pueden ver los resultados en el txt que se genere en donde hayamos especificado el output, pero lo interesante es lanzar el navegador y con el administrador de yarn mirar los resultados y es historial del proceso una vez terminado.


PD: Si se produce un error a la hora de ejecutar el mapReduce con streming, se comproba si se tiene python instalado con:

    $ python -V

Si esta instalado y sigue fallando, damos permisos a los dos archivos .py:

    $ chmod +x *