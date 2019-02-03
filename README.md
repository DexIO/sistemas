## 4. Gestión de sistemas de archivos mediante comandos.

Los archivos en Linux pueden ser gestionados de forma gráfica, pero nos centraremos en la forma mas tradicional mediante el uso de comandos en la terminal. 

Entre todos los comandos que existen cabe destacar los siguientes:

* - pwd (print working directory)

Nos indica cuál es el directorio en el que estamos trabajando.

* - ls (list)

Listado de los archivos y directorios contenidos en el directorio actual.

   * - ls /etc
                Pasándole la ruta de un directorio, se listará el contenido del mismo.
  
   * - ls -a

Muestra todos los archivos del directorio actual (incluido los ocultos).

   * - ls -l

Se muestran los archivos del directorio actual en formato largo (con permisos propietario, tamaño, fecha de modificación, etc).

   * - ls -lh

Añadiendo el parámetro ‘h’ se muestra el tamaño de archivos y directorios.

   * - ls -R

Se muestra el contenido de todos los subdirectorios.

   * - ls -i ‘fichero’

Muestra el número de inodo del fichero dentro del sistema de archivos.

Cabe destacar que los diferentes parámetros se pueden combinar de múltiples maneras y en cualquier orden. Por ejemplo:    ‘ls -laR’   o   ‘ls -l -a -R’, siendo igual de válidas las 2 formas.

* - cd (change directory)

Esta orden permite cambiar de un directorio a otro dentro de la estructura de directorios que poseamos.

En caso de querer situarnos directamente en el directorio HOME del usuario usaremos:    ‘cd’   o   ‘cs~’.

* - mkdir (make subdirectory)

Esta orden crea un nuevo directorio.

* - rmdir (remove directory)

Permite eliminar un directorio vacío.

Usando el comando ‘rm-rf’ se puede eliminar un directorio y sus subdirectorios (aunque estos tengan contenido). El parámetro ‘-r’ elimina los subdirectorios (elimina de manera recursiva) y con ‘f’ realizamos todas las confirmaciones de eliminación.

* - tree

Muestra de forma gráfica la estructura de un directorio (requiere instalación previa).

* - cat ‘léeme’ (concatenate)

Muestra el contenido del fichero indicado como parámetro (’mifichero’).

* - touch ‘mifichero’

Crea un fichero vacío con el nombre que le pasamos como parámetro (’mifichero’).

* - cp (copy)

Este comando dispone de 2 funcionalidades:

   * - Copiar uno o varios ficheros de un directorio a otro 

(ejemplo: ‘cp ./doc1 /home/usuario/’).

   * - Copiar el fichero origen con un nuevo nombre si le indicamos ese nombre en el destino (ejemplo: ‘cp doc1 doc2’).

Con el parámetro ‘-v’ se muestra por pantalla los archivos que se están copiando en tiempo real.

* - rm (remove)

Permite eliminar un fichero o un directorio.

Utilizando el parámetro ‘-r’  se eliminan también los subdirectorios (elimina de manera recursiva) y con el parámetro ‘f’ realizamos todas las confirmaciones de eliminación (de modo que sería: ‘rm -rf’).

* - mv (move)

Permite mover un fichero de un directorio a otro (ejemplo: ‘mv dir1/doc1 /home’).

También renombra el archivo si lo dejamos en el mismo directorio o si al indicarle el destino utilizamos un nombre distinto (ejemplo: ‘mv doc1 doc2’).

* - dirname

Muestra la ruta de directorios de una indicada por parámetro, eliminando el nombre del archivo (ejemplo: ‘dirname /home/usuario/.bashrc’). 

* - basename

Muestra el nombre del archivo de una ruta indicada como parámetro (ejemplo: ‘basename /home/usuario/.bashrc’). 

* - find

Este comando permite buscar un fichero dentro del árbol de directorios del sistema (aunque presenta un uso más amplio).

Con el parámetro ‘-name’ indicamos el nombre del fichero a buscar y con ‘-size’ los buscamos por el tamaño que le indicamos (ejemplos: ‘find /etc -size 50b’, ‘find /etc -name modprobe.conf’).

