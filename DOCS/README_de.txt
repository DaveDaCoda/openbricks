
         ooooo                     oo     o  o               oo     o
        M"   "Mo                    Mo  oM"  M                Mo  oM"
       M           oM""Mo  oM""Mo    "Mo"    Mo"""o  oM""Mo    "Mo"
       M    """M   MooooMM MooooMM   oMMo    M    "M M    M    oMMo
       "o     oM   M    o  M    o   oM  Mo   M    oM M    M   oM  Mo
        "MoooM"M   "MooM"  "MooM"  M"    "M  M"ooo"  "MooM"  M"    "M



| �BER GEEXBOX
| ~~~~~~~~~~~~

GeeXboX ist eine Art "Divx Box" Software. Genaugenommen ist es eine bootf�hige
CD, welche es erlaubt, Filme anzuschauen oder Musik zu h�ren. Es unterst�tzt
viele Formate wie zum Beispiel avi, mpeg, divx, ogm, rm, mp3, ogg, dvd, vcd und
 cdda. 
GeeXboX unterst�tzt zudem einige Infrarot-Fernbedienungen und den TV-Ausgang
einiger Grafikkarten.
Dieses Archiv enth�lt die n�tigen Scripte um ein eigenes ISO-Image von GeeXboX
zu erstellen.


| ERFORDERNISSE
| ~~~~~~~~~~~~~

Um ein GeeXboX ISO zu erstellen, ben�tigen Sie eines der folgenden Systeme:
  - ein GNU/Linux System mit mkisofs und mkzftree.
  - ein MAC OS X System mit mkisofs und mkzftree.
  - ein Windows System.

Um GeeXboX zu installieren ben�tigen Sie:
  - ein GNU/Linux System mit syslinux.

Um Ihre eigene GeeXboX zu erstellen ben�tigen Sie einige klassische Werkzeuge:
  - ein laufendes GNU/Linux System.
  - denn gcc C Compiler.
  - GNU make
  - das Kommando patch.
  - den nasm Assembler.
  - bzip2 und gzip.
  - mkfs.ext2 und mkfs.vfat
  - das wget Download-Werkzeug (wird nicht f�r das komplette GeeXboX Paket
    ben�tigt).
  - mkisofs und mkzftree um das ISO-Image zu erstellen.
  - mkzftree um die Dateien des ISO-Images zu komprimieren.
  - cdrecord (um das ISO-Image zu brennen).

Zudem ben�tigen Sie mindestens 500 MB freien Speicher auf Ihrer Festplatte.


| PERSONALISIERUNG
| ~~~~~~~~~~~~~~~~

Mit dem Generator ist es sehr einfach GeeXboX zu personalisieren.

Sie k�nnen zum Beispiel die Unterst�tzung einiger propriet�re Codecs wie rv9
oder wmv9 hinzuf�gen, indem Sie die Codecs einfach in das Verzeichnis
GEEXBOX/codecs kopieren. Diese Codecs finden Sie im Paket, welches unter
http://www.mplayerhq.hu/MPlayer/releases/codecs/ erh�ltlich ist.

Folgende Dateien aus diesem Paket sind n�tzlich:
  * Real Codecs (werden ben�tigt um beispielsweise rv9 abzuspielen):
    atrc.so.6.0, cook.so.6.0, sipr.so.6.0, drv3.so.6.0, drv4.so.6.0.
  * Windows Media Codecs (wmv9/wma9): wma9dmod.dll und wmv9dmod.dll.

Sie k�nnen aber auch andere Einstellungen ver�ndern, indem Sie einfach einige
Text-Dateien editieren.

* Sprache:
    Sie k�nnen die Menu-Sprache �ndern, indem Sie die Datei GEEXBOX/etc/lang
    editieren. Diese Einstellung hat keinen Effekt auf die Sprache der DVD
    (siehe Kapitel MPlayer). Falls Ihre Sprache nicht existiert, k�nnen Sie das
    Menu �bersetzen, indem Sie die Dateien GEEXBOX/etc/mplayer/menu_LANG.conf
    und GEEXBOX/usr/share/mplayer/help_LANG.txt bearbeiten.

