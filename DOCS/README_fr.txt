
         ooooo                     oo     o  o               oo     o
        M"   "Mo                    Mo  oM"  M                Mo  oM"
       M           oM""Mo  oM""Mo    "Mo"    Mo"""o  oM""Mo    "Mo"
       M    """M   MooooMM MooooMM   oMMo    M    "M M    M    oMMo
       "o     oM   M    o  M    o   oM  Mo   M    oM M    M   oM  Mo
        "MoooM"M   "MooM"  "MooM"  M"    "M  M"ooo"  "MooM"  M"    "M




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

Pour g�n�rer une iso GeeXboX vous devez poss�der l'un des syt�mes suivants:
  - GNU/Linux avec mkisofs et mkzftree.
  - MAC OS X avec mkisofs et mkzftree.
  - Windows.

Pour installer la GeeXboX, vous aurez besoin :
  - un syst�me GNU/Linux avec SysLinux.

Pour construire votre propre GeeXboX, vous n�cessiterez les outils classiques :
  - un syst�me GNU/Linux op�rationnel.
  - Le compilateur C GCC.
  - GNU make
  - La commande patch.
  - L'assembleur nasm.
  - bzip2 et gzip.
  - mkfs.ext2 et mkfs.vfat
  - L'outil de t�l�chargement wget (non n�cessaire pour le paquetage 
  GeeXboX complet).
  - mkisofs et mkzftree pour construire l'image ISO.
  - mkzftree pour compresser les fichiers de l'image ISO.
  - cdrecord (pour graver l'image).

Et environ 1.2 Go d'espace disque disponible.


| PERSONALISATION
| ~~~~~~~~~~~~~~~

Le but du g�n�rateur est de personnaliser facilement sa GeeXboX.

La chose la plus interessante que vous puissiez faire et de g�n�rer une image
comportant une vid�o compl�te qui sera lu automatiquement au boot. Vous avez
juste � copier vos vid�os (ou vos fichiers sons) et vos playlists dans le
repertoire iso.

Vous pouvez aussi ajouter des codecs propri�taires comme le rv9 ou le wmv9, en
les copiant simplement dans le r�pertoire iso/GEEXBOX/codecs. Ces codecs se
trouvent ici :
http://www.mplayerhq.hu/MPlayer/releases/codecs/

Les fichiers utiles sont les suivants:

  * Codecs Real (pour le rv9 par exemple) : atrc.so.6.0, cook.so.6.0,
      sipr.so.6.0, drv3.so.6.0 et drv4.so.6.0.
  * Codecs Windows Media (wmv9/wma9) : wma9dmod.dll et wmv9dmod.dll.

Vous pouvez modifier d'autres options en �ditant simplement des fichiers
textes.

* Langue :
    Choisissez la langue de vos menus en �ditant le fichier generator.sh ou
    generator.bat (en fonction de votre OS). Cela n'as pas d'effets sur la
    langue du DVD (voir section MPlayer). Si votre langue n'est pas disponible,
    vous pouvez toujours traduire un menu. Il suffit de re-cr�er les fichiers
    language/menu_LANG.conf and language/help_LANG.txt.

* MPlayer :
    C'est ici que se font la plupart des configurations et modifications.
    Les options se situent dans le fichier packages/MPlayer/mplayer.conf
    Il est possible de changer des options comme la taille des police de l'OSD
    (subfont-text-scale) et beaucoup d'autres choses telles que la langue par
    d�faut de lecture des DVD (ex: alang=fr,en). La meilleur fa�on de
    comprendre ces options est, pour les utilisateurs de Linux, de se r�f�rer
    au MAN de MPlayer (man -l build/MPlayer-*/DOCS/mplayer.1). D'autres
    informations sont aussi disponibles sur la documentation officielle
    (http://mplayerhq.hu/DOCS/).
    Il peut �galement �tre int�ressant de modifier le fichier 
    packages/MPlayer/menu.conf. Vous pouvez les menus qui vous semblent 
    inutiles, ou les traduire dans d'autres langues par exemple. Enfin, le 
    dernier int�ressant est packages/MPlayer/build, qui contient la s�lection
    d'options de compilation de MPlayer.

* Sortie TV :
    Activer la sortie TV se fait au moyen de nombreux petits utilitaires d�di�s
    chacun � une marque carte graphique. Nous utilisons actuellement atitvout
    pour les cartes ATI, s3switch pour les cartes S3 et nvtv pour les cartes
    nVidia (ce qui peut aussi marcher abec les cartes i810 et 3dfx). La
    configuration de ces programmes se fait dans iso/GEEXBOX/etc/tvout.
    Vous pouvez y choisir le standard que vous utilisez (pal, secam...) et y
    modifier les options sp�cifiques de nvtv.

    # TV Output Standard (ntsc/pal/secam)
    TVOUT_STANDARD=pal

    Vous pouvez �galement d�finir le rapport d'image de sortie (mode 4:3 ou
    16:9) via la ligne :

    TVOUT_ASPECT="4:3"

    Ce param�tre est utilis� � la fois pour la sortie TV et pour l'affichage
    classique sur moniteurs CRT ou TFT. Vous pouvez �galement d�finir les
    valeurs de hauteur et largeur (en pixels) pour l'affichage, ainsi que les
    fr�quences de rafraichissement horizontal et vertical, dans le cas o� vous
    utiliseriez un �cran panoramique ou encore un r�tro-projecteur. Ceci peut
    etre fait en modifiant le contenu du fichier /etc/mplayer/mplayer.conf.
    Les param�tres suivants sont donn�s par d�faut (veuillez d�commenter les
    lignes li�es � la fr�quence de refraichissement si vous souhaiter les
    utiliser ) :

    screenw=800
    screenh=600
    #monitor-hfreq=31.5k-50k
    #monitor-vfreq=50-90

* Lirc :
    Choisissez la t�l�commande support� en �ditant le fichier generator.sh ou
    generator.bat (en fonction de votre OS). Faite �galement attention �
    bien choisir le r�cepteur infrarouge correspondant dans le m�me fichier.
    Si vous d�sirez modifier le mappage des touches reportez vous au fichier
    lirc/lircrc_REMOTE.

* R�seau :
    Le r�seau est configurable au niveau du fichier iso/GEEXBOX/etc/network.
    Ici vous reglerez l'adresse IP de la GeeXboX (qui par d�faut cherche un
    serveur DCHP ou prend l'IP 192.168.0.54 si elle n'en trouve pas). Il est
    aussi possible de lui assigner un login est un mot de passe (par d�faut,
    la GeeXboX ne peut se connecter que sur des partages anonymes).
    Vous pouvez aussi d�clarer des montages NFS dans GEEXBOX/etc/nfs.