* - which

Permite localizar la ruta del fichero ejecutable o comando que se le pasa como parámetro (se ejecutaría en el entorno actual).

* - whereis

Este comando localiza todas las rutas donde se pueda encontrar el fichero ejecutable o comando que se le pasa como parámetro. 

## 5. Gestión de enlaces o accesos directos.

En Linux se pueden crear dos tipos de enlaces o accesos directos, los enlaces duros (también conocidos como enlaces físicos o enlaces fuertes) y los enlaces blandos (también conocidos como simbólicos o débiles).

### Enlaces duros

#### ¿Qué son?

El término hace referencia a aquellos archivos que apuntan al mismo contenido en la unidad de almacenamiento que un archivo de origen, disponiendo ambos del mismo inodo (número identificativo que tiene asignado cada fichero y carpeta). 
En resumen, se trata de un archivo (archivo original, con un inodo único) que se identifica con varios nombres. De esta forma cualquier cambio que se realice utilizando cualquiera de los nombres quedará reflejado en el archivo.
En la siguiente imagen se puede apreciar lo anteriormente explicado:
  
#### ¿Cómo se crean? 

Este tipo de enlaces se crean con el siguiente comando:

	ln ‘nombrefichero’ ‘nombreenlaceduro’ 

Ejemplo: 

	‘ln doc1 doc2’ 

de esta forma estamos creando un enlace duro llamado ‘doc2’ del archivo llamado ‘doc1’ 

Se puede comprobar que dos archivos son enlaces físicos examinando su inodo mediante el comando:

	ls -i

### Enlaces blandos

#### ¿Qué son?

Los enlaces simbólicos son lo más similar a los accesos directos en Windows, ya que a diferencia de los enlaces duros estos apuntan al nombre de un archivo y este archivo apunta al contenido almacenado en la unidad de almacenamiento, como es apreciable en la siguiente imagen explicativa:  
  
###### Insertar imagen  
  
####   ¿Cómo se crean? 

Este tipo de enlaces se crean con el mismo comando que el visto anteriormente pero añadiendo el parámetro ‘-s’. En este caso se pueden especificar directorios diferentes (atención al uso de rutas relativas en el destino).

Ejemplos: 

		‘ln -s doc1 doc2’, 
		 ‘ln -s /home/usuario/examples /home/usuario/Escritorio/ejemplos’,
     ‘ln -s /home/usuario/examples ../ejemplos’.

## 6. Estructura de directorios del sistema operativo

Existen varios tipos de directorios en Linux

### Directorios compatibles

Son aquellos que se pueden acceder desde distintos equipos

	Ej.: /var/mail, /opt, /home, /var/www/html, /usr

### Directorios no compatibles

Son aquellos ditectorios que no se pueden compartir y su acceso y modificación están limitados al administrador del sistema

	Ej.: /etc, /boot, /var/run

### Directorios variables

Son aquellos directorios que pueden ser modificados y pueden variar su contenido sin la intervención del administrador del sistema

	Ej.: /var/log/messages, /var/mail, /var/spool/news, /home, /var/run

### Directorios estáticos

Son aquellos directorios que contienen archivos que solo pueden ser modificados con la intervención del sistema

	Ej.: /etc/password, /etc/shadow, /usr, /opt, /etc, /boot, /bin, /sbin

Los directorios mas destacables son:

### Directorio raíz (/)

Es el directorio principal, desde aquí se ramifican todos los directorios

### Directorio /bin

Se almacenan los datos ejecutables necesarios para el funcionamiento del sistema

### Directorio /boot

En el se encuentran todos los archivos necesarios para que el ordenador arranque, salvo los archivos de configuración

### Directorio /dev

Aquí se almacenan los datos acerca de nuestro hardware

### Directorio /etc

Contiene los archivos de configuración del sistema operativo

### Directorio /home

Aquí se encuentran alojados todos los archivos personales de cada usuario

### Directorio /lib

Contiene bibliotecas compartidas para ejecutar binarios de los directorios /bin y /sbin

### Directorio /mnt

