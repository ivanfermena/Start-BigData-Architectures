# Instalacion de cluster real con varios nodos

Lo que haremos para la generacion de un cluster real es el clonado de nuestro nodo principal y asi se tiene instalado y configurado todo lo esencial.

Pero antes de crear un cluster real con varios nodos lo que haremos es apagar todos los procesos de nuestra maquina virtual para que su apagado sea los mas correcto posible.

    $ stop-yam.sh
    $ stop-dfs.sh

De este modo o que se hace el apagar todos los procesos arrancados de nuestro claster. Tras esto apagamos la maquina virtual.

## Clonar MV

Para esta practica los que haremos es clonar dos veces nuestra maquina virtual, antes de nada hay que generar una nueva tarjeta de red en nuestra maquina virtual. Teniendo asi una para internet y otra para la intranet entre nodos.

* Click derecho en nuestra maquina (nodo 1) -> Settings -> Network -> Adapter 2 -> Marcamos: Enable Network Adapte y seleccionamos "Internal Network"
* Click izquierdo en nuestra maquina virtual (nodo 1) y Clone
* Importante marcar la opcion "Reinitialize the MAC address of all network cards", de este modo tendra una nueva MAC para poder conectarse con el resto de nodos. De nombre ponemos el que queramos => nodo2, nodo3...
* Seleccionamos la opcion de "Full clone".

## Configuracion de red de los nodos

Este paso hay que hacerlo para cada uno de los nodos existentes, el ejemplo sera para el nodo2 pero vale para cualquier nodo clonado exclavo.

1. **Cambiamos el hostname**:
    ```
    $ sudo - root 
    $ hostname nodo2
    ```

2.  **Modificamos el sysconfig**:

    ```
    $ cd /etc/sysconfig
    $ vi network
    ```

    Modificamos la segunda linea cambiando al nodo que determinemos. Por ejemplo de nodo1 -> nodo2

3.  **Insertar redes en hosts**:

    Ahora lo que haremos es en todas las maquinas modificar el archivo hosts insertando todas las direcciones IP de los diferentes nodos:

    ```
    $ vi /etc/hosts
    ```

    Ponemos al final del archivo, borrando la IP que estaba puesta ya:

    ```
    192.168.0.101 nodo1
    192.168.0.102 nodo2
    192.168.0.103 nodo3
    ```

4. **Configuramos el eth del sistema**

    * Ahora tenemos que ir a la parte susperior derecha del escritorio y le damos click izquierdo en las conexiones, dandole a "editar las conexiones".

    * Seleccionamos el tipo interno que hemos creado "eth1" y le damos a editar. Tras esto vamos a la seccion de "Parametros IPv4".

    * Seleccionamos "Manual" para que las maquinas se conecten entre si. Insertamos los siguientes datos adaptados a cada nodo (nodo1 -> 192.168.0.101, nodo2 -> 192.168.0.102 ...):
    
        - Direccion: 192.168.0.101
        - Mascara de red: 255.255.255.0
        - Puerta de enlace: 192.168.0.1

    Le damos a aplicar.

5.  **Si todo es correcto debe aparecer los ordenadores y no la carga de red**.