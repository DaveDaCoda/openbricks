
         ooooo                     oo     o  o               oo     o
        M"   "Mo                    Mo  oM"  M                Mo  oM"
       M           oM""Mo  oM""Mo    "Mo"    Mo"""o  oM""Mo    "Mo"
       M    """M   MooooMM MooooMM   oMMo    M    "M M    M    oMMo
       "o     oM   M    o  M    o   oM  Mo   M    oM M    M   oM  Mo
        "MoooM"M   "MooM"  "MooM"  M"    "M  M"ooo"  "MooM"  M"    "M

                             Generator Version



| AVANT PROPOS
| ~~~~~~~~~~~~

La GeeXboX est une sorte "divx box" logicielle. En fait, il s'agit d'un CD
bootable qui vous permet de regarder des films ou d'�couter de la musique.
Il supporte de nombreux formats tels que avi, mpeg, divx, ogm, rm, mp3, ogg,
dvd, vcd et cdda. GeeXboX supporte aussi certains types de t�l�commandes
infra-rouge et les sorties TV de certaines cartes graphiques.
Cette archive contient tous les fichiers n�cessaires pour g�n�rer une image
iso personnalis�e de la GeeXboX


| PREREQUIS
| ~~~~~~~~~

Pour g�n�rer une iso GeexBoX vous devez poss�der l'un des syt�mes suivants:
  - GNU/Linux avec mkisofs et mkzftree.
  - Windows.


| PERSONALISATION
| ~~~~~~~~~~~~~~~

Le but du g�n�rateur est de personnaliser facilement sa GeeXboX.

La chose la plus interessante que vous puissiez faire et de g�n�rer une image
comportant une vid�o compl�te qui sera lu automatiquement au boot. Vous avez
juste � copier vos vid�os (ou vos fichiers sons) et vos playlists dans le
repertoire iso.

Vous pouvez aussi ajouter des codecs propri�taires comme le rv9 ou le wmv9, en
les copiant simplement dans le r�pertoire iso\GEEXBOX\codecs. Ces codecs se
trouvent ici:
http://www2.mplayerhq.hu/MPlayer/releases/codecs/extralite.tar.bz2.

Les fichiers utiles sont les suivants:

  * Codecs Real (pour le rv9 par exemple) : atrc.so.6.0, cook.so.6.0,
      sipr.so.6.0, drv2.so.6.0, drv3.so.6.0 et drv4.so.6.0.
  * Codecs Windows Media (wmv9/wma9) : wma9dmod.dll et wmv9dmod.dll.

Vous pouvez modifier d'autres options en �ditant simplement des fichiers
textes.

* Langue :
    Choisissez la langue de vos menus en �ditant le fichier generator.sh ou
    generator.bat (en fonction de votre OS). Cela n'as pas d'effets sur la
    langue du DVD (voir section MPlayer). Si votre langue n'est pas disponible,
    vous pouvez toujours traduire un menu. Il suffit de re-cr�er les fichiers
    language/menu_LANG.conf and language/help_LANG.txt.

* Lirc :
    Choisissez la t�l�commande support� en �ditant le fichier generator.sh ou
    generator.bat (en fonction de votre OS). Si vous utilisez la t�l�commande
    ATI Remote Wonder qui n'est pas support�e par lirc, il n'y a rien �
    modifier car elle est activ�e par d�faut. Si vous d�sirez modifier le
    mappage des touches reportez vous au fichier lirc/lircrc_REMOTE.

* MPlayer :
    C'est ici que se font la plupart des configurations et autres bidouilles.
    Les options se situent dans le fichier iso/GEEXBOX/etc/mplayer/mplayer.conf
    Il est possible de changer des options comme la taille des police de l'OSD
    (subfont-text-scale) et beaucoup d'autres choses telles que la langue par
    d�faut de lecture des DVD (ex: alang=fr,en). La meilleur fa�on de
    comprendre ces options est, pour les utilisateurs de Linux, de se r�f�rer
    au MAN de MPlayer (man -l build/MPlayer-*/DOCS/mplayer.1). D'autres
    informations sont aussi disponibles sur la documentation officielle
    (http://mplayerhq.hu/DOCS/).

* Sortie TV :
    Activer la sortie TV se fait au moyen de nombreux petits utilitaires d�di�s
    chacun � une marque carte graphique. Nous utilisons actuellement atitvout
    pour les cartes ATI, s3switch pour les cartes S3 et nvtv pour les cartes
    nVidia (ce qui peut aussi marcher abec les cartes i810 et 3dfx). La
    configuration de ces programmes se fait dans iso\GEEXBOX\etc\tvsettings.
    Vous pouvez y choisir le standard que vous utilisez (pal, secam...) et y
    modifier les options sp�cifiques du nvtv.

* R�seau :
    Le r�seau est configurable au niveau du fichier iso\GEEXBOX\etc\network.
    Ici vous reglerez l'adresse IP de la GeeXboX (qui par d�faut cherche un
    serveur DCHP ou prend l'IP 192.168.0.54 si elle n'en trouve pas). Il est
    aussi possible de lui assigner un login est un mot de passe (par d�faut,
    la GeeXboX ne peut se connecter que sur des partages anonymes).


| GENERATION DE L'ISO
| ~~~~~~~~~~~~~~~~~~~

Avant tout, jetez un oeuil sur la section personalisation juste au dessus

Sous Linux, l'ISO est g�n�r�e en lan�ant la commande suivante:
  ./generator.sh
et sous Windows:
  generator.bat


| LICENSE
| ~~~~~~~

Tous les programmes utilis�s par GeeXboX sont prot�g�s par leurs licenses
respectives. Tous ces logiciels sont libres et, pour la plupart, prot�g�s par
une licence GPL (License Publique G�n�rale)
La GeeXboX elle-m�me, c'est � dire tous les scripts utilis� et le syst�me
de compilation, est couvert par la licence GNU-GPL.


| AUTEUR
| ~~~~~~

Aurelien Jacobs  <aurel@geexbox.org>


| REMERCIMENTS PARTICULIERS
| ~~~~~~~~~~~~~~~~~~~~~~~~~

Benjamin Zores  <ben@geexbox.org>           pour les patches, les tests
                                            et le site web


| REMERCIMENTS
| ~~~~~~~~~~~~

Serial Cleaner   <serial.cleaner@gmx.net>   pour les patches
                                            et la t�l�commande hauppauge

Herv� Urbain     <dersie.urbain@wanadoo.fr> pour la t�l�commande logitech.
David Legrand    <david@pcinpact.com>       pour la t�l�commande ATI Remote Wonder.
Micka�l Beugnier <Mitch@no-log.org>         pour les logo et bootlogo de la GeeXboX.
Andrighetto Riccardo  <geexbox@truzzone.it> pour la traduction Italienne.
Plom             <tbb.plom@libertysurf.fr>  pour la t�l�commande leadtek.
Eva Mikulcikova  <evmi@seznam.cz>           pour les traduction tch�que et slovaque.
Nicolas Forgeard <nicephore17@yahoo.fr>     pour la version fran�aise du LISEZMOI

La communaut� du Libre et principalement l'�quipe de MPlayer