* wifi :
    Par defaut, le syst�me tente de d�tecter automatiquement votre
    configuration r�seau. Si vous disposez � la fois d'une carte r�seau
    Ethernet classique et d'une carte WiFi, seule cette derni�re sera
    configur�e. Vous pourrez avoir � modifier le fichier /etc/network afin
    d'y configurer vos param�tres r�seaux. Dans ce dernier, 4 lignes sont
    relatives aux cartes sans-fils :

    PHY_TYPE="auto"      # Network physical type (auto|ethernet|wifi)
    WIFI_MODE="managed"  # Wifi working mode (managed|ad-hoc)
    WIFI_WEP=""          # Wifi WEP key
    WIFI_ESSID="any"     # Wifi SSID

    Vous pouvez soit conserver la d�tection automatique, soit forcer
    l'activation du controleur Ethernet ou WiFi. De la m�me fa�on, ceci vous
    permettra de choisir entre le mode managed et le mode de communication dit
    ad-hoc et de d�finir � la fois votre cl� WEP et le SSID de votre r�seau.

* passerelle :
    La GeeXboX supporte l'acc�s � Internet. D�finissez simplement l'adresse IP
    de la passerelle dans le fichier /etc/network

    GATEWAY=""     # Gateway IP ("" for DHCP or no internet connection)

* configuration TV :
    La GeeXboX supporte les entr�es et tuners de cartes TV. Le syst�me essaie
    avec peine de d�tecter automatiquement le type de carte et de tuners
    utilis�s. Vous pouvez forcer les param�tres et ainsi �viter la tentative
    de d�tection automatique. Veuillez modifier le fichier /etc/tvcard
    tel qu'il suit :

# TV CARD/TUNER Model (AUTO for autodetection or look at the following urls)
# http://www.linuxhq.com/kernel/v2.6/2/Documentation/video4linux/CARDLIST.bttv
# http://www.linuxhq.com/kernel/v2.6/2/Documentation/video4linux/CARDLIST.tuner
TV_CARD=AUTO
TV_TUNER=AUTO

    Laissez le param�tre AUTO si vous souahitez conserver la d�tection
    automatique, ou remplacez le par le num�ro de la carte et du tuner,
    comme d�crit dans les URL pr�c�dentes. Soyez attentifs : pour forcer les
    types de cartes et de tuners, vous devez conna�tre les REFERENCES EXACTES
    de votre mat�riel.

    Une fois cela fait, vous devriez �tre en mesure d'utiliser les entr�es TV
    (Composite et S-VHS) de votre carte TV. De la m�me mani�re, vous pouvez
    utiliser le tuner pour regarder la TV. Pour cela, vous devrez d�finir
    votre r�gion ainsi que les fr�quences des cha�nes que vous souhaitez
    visionner. Editez simplement le fichier /etc/tvcard :

    # TV Channels
    # Syntax : CHAN="Channel Title":"Channel Frequency"
    # Example :
    # CHAN="France 2":"26"
    # CHAN="Canal +":"K08"
    # TV Channels List
    # Available : france, europe-east, europe-west, us-bcast, us-cable
    CHANLIST=france

    Faites attention lors de l'�dition des canaux TV et veillez � utiliser
    la m�me syntaxe que d�crit ci-dessus et les canaux TV devraient
    appara�tre dans le menu principal.

