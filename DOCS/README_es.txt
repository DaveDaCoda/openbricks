
         ooooo                     oo     o  o               oo     o
        M"   "Mo                    Mo  oM"  M                Mo  oM"
       M           oM""Mo  oM""Mo    "Mo"    Mo"""o  oM""Mo    "Mo"
       M    """M   MooooMM MooooMM   oMMo    M    "M M    M    oMMo
       "o     oM   M    o  M    o   oM  Mo   M    oM M    M   oM  Mo
        "MoooM"M   "MooM"  "MooM"  M"    "M  M"ooo"  "MooM"  M"    "M



| ACERCA DE...
| ~~~~~~~~~~~~

Geexbox es un software que convierte tu ordenador en una m�quina de
reproducir DivX. De hecho, es un CD auto-arrancable que permite ver
pel�culas o escuchar m�sica. Soporta multitud de formatos, tales como avi,
mpeg, divx, ogm, rm, mp3, ogg, dvd, vcd y cdda. Tambi�n soporta algunos
mandos a distancia IR y las salidas de TV de ciertas tarjetas. Este archivo
contiene los ficheros necesarios para generar una imagen iso personalizada
de GeexBoX.


| REQUISITOS
| ~~~~~~~~~~

Para generar una iso GeeXboX, necesitas:
  - un sistema GNU/Linux con mkisofs y mkzftree.
  - un sistema windows.

Para instalar GeeXboX, necesitar�s:
  - un sistema GNU/Linux con syslinux.

Para construir GeeXboX, te har�n falta algunas utilidades cl�sicas:
  - un sistema GNU/Linux funcionando.
  - el compilador gcc para el lenguaje C.
  - GNU make.
  - el comando patch.
  - el ensamblador nasm.
  - bzip2 y gzip.
  - mkfs.ext2 y mkfs.vfat.
  - la utilidad de descarga wget (no necesaria para todo el paquete GeeXboX).
  - mkisofs y mkzftree para construir la imagen iso.
  - mkzftree para comprimir los archivos en la imagen iso.
  - cdrecord (para tostar la iso).

Y tambi�n 500 megas de espacio libre en disco.


| PERSONALIZACI�N
| ~~~~~~~~~~~~~~~

Cuando GeeXboX est� instalado en un disco duro o es generado, resulta muy
f�cil personalizarlo.

Puedes a�adir algunos c�decs propietarios como rv9 o wmv9, copi�ndolos
en el directorio iso/GEEXBOX/codecs. Puedes encontrar estos c�decs en el
paquete http://www.mplayerhq.hu/MPlayer/releases/codecs/ .

Ficheros �tiles en el paquete de c�decs:
  * C�decs de Real (usados para reroducir ficheros rv9 por ejemplo) : atrc.so.6.0,
     cook.so.6.0, sipr.so.6.0, drv3.so.6.0, drv4.so.6.0.
  * C�decs de Windows Media (wmv9/wma9) : wma9dmod.dll y wmv9dmod.dll.

Tambi�n puedes modificar muchas opcionesa trav�s de la edici�n de algunos
ficheros de texto.

* Idioma :
    Puedes seleccionar f�cilmente tu idioma de men� favorito editando
    el fichero GEEXBOX/etc/lang. Esto no tiene efecto en el lenguaje del DVD
    (mira en la secci�n de MPlayer). Si tu idioma no est� disponible, puedes
    traducir el men� a tu propio idioma, lo que conlleva la creaci�n de los
    archivos GEEXBOX/etc/mplayer/menu_LANG.conf y
    GEEXBOX/usr/share/mplayer/help_LANG.txt.

