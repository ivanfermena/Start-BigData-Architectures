## Instalacion de Nodo Maestro

En un comienzo las practicas se haran con un nodo maestro y despues se iran insertando nodos esclavos para el aumento del cluster.
Para la instalacion del nodo maestro se usaran programas de vistualizacion (maquinas virtuales) debido a la falta de quipos reales para hacer un cluster completo.

### Programas:
- **Oracle VitualBox** -> Programa que se usa para la virtualizacion de maquinas virtuales. Simula un ordenador con unas caracterisiticas especificas. Link de descarga: [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads). Seleccionamos la version para nuestro SO (Windows hosts, OS X hosts...)
- **CentOs 6** -> Distribucion de Linux basada en RedHat, se usara esta ya que las distribuciones empresariales son las mas idoneas para el uso de clusters distribuidos. Usamos CentOS 6 debido a la implemetacion total con los programas a usar en el curso, evitando problemas. Se puede hacer perfectamente con CentOS 7. Link de descarga: [CentOS](https://wiki.centos.org/Download). Instalaremos el DVD y en el caso de que vengas dos discos es solo necesario con DVD1.

Ademas internamente en las maquinas virtuales se instalaran los diferentes programas como Hadoop.

### Configuracion VB:
A la hora de configurar la maquina virtual se creara una para su posterior clonado.

1. Arrancamos VirtualBox y iniciamos una nueva virtualizacion. Con el nombre que queramos seleccionamos la distribucion Linux y version RedHat de 64bits.
2. Seguimos una instalacion por defecto cambiando: Ram -> 4Gb minimo, almacenamiento dinamico y seleccionando unos 15-30Gb.
3. Abrimos la configuracion de esa maquina y seleccionamos: 
    - General -> Advanced => Bidirecional en las dos secciones. 
    - Display -> Video Memory => 32 MB
    - Network => "NAT"
    Remarcar que la configuracion es dependiente de nuestro ordenador, aumentando si se tiene un ordenador con mejores especificaciones. Se aconseja no poner menos por los recursos que usan los programas a usar.
4. Arrancamos la maquina virtual y seleccionamos la iso de CentOS descargada antes.
5. Se sigue una instalacion comun de un SO, seleccionando idiomas, password de root, nombre usuario...

### Guest Additions:

Cuando se tenga todo instalado se debe configurar los Guest Additions:

Las Guest Additions son configuracions asociadas a la maquina virtual de VirtualBox que sriven para poder tratar libremente con los drivers de la maquina, por ejemplo poder sacar el raton libremente de la pantalla o la resolucion de pantalla.

1. Seleccionaremos del menu de la maquina arrancada Devices -> Insert Guest Additions CD... Esto nos insertara un disco en el escritorio. Si no se puede sacar el raton seleccionamos "Ctrl Derecho" del teclado o "Alt + Ctrl + Sup", se da a cancelar y ya se puede seleccionar (Casos en los que no se tenga Ctrl derecho).
2. Te saldra una pantalla a la que tienes que dar cancelar. Tras esto te vas a Aplicaciones -> Herramientas del sistema -> Terminal
3. En el Terminal: 
    - su - root
    - cd /media/VBOXADDITIONS_XXXXXXXX donde las "X" sera la version que este disponible.
    - ./VBoxLinuAddiotions.run
4. Si no se ha instalado bien (lo mas seguro) debe instalar un paquete del kernel de linux: 
    - yum install kernel-devel-XX.XXXXXXXXXXX... Donde "X" es la version que le aperece en el error. Se copia y se pega despues del install.
    - yum install gcc (Compilador de c)
5. Despues de estos errores se vuelve a lanzar el ejecutable: ./VBoxLinuAddiotions.run
6. Reiniciamos la maquina virtual.