* MPlayer:
    Dies ist der Ort, an dem Sie die meisten Einstellungen und Ver�nderungen
    vornehmen k�nnen. Die Einstellungen sind in der Datei 
    packages/MPlayer/mplayer.conf enthalten.
    Es ist zum Beispiel m�glich, die Schriftgr�sse des OSD zu ver�ndern
    (subfont-text-scale).
    Sie k�nnen aber auch viele andere Einstellungen wie zum Beispiel die DVD
    Standard-Sprache ver�ndern (zum Beispiel: alang=fr,en). Die beste �bersicht
    �ber alle Einstellung finden Linux-Benutzer in der manpage
    (man -l build/MPlayer-*/DOCS/mplayer.1). Weitere Informationen finden Sie
    auch in der MPlayer Dokumentation (in build/MPlayer-*/DOCS oder unter
    http://mplayerhq.hu/DOCS/).
    Eine andere Datei, die sie vielleicht editieren wollen, ist
    packages/MPlayer/menu.conf. Sie k�nnen einzelne Menupunkte entfernen oder
    �bersetzungen machen.
    Die letzte interessante Datei ist packages/MPlayer/build. Sie enth�lt die
    Optionen, welche f�r das Erstellen von MPlayer gesetzt sind.

* TV-Ausgang:
    F�r das Aktivieren des TV-Ausgangs werden mehrere kleinen Programme f�r
    jeweils einen Hersteller benutzt. Wir verwenden im Moment atitvout f�r ATI
    Karten, s3switch f�r S3 Karten und nvtv f�r nVidia Karten (unterst�tzt zum
    Teil ebenfalls Intel i810 und 3dfx Karten). Die Einstellungen dieser
    Programme werden �ber die Datei config/tvsettings gemacht. Sie k�nnen den
    TV-Standard w�hlen (PAL, NTSC) und einige spezifische Optionen f�r nvtv
    vornehmen.

* Lirc:
    Sie k�nnen eine unterst�tzte Fernbedienung w�hlen, indem Sie die Datei
    GEEXBOX/etc/remote editieren. Falls Sie eine ATI Remote Wonder verwenden,
    welche nicht von Lirc unterst�tzt wird, m�ssen Sie nichts ver�ndern, da
    sie standardm�ssig von GeeXboX unterst�tzt wird. Falls Sie die
    Tastenbelegung ihrer Fernbedienung ver�ndern m�chten, so editieren Sie die
    Datei GEEXBOX/etc/lirc/lircrc_REMOTE.

* Netzwerk :
    Die Netzwerkeinstellungen werden in der Datei GEEXBOX/etc/network
    vorgenommen. Hier k�nnen Sie beispielsweise die IP-Adresse festlegen
    (Standardm�ssig wird DHCP verwendet und falls dies nicht funktioniert,
    wird die IP 192.168.0.54 verwendet).
    Sie k�nnen aber auch einen Login-Name und eine Passwort festlegen, welches
    f�r die Windows-Freigaben verwendet wird (standardm�ssig wird nur zu
    anonymen Freigaben verbunden).


| ERSTELLEN EINER ISO-DATEI
| ~~~~~~~~~~~~~~~~~~~~~~~~~

Bitte widmen Sie einen Augenblick der oben beschriebenen Personalisierung
bevor Sie mit der Erstellung einer ISO-Datei beginnen.

Anschliessend k�nnen Sie unter Linux die ISO-Datei mit dem folgenden Kommando
erstellen:
  ./generator.sh
oder unter Windows mit dem Starten der Datei
  generator.exe


| INSTALLATION
| ~~~~~~~~~~~~

Als erstes ben�tigen Sie eine FAT16 Partition mit ungef�hr 16 MB freiem
Speicherplatz.

Dann k�nnen Sie die Installation unter Linux starten, indem Sie folgendes
Kommando eingeben:
  ./installator.sh
Beantworten Sie anschliessend alle Fragen. Seien Sie bei diesem Vorgang sehr
vorsichtig! Lesen Sie jede Frage zweimal und unterbrechen Sie die Installation
wenn Sie eine Frage nicht verstehen.


| PXE BOOT
| ~~~~~~~~

Ja, GeeXboX ist f�hig �ber ein Netzwerk ohne Festplatte zu starten!
Um dies zu erreichen ben�tigen Sie folgendes:
 - ein DHCP Server
 - ein TFTP Server
 - ein NFS Server
 - ein PXE f�higer Computer :-)