* configuration audio :
    La GeeXboX supporte � la fois la restitution audio via la sortie analogique
    ou num�rique, en utilisant les connecteurs classiques JACK ou RCA SPDIF.
    Par d�faut, la sortie est g�r�e de mani�re analogique. Ceci peut etre
    chang� en modifiant le fichier /etc/audio :

    # Output using SPDIF (yes/no), otherwise ANALOG output
    SPDIF=no

    Souvenez vous qu'il est n�cessaire de r�gler la sortie en mode num�rique
    (SPDIF), si vous souhaitez relier votre carte son � un amplificateur hifi
    externe pour d�coder des flux AC3/DTS (en utilisant le mode passthrough).

* Post-Processing vid�o :
    Le Post-Processing est un moyen logiciel pour affiner une image, en la
    rendant plus nette et plus pr�cise. Cela a par contre l'inconv�nient de
    consommer une partie du temps processeur afin de rendre l'image plus belle.
    Via l'utilisation des filtres internes � MPlayer, la GeeXboX vous permet de
    minimiser les effets de blocs horizontaux et verticaux, les effets
    d'anneaux de d�grad�s et de corriger automatiquement la luminosit� de votre
    film. Par d�faut, le Post-Processing est d�sactiv�, pour �viter de saccader
    sur de petites configurations mat�rielles. Il vous est possible de
    l'activer tr�s simplement en �ditant le fichier /etc/tvout :

    # Set Post Processing (consume CPU power, disable for low configs)
    POSTPROCESS=no

* DXR3/Hollywood+ cards :
    Les utilisateurs de ce type de cartes de d�compression n'ont pas besoin
    d'avoir une carte vid�o ou une carte son dans leur ordinateur. Parmi les
    inconv�nients, on notera n�anmoins que seule la sortie TV peut etre
    utilis�e avec ce type de carte (pas d'affichage sur moniteur).
    Vous pouvez etre amen� � d�finir la norme d'image souhait�e (PAL/NTSC)
    via le fichier /etc/tvout ainsi que le type de sortie audio � utiliser
    (Analogique ou SPDIF) via le fichier /etc/audio.


| GENERATION DE L'ISO
| ~~~~~~~~~~~~~~~~~~~

Avant tout, jetez un oeuil sur la section personalisation juste au dessus

Sous Linux, l'ISO est g�n�r�e en lan�ant la commande suivante:
  ./generator.sh
et sous Windows:
  generator.exe


| POLICES DE CARACTERES ADDITIONELLES POUR LES SOUS-TITRES
| ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Vous pouvez �tre amen�s � vouloir rajouter un jeu de caract�re diff�rent de
celui propos� par d�faut (iso8859-1) pour les sous-titres. La premi�re �tape
est de s'assurer que la fonte n'est pas d�j� inclus dans l'archive officielle
de la GeeXboX. Pour cela, utilisez le generator et regardez si la fonte ne s'y
trouve pas d�j�.

La plupart des jeus de caract�res sont d�j� pr�sents dans l'archive officielle
mais certains n'ont pas pu l'�tre en raison de leur taille excessive (les
polices asiatiques en particulier).

* Fontes g�n�riques :

  Pour rajouter le support de nouvelles fontes, vous n'avez qu'� extraire votre
  police dans le r�pertoire font et ajouter le nom de votre fonte � la variable
  FONT du fichier language/lang.conf.

* Support du Chinois :

  Pour inclure les fontes Chinoise dans l'ISO, vous devez au pr�alable
  r�cup�rer l'archive big5 ou gb2312 utilis�e par MPlayer :

    http://www1.mplayerhq.hu/MPlayer/contrib/fonts/chinesefonts/

  et la d�compresser et copier dans le r�pertoire ./font/big5 ou ./font/gb2312
  du generator le contenu du r�pertoire se terminant par `24` (taille de fonte
  valant 24)

  Par exemple, si vous souhaitez utiliser la police 'gb2312 kai' :

  - Pour les utilisateurs de syst�mes GNU/Linux :
  wget http://www1.mplayerhq.hu/MPlayer/contrib/fonts/chinesefonts/gb2312-kai.tar.bz2
  tar -jxf gb2312-kai.tar.bz2
  mv gb2312-kai/gkai00mp24 ../path/to/generator/font/gb2312

  - Pour les utilisateurs de Windows :
  T�l�chargez le fichier � l'adresse http://www1.mplayerhq.hu/MPlayer/contrib/fonts/chinesefonts/gb2312-kai.tar.bz2
  Ouvrez le avec WinZip ou �quivalent.
  Extrayez le contenu du r�pertoire gb2312-kai\gkai00mp24 de l'archive vers le
  r�pertoire ..\path\to\generator\font\gb2312 du generator.


| INSTALLATION
| ~~~~~~~~~~~~

Avant tout, vous devez cr�er une partition de type FAT16/32 ou EXT2/3 d'une
taille d'environ 16 Mo minimum.

Puis, vous pouvez installer la GeeXboX depuis Linux en lan�ant simplement
  ./installator.sh

R�pondez ensuite � toutes les questions. Lisez les questions avec attention
et stoppez l'installation si vous ne comprenez pas ce que vous faites.

Mais le plus simple reste encore de d�marrer la GeeXboX depuis le CD est de
taper "install" au prompt de d�marrage.

| BOOT PXE
| ~~~~~~~~

Oui, la GeeXboX est capable de booter depuis le r�seau sur une machine
sans disque ! Pour obtenir cela il vous faudra :
 - un serveur DHCP
 - un serveur TFTP
 - un serveur NFS
 - une machine supportant le PXE :-)