Aquí se encuentran los puntos de montaje de distintos dispositivos de almacenamiento (generalmente discos duros y particiones)

### Directorio /media

Aquí se encuentran los puntos de montaje de distintos dispositivos de almacenamiento (generalmente memorias USB, lectores CD-ROM o similares)	

### Directorio /opt

Aquí se almacenan los programas que no vienen por defecto con el sistema operativo

### Directorio /proc

Se almacena información de procesos y aplicaciones en ejecución

### Directorio /root

Es el directorio /home del administrador del sistema

### Directorio /sbin

Es la variante root del directorio /bin

### Directorio /srv

Se almacenan datos que usan x servidores que se encuentren instalados en el equipo

### Directorio /tmp

Se almacenan archivos temporales de programas que posteriormente son eliminados por el sistema operativo

### Directorio /usr

Contiene la gran mayoría de programas instalados en el sistema

### Directorio /var

Contiene datos variables y temporales de los registros del sistema (Logs)

### Directorio /sys

Contiene información similar al directorio /proc, aquí encontramos información sobre el kernel del sistema

### Directorio /lost+found

Aquí se encuentran archivos y ficheros necesarios para recuperar datos en caso de una posible caída del sistema operativo

## 7. Búsqueda de información del sistema mediante comandos.

### Información del sistema (software)

Para mostrar Información del sistema podemos usar el siguiente comando:

	uname

Para listar los usuarios que han iniciado sesión en el sistema en tiempo real usamos el siguiente comando:

	who

Para mostrar información relacionada con la configuración de red usamos el siguiente comando:
	
	ifconfig
	
### Información del sistema (hardware)

Para mostrar un listado con los componentes físicos usamos el siguiente comando:

	sudo lshw	


## 8.Identificación del software instalado

Si queremos saber los programas que tenemos instalados en nuestro Ubuntu tan solo tenemos que abrir una Terminal y escribir el siguiente comando:

		dpkg –get-selections

Dependiendo la version, te aparecera una lista con todos los programas o solo los ultimos instalados.

Ademas del uso del comando anterior, se pueden ver entrando en el icono de software de Ubuntu y podemos añadir filtros. En esa misma pantalla hay un boton ‘Instaladas’ que, si pulsamos, nos mostrara las aplicaciones instaladas en el pc.


## 9.Montaje y desmontaje del dispositivo del sistema operativo

Para montar y desmontar un dispositivo de Linux, se puede hacer de 2 formas distintas, grafica y manualmente.

Para montar y demontar un disco graficamente, solo necesitamos entrar en ‘Discos’ y seleccionamos el disco que queramos montar/desmontar. Si queremos intalarlo, le daremos al triangulo que aparece en el lado derecho y, si lo que queremos es desmontarlo, le daremos al cuadrado.

Para montar/desmontar manualmente, abriremos el terminal y seguiremos la guia del siguiente video:

		https://www.youtube.com/watch?v=TO7SrGv2RWk





## 10. Permisos


### ¿Cómo funcionan los permisos en Linux?
En Linux todos los ficheros y directorios pertenecen a un usuario y al grupo primario del mismo (es decir, cuando se crea un fichero o directorio este pertenece al usuario creador y a su grupo principal).
Cuando visualizamos la información de permisos sobre un fichero (con comando de listado como ‘ls -l’, los cuales se explican en el apartado 4) se nos mostrará como se puede observar en el siguiente ejemplo:
  
Como se analiza en la imagen la primera parte hace referencia al tipo de archivo, existiendo entre otros lo siguientes:
  
Como se puede observar en la primera imagen los permisos de dividen en 3 (lectura, escritura y ejecución), siendo estos indicados en orden para el usuario propietario, el grupo y otros. Estos permisos se pueden otorgar en 3 formatos (en binario, en octal o de manera simbólica indicando con las letras de cada permiso: ‘r’, ‘w’, ‘x’ o ‘-’ en caso de no querer otorgar el permiso), como se puede observar en la siguientes tablas de equivalencias:    

Entre octal y binario la equivalencia y la lectura será de la siguiente manera:  

