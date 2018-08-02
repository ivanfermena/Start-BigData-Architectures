## Configuracion ssh de nodoMaestro-nodosEsclavos

Cuando tenemos un cluster de hadoop el nodo maestro tiene que hacer peticiones a los nodos exclavos para poder realizar las tareas que se quieran distribuir.

Para ello se tiene que tener una conexion de ssh entre mestro-exclavo para que esta conexion ademas de directa sea segura. Esto requiere una pequeña configuracion:

### Pasos a realizar:
* Creamos las claves publicas y privadas:
    $ ssh-keygen 

    Se da enter en las peticiones que se requieren(no insertando mas proteccion), si se prefiere se puede insertar pero no es necesario en un cluster virtual.

    Genera una clave privada y publica en "/home/hadoop/.ssh/"

* Autorizamos en linux a usar esa clave generada para el nodo1:

    $ cp id_rsa.pub authorized_keys

    El directorio authorized_keys no existe y hay que ponerle ese nombre exacto para que el sistema lo cree y lo localice correctamente.