Il faut tout d'abord configurer le server DHCP pour qu'il envoie les info de
boot PXE. Voil� un exemple de configuration avec isc dhcp :

allow booting;
allow bootp;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.128 192.168.0.192;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.0.255;
  next-server 192.168.0.1;
  filename "/tftpboot/GEEXBOX/boot/pxelinux.0";
}

L'option next-server est l'adresse du server TFTP.
Ensuite il faut configurer votre serveur TFTP (tel que atftpd) pour qu'il
serve le r�pertoire /tftpboot et copier une arborescence GEEXBOX compl�te
dans ce r�pertoire. Par exemple il est possible de copier le contenu d'un
CD de GeeXboX depuis un linux AVEC L'OPTION CDROM TRANSPARENT DECOMPRESSION
ACTIVE !! (pour v�rifier cela, il suffit de regarder si le fichier sbin/init
de l'arborescence GeeXboX ne contient pas de caract�res totalement incoh�rents)
Si vous avez compil� la GeeXboX vous m�me a partir des sources, il est aussi
possible de g�n�rer l'arborescence GEEXBOX avec make pxe.

Ensuite il faut �diter le fichier /tftpboot/GEEXBOX/boot/pxelinux.cfg/default
pour faire correspondre le nfsroot au bon chemin NFS vers l'arborescence
GeeXboX.

Enfin il reste a configurer NFS pour qu'il exporte l'arborescence GEEXBOX
avec un fichier /etc/exports ressemblant � ceci :

/tftpboot/GEEXBOX (ro)

et un /etc/hosts.allow ressemblant � :

ALL: ALL

Ca devrait �tre bon. Reste a booter la machine PXE et a voir ce qu'il se passe.


| COMPILATION
| ~~~~~~~~~~~

Tout d'abord, regardez la partie de configuration ci-dessous.

Typiquement, la compilation s'effectue simplement au moyen de : 
  make
Ou vous pouvez directement compiler et graver l'ISO via : 
  make burn

Une fois cela fait, vous pouvez regagner de l'espace disque en effa�ant 
l'arborescence de compilation via :
  make clean
ou en effectant un nettoyage complet, �liminant m�me les sources t�l�charg�es :
  make distclean

Il existe �galement des commandes plus avanc�es si vous d�sirez effectuer
des modifications en profondeur au niveau de la GeeXboX :
  scripts/get package          # t�l�charge le paquetage
  scripts/unpack package       # pr�pare le paquetage
  scripts/build package        # compile le paquetage
  scripts/install package      # installe le paquetage dans $INSTALL
  scripts/clean package        # nettoie l'arborescence du paquetage
  scripts/clean --full package # nettoie les sources du paquetage
  make exec                    # lance la GeeXboX dans une cellule
                               # ATTENTION: ceci est une fonction exp�rimentale
                               # Utilisez l� � vos propres risques.

Si vous avez effectu� une version modifi�e de la GeeXboX, vous pouvez :
construire une archive r�duite tar.bz2 via :
  make dist
ou une archive compl�te (avec l'int�gralit� des sources) au moyen de :
  make fulldist
ou construire le g�n�rateur d'ISO :
  make generator
ou encore l'installateur : 
  make installator
ou enfin une arborescence PXE :
  make pxe


| CONFIGURATION
| ~~~~~~~~~~~~~

* Options Globales :
    C'est la premi�re chose dont vous aurez � vous soucier avant d'essayer de
    compiler la GeeXboX. Elles sont contenues dans le fichier config/options, 
    et devraient �tre suffisamment explicites.

* Linux :
    Il s'agit d'une configuration Linux classique (packages/linux/linux.conf).
    Vous pouvez �diter le fichier � la main, ou via scripts/unpack linux
    suivi de make menuconfig -C build/linux-* (ou utiliser votre m�thode 
    pr�f�r�e en lieu et place de menuconfig). Puis, vous devrez sauvegarder
    votre fichier build/linux-*/.config dans packages/linux/linux.conf.

* Lirc :
    Lirc vous permet de contr�ler la GeeXboX en utilisant une t�l�commande.
    En premier lieu, vous aurez � choisir le fichier correspondant � votre
    t�l�commande dans build/lirc-*/remotes (apr�s avoir effectu� scripts/unpack
    lirc) et l'ajouterez � packages/lirc/install. Puis, choisissez votre
    p�riph�rique (par d�faut, il s'agit de /dev/ttyS0 (COM1)) et le pilote
    lirc et mettez le tout dans un fichier nomm� packages/lirc/lircd_$REMOTE. 
    Vous pourrez ensuite choisir l'affectation des touches dans le fichier 
    packages/lirc/lircrc_$REMOTE. Pour chaque affectation, vous aurez � chosir
    un bouton (choisissez leurs noms dans le fichier de d�finitions de la
    t�l�commande) et associez lui une action. L'action sera une de celle
    disponible dans MPlayer (vous pouvez trouver une liste dans le fichier html
    build/MPlayer-*/DOCS/documentation.html#commands).


| MODIFICATION
| ~~~~~~~~~~~~

La premi�re chose dont vous aurez �vous soucier concerne le script 
d'initialisation. En fait, ils sont 2. Le premier est dans 
packages/initrd/linuxrc mais vous ne devriez pas avoir besoin de le modifier.
Le second est config/init et c'est dans ce dernier que vous aurez de
probables modifications � effectuer.

Puis, vous pourrez �tre int�ress�s par l'ajout de nouveaux paquetages. Un
paquetage n'est implement qu'un ensemble de scripts qui se doivent de suivre
certaines r�gles. Tous les scripts se doivent d'�tre plac�s dans un
r�pertoire dont le nom co�ncide avec celui du programme que vous d�sirez
ajouter, lui-m�me dans le r�pertoire packages.

Voici une liste de scripts que vous aurez � cr�er :
 - url : simple liste d'URLS o� sont disponibles les sources.
 - unpack : que faire apr�s avoir d�compresser les sources. Par exemples, vous
            pouvez modifier les fichiers de configuration. Ceci ne concerne pas
            l'application de patchs.
 - need_build : appel� lorsque le paquetage a d�j� �t� compil�, afin de
                s'assurer qu'il n'aura plus besoin d'�tre recompil�. Il devrait
                supprimer le fichier .stamps/"package name"/build si le
                paquetage n�cessite d'�tre reconstruit.
 - build : l'ensemble des �tapes n�cessaires pour compiler le programme.
 - install : l'ensemble des �tapes n�cessaires � l'installation du programme.
             Le pr�fixe d'installation devrait �tre $INSTALL.

Lorsqu'un fichier de la liste d'URLS est nomm� patch-nom_du_programme-..., il
est automatiquement appliqu� aux sources du programme.

Vous devez avoir � l'esprit que les applications qui tournent sous le syst�me
GeeXboX doivent avoir �t� compil� avec la librairie uClibc.

Enfin, la meilleure mani�re d'ajouter un paquetage est de s'inspirer de la 
fa�on dont les actuels sont faits.


| LICENSE
| ~~~~~~~

Tous les programmes utilis�s par GeeXboX sont prot�g�s par leurs licenses
respectives. Tous ces logiciels sont libres et, pour la plupart, prot�g�s par
une licence GPL (License Publique G�n�rale)
La GeeXboX elle-m�me, c'est � dire tous les scripts utilis� et le syst�me
de compilation, est couvert par la licence GNU-GPL.