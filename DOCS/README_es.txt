
         ooooo                     oo     o  o               oo     o
        M"   "Mo                    Mo  oM"  M                Mo  oM"
       M           oM""Mo  oM""Mo    "Mo"    Mo"""o  oM""Mo    "Mo"
       M    """M   MooooMM MooooMM   oMMo    M    "M M    M    oMMo
       "o     oM   M    o  M    o   oM  Mo   M    oM M    M   oM  Mo
        "MoooM"M   "MooM"  "MooM"  M"    "M  M"ooo"  "MooM"  M"    "M

                             Versi�n Generator



| SOBRE GEEXBOX
| ~~~~~

Geexbox es un software que convierte tu ordenador en una m�quina de
reproducir DivX. De hecho, es un CD auto-arrancable que permite ver
pel�culas o escuchar m�sica. Soporta multitud de formatos, tales como avi,
mpeg, divx, ogm, rm, mp3, ogg, dvd, vcd y cdda. Tambi�n soporta algunos
mandos a distancia por IR y salidas de TV para algunas tarjetas. Este archivo
contiene los ficheros necesarios para generar una imagen iso personalizada
de GeexBoX.


| REQUISITOS
| ~~~~~~~~~~

Para generar una iso GeeXboX, necesitas o:
  - un sistema GNU/Linux con mkisofs y mkzftree.
  - un sistema windows.


| PERSONALIZACI�N
| ~~~~~~~~~~~~~~~

El objetivo de esta versi�n generadora es la de personalizar facilmente GeeXboX.

Lo m�s interesante que puedes hacer con esta versi�n es la de construir
una imagen GeeXboX incluyendo una pel�cula. Esta pel�cula se reproducir� 
autom�ticamente al arrancar. S�lo tienes que poner tus pel�culas o ficheros
de sonido y listas de reproducci�n en el directorio iso.

Tambi�n puedes a�adir algunos c�decs propietarios como rv9 o wmv9, simplemente
a�adi�ndolos en el directorio iso/GEEXBOX/codecs. Puedes encontrar estos c�decs
en el paquete http://www2.mplayerhq.hu/MPlayer/releases/codecs/extralite.tar.bz2.
Ficheros �tiles :
  
  * C�decs de Real (usados para reroducir ficheros rv9 por ejemplo) : atrc.so.6.0,
     cook.so.6.0, sipr.so.6.0, drv2.so.6.0, drv3.so.6.0, drv4.so.6.0.
  
  * C�decs Windows Media (wmv9/wma9) : wma9dmod.dll and wmv9dmod.dll.

Tambi�n puedes modificar muchas opciones. Esto se hace editando algunos ficheros
de texto.

* Idioma :
    Puedes seleccionar facilmente tu idioma preferido para el men� editando
    el fichero generator.sh o generator.bat (dependiendo de tu SO). Esto no 
    tiene efecto en el lenguaje del DVD (ver secci�n del MPlayer). Si tu idioma
    no est� disponible, puedes traducir el men� a tu propio idioma simplemente
    creando los archivos language/menu_LANG.conf y language/help_LANG.txt.
	
* Lirc :
    Puedes elegir uno de los controladores soportados editando el fichero
    generator.sh o generator.bat (dependiendo de tu SO). El ATI Remote Wonder
    no es controlado por lirc y esta siempre activado, asi que no tienes que
    modificar nada para su uso. Si quieres modificar la asignaci�n a las teclas
    para tu controlador remoto, mira en el fichero lirc/lircrc_REMOTE.

* MPlayer :
    Aqu� es donde puedes hacer la mayor parte de las configuraciones y ajustes.
    Las opciones se encuentran en el fichero iso/GEEXBOX/etc/mplayer/mplayer.conf.
    Quiz�s quieras modificar opciones como tama�o de fuente del OSD (subfont-text-scale).
    Tambi�n puedes a�adir muchas opciones como idioma por defecto del DVD 
    (ej: alang=es,en). El mejor sitio para encontrarlas es en la pagina man
    de MPlayer, para usuarios de linux (man -l build/MPlayer-*/DOCS/mplayer.1)
    Tambien deberias echar un vistazo a la documentaci�n de Mplayer
    (http://mplayerhq.hu/DOCS/).

* Salida de TV :
    Activando la Salida de TV se consigue con la ayuda de m�ltiples
    programas dedicados a las diferentes marcas de tarjetas.
    Actualmente usamos atitvout para las tarjetas Ati, s3switch para
    las tarjetas S3 y nvtv para las tarjetas Nvidia (y posiblemente
    las intel i810 y las 3dfx. 
    La configuracion de estos programas se realiza en    
    iso/GEEXBOX/etc/tvsettings. Ah� puedes elegir el estandar de TV
    que quieras (pal para Espa�a, ntsc...) y puedes modificar opciones espec�ficas
    para nvtv.

* Red :
    Puedes configurar la red en el fichero iso/GEEXBOX/etc/network.
    Ah� puedes escoger la direcci�n IP usada por GeeXboX ( por defecto
    usa DHCP y si no funciona, pasa a 192.168.0.54.)
    Tambi�n puedes establecer un login y una clave que se usar� para
    conectarse a maquinas windows ( por defecto se conecta an�nimamente)


| GENERACI�N
| ~~~~~~~~~~

Primero hecha un vistazo a la secci�n de personalizaci�n detallada m�s arriba.

Para generar la iso �nicamente tienes que ejecutar en Linux
   ./generator.sh

o bajo windows ejecutando
  generator.bat


| LICENCIA
| ~~~~~~~~

Todos los programas usados por GeeXbox estan protegidos por sus respectivas
licencias. Todos ellos son software libre y muchos estan cubiertos por la
Licencia P�blica General GNU

GeeXbox, entendiendose por todos los scripts que son usados durante el proceso
de construcci�n del mismo, est� cubierto por la Licencia P�blica General GNU
General Public License (GPL).
 

| AUTOR
| ~~~~~~

Aurelien Jacobs  <aurel@geexbox.org>


| GRACIAS ESPECIALES
| ~~~~~~~~~~~~~~~~~~

Benjamin Zores  <ben@geexbox.org>  por sus parches, pruebas, y la p�gina web.


| GRACIAS
| ~~~~~~

Serial Cleaner   <serial.cleaner@gmx.net>  por su parche setcd y soporte para
                                           hauppauge.                                          
Herv� Urbain     <dersie.urbain@wanadoo.fr>  por su soporte para control remoto Logitech.
David Legrand    <david@pcinpact.com>  por prestarnos su ATI Remote Wonder.
Micka�l Beugnier <Mitch@no-log.org>  por el logo de GeexBoX y el dise�o del logo de arranque. 
Andrighetto Riccardo  <geexbox@truzzone.it> por su traducci�n al italiano.
Plom             <tbb.plom@libertysurf.fr>  por su soporte para el control remoto leadtek
Eva Mikulcikova  <evmi@seznam.cz>  por sus traducciones al checo y al eslovaco.
La entera comunidad del software libre, y especialmente a todo el equipo de MPLayer.