### Gestión de permisos 
Aunque la gestión de permisos en Linux se puede realizar de forma gráfica nos vamos a centrar en la gestión mediante el uso de comandos en la terminal, entre estos cabe destacar los siguientes comandos:

* - chmod (change mode)
Este comando nos permitirá realizar cambios de permisos de protección sobre un fichero o directorio. Para usarlo debemos indicar las iniciales del usuario o grupo al que va dirigidos (siendo ‘u’ para el usuario propietario, ‘g’ para el grupo primario del usuario, ‘o’ para el resto de usuarios y ‘a’ para todos los usuarios), con ‘+’ o ‘-’ indicaremos si deseamos añadir o quitar los permisos que le indicamos y con ‘=’ asignaremos solo los permisos indicados (eliminando el resto de permisos del usuario o grupo, si los tuviera).

Ejemplos (también se podrían realizar con el formato binario y octal como indicamos en el apartado anterior): ‘chmod u+rw atracos’, ‘chmod ug+r’, ‘chmod ug=r’.

* - chown (change owner)
Con este comando podemos cambiar el usuario propietario de un fichero. Para usarlo tendremos que indicar el usuario que va a ser propietario y el objeto al que se le ve a establecer la propiedad.

Ejemplo: ‘chown pepe /home/atraco’.

* - chgrp (change group)
                Este comando nos permite modificar el grupo propietario de un fichero.
Para usarlo tendremos que indicar dos parámetros, el grupo que va a ser propietario y el objeto al que se le va a establecer la propiedad.

Ejemplo: ‘chgrp delincuentes pruebas’ (al fichero ‘pruebas’ le hemos asignado como nuevo grupo propietario al grupo ‘delincuentes’).

* - umask (user mask)
Cuando se crea un nuevo fichero a este se le es asignado una serie de permisos de manera automática (debido a la máscara de permisos, la cual se los asigna con el valor octal a la hora de aplicarlos).
Este comando nos permitirá conocer el valor por defecto de dicha máscara y en caso de querer modificarlo solo tendremos que insertar un valor en octal después de la instrucción (ejemplo: ‘umask 057’).

## 11. Ficheros de logs y de configuración del sistema

El sistema de logs se inicia con el siguiente script ubicado en:
	
	/etc/init.d/sysklogd

Este script engloba logs del sistema (syslogd) y logs del kernel (klogd)

Estos logs se guardan en archivos ubicados en el directorio:

	/var/log

Una gran parte de programas gestiona sus propios logs, estos se almacenan en:

	/var/log/<programa>

Los logs se van comprimiendo para evitar que se vuelvan excesivamente largos

Para monitorizar los logs por consola, usamos el siguiente comando

	tail

Estos también se pueden visualizar mediante un entorno gráfico, para ello existen diferentes programas que, según la distribución de linux que uses, puede que venga preinstalada en tu equipo.

Algunos ejemplos son KSystemLog (Es el monitor de logs del entorno de escritorio KDE), GNOME-System-Log (monitor de logs del entorno de escritorio GNOME), XLogmaster (monitor de logs de GNU) y Xwatch (monitor de logs para las librerías X)


## 12.Administracion de usuarios y grupos

Para crear usuarios en Linux necesitaremos el comando useradd, escribiendo en el terminal:
		sudo useradd juan
Si queremos que haya un comentario podemos añadir:
		sudo useradd -d /usr/juan -s /bin/csh -u 800 -c "Juan Perez Hernandez" juan
Para modificar el usuario, deberemos usar usermod de la siguiente forma:
		sudo usermod -l sego sergio
Si lo que queremos es eliminar el usuario, escribiremos en el terminal:
		sudo userdel sergio
Para crear un grupo utilizaremos el comando groupadd de la siguiente forma:
		sudo groupadd nombreDeGrupo
Para modificar el grupo:
		 sudo groupmod -g 2000 profesores

Y para eliminar:
		sudo  groupdel profesores

Para añadir o eliminar usuarios del grupo, se utilizaran los comandos:
		sudo adduser juan profesores
		sudo deluser juan profesores