Zuerst m�ssen Sie den DHCP Server konfigurieren, damit dieser die PXE Boot
Informationen schickt. Im Folgenden eine Beispiel mit isc dhcp:

allow booting;
allow bootp;

subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.128 192.168.0.192;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.0.255;
  next-server 192.168.0.1;
  filename "/tftpboot/GEEXBOX/boot/pxelinux.0";
}

Die next-server Option ist die Adresse des TFTP Servers.

Anschliessend konfigurieren Sie Ihren TFTP Server (wie zum Beispiel atftpd)
so, dass er das Verzeichnis /tftpboot zur Verf�gung stellt. Das Verzeichnis
/tftpboot muss einen vollst�ndigen GEEXBOX Stammbaum enthalten. Sie k�nnen
dazu zum Beispiel den Inhalt eine GeeXboX CD von Linux aus MIT DER AKTIVIERTEN
TRANSPARENTEN DEKOMPRESSION DER CDROM! (um dies zu �berpr�fen schauen Sie auf
den Inhalt der sbin/init im GeeXboX Dateibaum und pr�fen, ob diese Datei
keinen M�ll enth�lt).
Falls Sie GeeXboX selber aus den Sourcen kompiliert haben, so k�nnen Sie einen
Dateibaum ganz einfach mit make pxe erstellen.

Danach sollten Sie die Datei /tftpboot/GEEXBOX/boot/pxelinux.cfg/default
editieren, so dass nfsroot zum richtigen NFS Pfad des GEEXBOX Dateibaumes
zeigt.

Am Schluss m�ssen Sie noch NFS so konfigurieren, dass der GEEXBOX Dateibaum
exportiert wird. Dies erreichen Sie, indem Sie der Datei /etc/exports in etwa
folgendes hinzuf�gen:

/tftpboot/GEEXBOX (ro)

und der Datei /etc/hosts.allow folgendes hinzuf�gen:

ALL: ALL

Damit ist die Konfiguration abgeschlossen. Starten Sie den PXE Computer und
schauen Sie was passiert.


| KOMPILIERUNG
| ~~~~~~~~~~~~

Bevor Sie beginnen, lesen Sie bitte das anschliessende Konfigurations-Kapitel
(mindestens die allgemeinen Einstellungen).

Anschliessen k�nnen Sie das ISO-Image einfach mit folgendem Kommando erstellen:
  make
oder Sie brennen das ISO-Image sogleich:
  make burn

Wenn Sie fertig sind, k�nnen Sie Speicherplatz schaffen, indem Sie nicht mehr ben�tigte Dateien l�schen:
  make clean
oder alle Dateien inklusive der heruntergeladenen Dateien l�schen:
  make distclean

Es gibt noch einige Kommandos, die f�r fortgeschrittene Benutzer gedacht sind:
  scripts/get package        # l�dt ein Paket herunter
  scripts/unpack package     # entpackt und bereitet das Paket vor
  scripts/build package      # kompliert das Paket
  scripts/install package    # installiert das Paket nach $INSTALL
  scripts/clean package      # reinigt den Dateibaum des Paketes
  make exec                  # startet GeeXboX in einem K�fig
                             # WARNUNG: Dies ist eine experimentelle Funktion
                             # Benutzung auf eigene Gefahr.

Falls Sie eine ver�nderte Version von GeeXboX erstellt haben, so k�nnen Sie
sehr einfach ein tar.bz2 Archiv davon erstellen:
  make dist
oder ein vollst�ndiges Archiv (inklusive allen Sourcen):
  make fulldist
oder einen GeeXboX Generator mit:
  make generator
oder eine GeeXboX Installationsroutine mit:
  make installator


| KONFIGURATION
| ~~~~~~~~~~~~~

* Allgemeine Einstellungen:
    Dies ist der erste Schritt, den Sie vor dem Kompilieren von GeeXboX machen
    sollten. Alle Einstellungen stehen in der Datei config/options, welche
    sich selbst erkl�ren sollte. Dort k�nnen Sie die CPU-Familie und das Thema
    w�hlen, und ob sie TrueType Schriften wollen oder nicht. Sie sollten zudem
    die Konfiguration des CD-Brenners anpassen, sofern sie die ISO-Datei
    direkt brennen wollen.