* MPlayer :
    Aqu� es donde puedes hacer la mayor parte de las configuraciones y ajustes.
    Las opciones se encuentran en el fichero packages/MPlayer/mplayer.conf.
    Quiz�s quieras modificar opciones como tama�o de fuente del OSD
    (subfont-text-scale). Tambi�n puedes a�adir muchas opciones como idioma
    por defecto para DVD (ej: alang=es,en). El mejor sitio para encontrar
    estas opciones es en la pagina man de MPlayer, para usuarios de linux
    (man -l build/MPlayer-*/DOCS/mplayer.1). Tambien deberias echar un vistazo
    a la documentaci�n de MPlayer (http://mplayerhq.hu/DOCS/).
    Otro archivo que quiz� quieras modificar es packages/MPlayer/menu.conf.
    Puedes quitar elementos del men� que no necesites, o, por ejemplo,
    traducirlos a tu propio idioma.
    El ultimo archivo que puedes mirar es packages/MPlayer/build, que contiene
    la selecci�n de opciones que est�n compiladas en MPlayer.

* Salida de TV :
    La activaci�n de la salida de TV se consigue con la ayuda de m�ltiples
    programas dedicados a las diferentes marcas de tarjetas.
    Actualmente usamos atitvout para las tarjetas Ati, s3switch para las
    tarjetas S3 y nvtv para las tarjetas Nvidia (y posiblemente las intel
    i810 y las 3dfx). La configuracion de estos programas se realiza en
    config/tvout. Ah� puedes seleccionar el estandar de TV que quieras
    (pal para Espa�a, ntsc en Iberoam�rica...) y modificar otras opciones
    espec�ficas de nvtv.

* Lirc :
    Puedes elegir uno de los controladores soportados editando el archivo
    GEEXBOX/etc/remote. Lirc no puede controlar ATI Rempote Wonder y est�
    siempre activado, asi que no tienes que modificar nada para usarlo.
    Si quieres cambiar la asignaci�n de teclas para el mando a distancia,
    mira en el fichero GEEXBOX/etc/lirc/lircrc_REMOTE.

* Red :
    Puedes configurar la red en el archivo GEEXBOX/etc/network.
    Ah� puedes escoger la direcci�n IP usada por GeeXboX (por defecto
    se usa DHCP, y si no funciona, la IP cambia a 192.168.0.54.). Tambi�n
    puedes establecer un usuario y contrase�a para conectarse a recursos
    compartidos en m�quinas windows (por defecto se conecta �nicamente a los
    recursos que permitan conexiones an�nimas).


| GENERACI�N
| ~~~~~~~~~~

Primero hecha un vistazo a la secci�n de personalizaci�n detallada m�s arriba.

Para generar la iso �nicamente tienes que ejecutar en Linux
   ./generator.sh

o
  generator.bat
bajo windows.


| INSTALACI�N
| ~~~~~~~~~~~

Lo primero que necesitas es crear una partici�n FAT16 con unos 16 MB libres.

A partir de aqu�, puedes instalar GeeXboX bajo Linux ejecutando
  ./installator.sh
Responde a todas las preguntas y ten mucho cuidado con ellas. L�elas dos veces
y, si no entiendes alguna, para la instalaci�n.


| COMPILANDO
| ~~~~~~~~~~

Lo primero es echar un vistazo a la secci�n de configuraci�n, m�s arriba (al
menos, la parte general y la que se refiere al tostado en CD).

A continuaci�n, puedes crear la iso b�sicamente con:
  make
O puedes quemarla directamente en CD con:
  make burn

Cuando se haya terminado, puedes ahorrar espacio de disco limpiando el �rbol
de compilaci�n:
  make clean
o haciendo una limpieza total, incluso borrando las fuentes descargadas:
  make distclean

Existen tambi�n otros comandos m�s avanzados si quieres enredar en las tripas
de GeeXboX:
  scripts/get package        # descargar el paquete
  scripts/unpack package     # desempaqueta y prepara el paquete
  scripts/build package      # construye el paquete
  scripts/install package    # instala el paquete con el prefijo $INSTALL
  scripts/clean package      # limpia el �rbol de fuentes del paquete
  make exec                  # lanza directamente GeeXboX en una jaula
                             # AVISO: esta caracter�stica es �ltamente experimental
                             # �sala a tu propio riesgo.

Si has hecho una versi�n modificada de GeeXboX, puedes construir f�cilmente un
peque�o tar.bz2 con:
  make dist
o un tar completo (conteniendo todos los fuentes) con:
  make fulldist
o un generador geexbox con:
  make generator
o un instalador geexbox con:
  make installator


| CONFIGURACI�N
| ~~~~~~~~~~~~~

* Opciones globales:
    �ste es el primer apartado en el que debes fijarte antes de intentar
    compilar GeeXboX. Se encuentra en el archivo config/options, y deber�a
    explicarse por s� mismo. En este fichero puedes seleccionar la familia
    de tu CPU, el tema a usar, y si quieres utilizar fuentes truetype o no.
    Adem�s, deber�as modificar la configuraci�n de la grabadora de CD para
    poder grabar directamente la ISO.

* Linux:
    El archivo packages/linux/linux.conf es una configuraci�n cl�sica de Linux.
    Puedes editarlo a mano, o tambi�n puedes ejecutar scripts/unpack linux
    y hacer make menuconfig -C build/linux-* (o utilizar el m�todo que
    prefieras en vez de menuconfig). Es conveniente que hagas una copia de
    seguridad de build/linux-*/.config en packages/linux/linux.conf.
    Lo m�s "dif�cil" que puede ocurrir es mantener tama�o del kernel lo
    suficientemente reducido como para que quepa en una imagen de un disquete
    de arranque.

* Lirc:
    Lirc te permite controlar GeeXboX a trav�s de un mando a distancia. Lo
    primero que debes hacer es escoger el archivo que describe tu mando en
    concreto en build/lirc-*/remotes (despues de hacer scripts/unpack lirc) y
    a�adirlo a packages/lirc/install. A partir de aqu�, escoge un dispositivo
    (por defecto es /dev/ttyS0, o COM1) y el driver lirc y col�calos en un
    archivo con el nombre packages/lirc/lircd_$REMOTE. Entonces podr�s escoger
    la asignaci�n de teclas en packages/lirc/lircrc_$REMOTE. En cada asignaci�n
    tienes que seleccionar un bot�n (coge los nombres del archivo de definici�n
    del mando a distancia) y asociarle una acci�n. Esta acci�n pertenece a
    MPlayer, y puedes encontrar un listado en
    build/MPlayer-*/DOCS/documentation.html#commands.


| HACKING
| ~~~~~~~

El primer sitio donde debes mirar es en el script de inicializaci�n.
De hecho, existen dos scripts de inicializaci�n. El primero est� en
packages/initrd/linuxrc, aunque no deber�as necesitar modificarlo.
El segundo se encuentra en config/init y es donde puedes personalizar.

Lo siguiente que podr�a interesarte es la creaci�n de un nuevo "paquete".
Un paquete consiste en una gran cantiad de scripts que han de seguir algunas
reglas. Todos los scripts deben funcionar sobre un directorio llamado como
el programa que quieres empaquetar, dentro del directorio packages.
Una lista de scripts que puedes crear:
 - url: s�lo una lista de urls para conseguir los fuentes del programa.
 - unpack: qu� hacer despu�s de desempaquetar los fuentes. Por ejemplo,
            puedes modificar algunos ficheros de configuraci�n. �sto no
            incluye aplicar parches.
 - need_build: es llamado cuando el paquete ha terminado de compilarse, con
            el objetivo de estar seguros de que no necesita volver a cons-
            truirse. Debe borrar el archivo .stamps/"nombre del paquete"/build,
            si el paquete debe ser recompilado.
 - build: todos los pasos necesarios para compilar el programa.
 - install: todos los pasos necesarios para instalar el programa. El prefijo
            de instalaci�n debe ser $INSTALL.

Cuando un archivo de las url se llama patch-nombre_del_programa-... se aplica
autom�ticamente a los fuentes desempaquetados del programa.

Adem�s, debes recordar que el software que corre en GeeXboX debe ser compilado
con el wrapper gcc de uClibc.

Finalmente, el mejor modo de hacer un paquete es observar c�mo est�n hechos
otros paquetes.


| LICENCIA
| ~~~~~~~~

Todos los programas usados por GeeXbox estan protegidos por sus respectivas
licencias. Todos ellos son software libre, y la mayor�a est�n cubiertos por la
Licencia P�blica General GNU (GPL).
El propio GeeXboX, incluyendo todos los scripts que son utilizados en el
proceso de construcci�n y compilaci�n, est�n cubiertos por la Licencia P�blica
General GNU (GPL).