* Linux :
    Dies ist die klassische Linux-Konfiguration (packages/linux/linux.conf).
    Sie k�nnen diese Datei entweder von Hand oder mit einem
    scripts/unpack linux und einem anschliessenden
    make menuconfig -C build/linux-* (oder ihrer bevorzugten Methode anstatt
    von menuconfig) anpassen. Danach sollten Sie Ihre Konfigurationsdatei
    build/linux-*/.config nach packages/linux/linux.conf sichern.

* Lirc :
    Lirc erlaubt Ihnen GeeXboX mit einer Fernbedienung zu steuern. Zuerst
    m�ssen Sie die zur ihrer Fernbedienung passende Datei aus
    build/lirc-*/remotes (nachdem Sie ein scripts/unpack lirc gemacht haben)
    ausw�hlen und diese zur Datei packages/lirc/install hinzuf�gen. Danach
    sollten Sie die Ger�tedatei (Standard ist /dev/ttyS0 (COM1)) und den Lirc
    Treiber ausw�hlen und dies in die Datei packages/lirc/lircd_$REMOTE
    hinzuf�gen. Danach k�nnen Sie die Tasten in der Datei
    packages/lirc/lircrc_$REMOTE belegen. F�r jede Belegung m�ssen Sie einen
    Knopf (entnehmen Sie die Namen der Kn�pfe der Fernbedienungs-Defintion-
    Datei) mit einer passenden Aktion assoziieren. Die Aktion ist eine der
    MPlayer Aktionen (sie finden eine Liste der m�glichen Aktionen in der
    HTML-Datei build/MPlayer-*/DOCS/documentation.html#commands).


| VER�NDERUNGEN 
| ~~~~~~~~~~~~~

Das Erste was Sie anschauen sollten, ist das Initialisierungs-Script. 
Eigentlich sind es zwei Initialisierungs-Scripte. Das Erste ist 
packages/initrd/linuxrc welches Sie aber wahrscheinlich nicht zu ver�ndern
brauchen. Das Zweite ist config/init, wo Sie Ihre Personalisierungen
einbringen k�nnen.

Das n�chste was Sie interessieren k�nnte, ist die Erstellung eines neuen
"Paketes". Ein Paket ist nur eine Reihe von Scripten, die einigen Regeln
folgen m�ssen. Alle Scripte m�ssen sich in einem Verzeichnis befinden mit dem
gleichen Namen wie das Programm, das Sie "packen" wollen, dieses Verzeichnis
wiederum im packages Verzeichnis.

Hier ist eine Liste mit den Scripten, die Sie erstellen sollten:
 - url : nur eine Liste der URL's, wo man die Programm-Sourcen herunterladen
         kann.
 - unpack : enh�lt was nach dem Auspacken des Paketes gemacht wird. Zum
            Beispiel das Modifizieren von Konfigurations-Dateien. Dieses
            Script f�hrt jedoch keine Patches durch.
 - need_build : wird aufgerufen falls das Paket schon kompiliert wurde, um
                sicherzugehen, dass es nicht noch einmal kompiliert werden
                muss. Es sollte die Datei .stamps/"package name"/build
                entfernen, falls das Paket nochmals kompiliert werden muss.
 - build : enth�lt alle Schritte um das Programm zu kompilieren.
 - install : enth�lt alle Schritte um das Programm installieren zu k�nnen. Das
             Prefix der Installtion sollte $INSTALL sein.

Wenn die Datei url einen Dateinamen der Form patch-programmname-... enth�lt,
wird der Patch automatisch auf die entpackten Sourcen ausgef�hrt.

Beachten Sie zudem, dass Software, die auf der GeeXboX laufen soll, mit dem
uClibc gcc Wrapper kompiliert werden muss.

Es bleibt nur noch zu sagen, dass der beste Weg ein eigenes Paket zu erstellen
der ist, einen Blick auf andere Pakete zu werfen.


| LIZENZ
| ~~~~~~~

Alle Programme die von GeeXboX benutzt werden sind durch ihre eigene Lizenz
gesch�tzt. Sie alle sind freie Software und die meisten Programme stehen unter
der GNU General Public License.
GeeXboX selber, gemeint sind alle Scripte die f�r die Komilierung benutzt
werden, stehen unter der GNU General Public License.

