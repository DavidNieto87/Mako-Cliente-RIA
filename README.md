# Mako-Cliente-RIA

## Configuración de Ubuntu 14.04 64 bits para trabajar con Mako.


Lista de Tareas que se llevan acabo para la generación de imagen cliente de Mako en el proyecto RIA.

1. Instalación en limpio de Ubuntu 14.04.5 64 bits

2. Configuración de usuario root

	- sudo passwd root

3. Instalación de paquete aptitude y vim

	- apt install aptitude vim

4. Actualización completa del sistema operativo

	- apt update
	- aptitude full-upgrade

5. Se instalan complementos en soporte de idiomas

6. Instalacion de Gnome clasico

	- apt install gnome-session-fallback
	
	- Una vez instalado, cerrar la sesión actual y en la pantalla de login hacer clic en el icono del logotipo y seleccionar 		  Gnome Flashback (Compiz) o Gnome Flashback (Metacity).

7. Desactivar Informes del sistema Crash:

	- Introduzca los siguientes comandos para deshabilitar los informes de errores:

		- vim /etc/default/apport

		- Edita la última linea del archivo, en donde aparece " enabled=1 "se cambia a"enabled=0". Guardar y cerrar el 			  archivo.

#**************************************************************************

# set this to 0 to disable apport, or to 1 to enable it
# you can temporarily override this with
# sudo service apport start force_start=1
enabled=0

#**************************************************************************

		- A continuación, introducir el siguiente comando para detener el servicio apport:

		- sudo service apport stop

8. Instalamos la aplicación numlockx

	- apt install numlockx

9. Agregamos los scripts de Mako PreSession y PostSession a la carpeta /usr/share/lightdm/lightdm.conf.d

	- PreSession/Default

	- PostSession/Default

	- Aplicar permisos de ejecución a los scripts

		- chmod -R 777 /usr/share/lightdm/lightdm.conf.d/PreSession/
		- chmod -R 777 /usr/share/lightdm/lightdm.conf.d/PostSession/


10. Desactivar los tipos de sesion que no se ocupan (gnome-compiz, ubuntu)

	- Entrar a la carpeta xsessions y a los archivos internos ponerle al ultimo el sufijo .orig a excepción del que se usuará por 		  default, en este caso gnome-fallback.desktop

		- cd /usr/share/xsessions/
		- ls -lh
		- mv gnome-fallback-compiz.desktop gnome-fallback-compiz.desktop.orig
		- mv gnome.desktop gnome.desktop.orig
		- mv ubuntu.desktop ubuntu.desktop.orig

11. Aplicar Gnome como escritorio por defecto y todas las configuraciones de lightdm.

	- Para aplicar el escritorio de gnome por defecto tenemos acceder a los archivos de configuración.

		- vim /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

			- Eliminamos el contenido del archivo y agregamos las siguientes lineas, para que quede como se muestra.

************************************************************************************************************

[SeatDefaults]
user-session=gnome-fallback
greeter-hide-users=true
greeter-show-manual-login=true
allow-guest=false
greeter-setup-script=/usr/bin/numlockx on
session-setup-script= /usr/share/lightdm/lightdm.conf.d/PreSession/Default
session-cleanup-script= /usr/share/lightdm/lightdm.conf.d/PostSession/Default

*************************************************************************************************************

	- Una vez realizado este paso guardamos el fichero y reiniciamos lightdm.

		- sudo service lightdm restart

12. Instalación de paqueteria y librerias necesarias.

	- Desde terminal ejecutar:

************************************************************************************************************

apt-get install flashplugin-installer ubuntu-restricted-extras gstreamer0.10-plugins-ugly libxine1-ffmpeg gxine mencoder libdvdread4 totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 mpg321 libavcodec-extra vim vncviewer clusterssh ktimer scratch gtkpod tftp tftpd-hpa dconf-editor dconf-tools aptitude gparted expect libanyevent-dbd-pg-perl libnet-xmpp-perl libanyevent-xmpp-perl libproc-processtable-perl libarray-unique-perl libalgorithm-diff-perl python-keybinder libexpect-perl libui-dialog-perl xvnc4viewer postgresql-client sshpass W3m shutter fping nmap tcptraceroute traceroute mtr links openssh-server ssh gnome-tweak-tool multitail gdebi-core htop dos2unix gdebi

************************************************************************************************************


	- Desde el centro de software de ubuntu:

		* Gvim
		* Notas tomboy
		* kalzium
		* Kalgebra
		* Klavaro
		* Kturtle
		* Parley
		* Squeak
		* Step
		* TuxMath
		* TuxPaint
		* TuxTyping
		* Agave
		* dia
		* Inkscape
		* Gimp
		* F-spot
		* ScribusNG
		* Xpdf
		* Psi
		* Umbrello
		* Audacity
		* RecordMyDesktop
		* K3b
		* Kino
		* VLC
		* Ripper X
		* SuperTux 2
		* Ajedrez
		* Vinagre

	- Paquetes a descargar desde su sitio Web:

		- skype (4.3.0.37-1_i386) ----->>> http://www.skype.com/es/download-skype/skype-for-linux/downloading/?type=ubuntu64
			- apt-get install -f --->> necesario para satisfacer dependencias.

		- supertuxkart (0.8.1-2_amd64)----->>> http://www.ubuntuupdates.org/package/core/trusty/universe/base/supertuxkart
			- apt-get install -f --->> necesario para satisfacer dependencias.

		- google-chrome-stable --->>> https://www.google.com.mx/chrome/browser/desktop/
		- google-talkplugin ------>>> https://www.google.com/tools/dlpage/hangoutplugin/download.html?hl=es-419
		- xmind (7.5)------------->>> http://www.xmind.net/download/linux/
		- virtualbox (5.1_5.1.6-110634)------>>> https://www.virtualbox.org/wiki/Linux_Downloads
		- VirtualBox_Extension_Pack-->> Abrir con... VirtualBox --->> https://www.virtualbox.org/wiki/Downloads
		- Brackets (1.7) ----------->>> http://brackets.io/

************************************************************************************************************
************************************************************************************************************


		- Ocsinventory ----------->>> http://www.ocsinventory-ng.org/en/#download-end
			
			-  Descomprimir el archivo Ocsinventory-Unix-Agent-2.1.1.tar.gz
			-  tar -xvzf Ocsinventory-Unix-Agent-2.1.1.tar.gz
			-  cd Ocsinventory-Agent-2.1.1

			- Ejecutar los siguientes comandos

			- env PERL_AUTOINSTALL=1 perl Makefile.PL
			- make
			- make install

			- Ejecutar para configurar Agente: /usr/bin/perl postinst.pl

		http://wiki.ocsinventory-ng.org/index.php/Documentation:UnixAgent

************************************************************************************************************
************************************************************************************************************


		- Se instala Visual Studio Code.

			- Descargar el programa de la direccion web:  https://code.visualstudio.com/Download
		
		Forma 1 

				- Ejecutar dpkg -i code_1.5.2-1473686317_amd64.deb


		Forma 2 (antes de que existiera el .deb)

			- Version 64 bits: https://code.visualstudio.com/Docs/?dv=linux64
			- Descomprimir el archivo en la carpeta /opt/
				- sudo unzip VSCode-linux32.zip -d /opt/vscode

			- Crear el acceso directo para no tener que ejecutar siempre la expresión ./Code
			- En un archivo de texto agregamos las siguientes lineas:

***************************************************************************************

[Desktop Entry]
Name=Visual Studio Code
Comment=Editor de código Visual Studio Linux
Exec=/opt/vscode/VSCode-linux-x64/code
Icon=/opt/vscode/VSCode-linux-x64/resources/app/resources/linux/code.png
Terminal=false
Type=Application
StartupNotify=true
Categories=GTK;GNOME;Development;WebDevelopment;

***************************************************************************************
		
			- Guardamos el archivo con el nombre VisualStudioCode.desktop en la ruta /usr/share/applications/
			- vim /usr/share/applications/VisualStudioCode.desktop
			- Si todo sale correcto el programa aparecerá en el apartado "Programación" del menu "Aplicaciones" y se abrirá de forma correcta.

		https://geekytheory.com/como-instalar-visual-studio-code-en-ubuntu-linux-y-derivadas/

************************************************************************************************************
************************************************************************************************************


		- Se instala Scratch 2

		- Opción 1

			- Descargar los archivos necesarios: https://scratch.mit.edu/scratch2download/

				- Adobe Air:

					- airdownload.adobe.com/air/lin/download/2.6/AdobeAIRInstaller.bin

				- Scratch 2 Ver: 450-1

					- https://scratch.mit.edu/scratchr2/static/sa/Scratch-450.1.air

			-     Instalamos Adobe Air en linux:

				- Abrimos un terminal y nos vamos al directorio donde nos hemos descargado el paquete de instalación.

				- Le damos permisos de ejecución:

					- chmod +x AdobeAIRInstaller.bin

				- Buscamos dónde se encuentra la librería libgnome-keyring.so.

					- locate libgnome-keyring.so

				- Utilizando el directorio en el que se encuentra la librería anterior, realizamos la instalación, 					ejecutando en un terminal:

					- LD_LIBRARY_PATH=/usr/lib/i386-linux-gnu ./AdobeAIRInstaller.bin

				- Abrimos Adobe Air y desde ahí seleccionamos el archivo descargado de Scratch, con lo que comenzará la 				instalación.


http://programamos.es/instalacion-de-scratch2-offline-en-debianubuntu/

		- Opción 2

			- Descargar los programas scratch2 y Adobe Air de los siguientes enlaces:

				- https://dl.dropboxusercontent.com/u/41471238/scrash/adobeair_2.6.0.19170-devolo1_i386.deb
				- https://dl.dropboxusercontent.com/u/41471238/scrash/Scratch.zip
				- https://dl.dropboxusercontent.com/u/41471238/scrash/scratch.desktop
		
			- Ejecutar el siguiente comando:

				- gdebi --n adobeair_2.6.0.19170-devolo1_i386.deb ;  unzip Scratch.zip -d / 

			- Crear el acceso directo:
			- En un archivo de texto agregamos las siguientes lineas:

***************************************************************************************

#!/usr/bin/env xdg-open
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=/opt/Scratch\\ 2/bin/Scratch\\ 2
Icon=scratch
Terminal=false
Name=Scratch 2
Comment=Programming system and content development tool
Categories=Application;Education;Development;ComputerScience;
MimeType=application/x-scratch-project
Name[es_MX]=Scratch 2

***************************************************************************************
		
			- Guardamos el archivo con el nombre scratch.desktop en la ruta /usr/share/applications/
			- vim /usr/share/applications/scratch.desktop
			- Si todo sale correcto el programa aparecerá en el apartado "Programación" del menu "Aplicaciones".
			- Copiar la carpeta .appdata a /etc/skel/, que es creada después de aceptar la licencia Adobe AIR y cambiar 
			  el idioma a español de Scratch 2.


************************************************************************************************************
************************************************************************************************************

	- Paquetes a instalar mediante repositorios:

		- Se instala Java Oracle 7
	 
			- add-apt-repository ppa:webupd8team/java
			- apt-get update
			- apt-get install oracle-java7-installer

		http://www.ubuntu-guia.com/2012/04/instalar-oracle-java-7-en-ubuntu-1204.html


		- Se instala Blender 2.78.

			- add-apt-repository ppa:thomas-schiex/blender
			- apt-get update
			- apt-get install blender

		- Se instala Blue Fish 2.2.8.

			- add-apt-repository -y ppa:klaus-vormweg/bluefish
			- apt-get update
			- apt-get install bluefish

		- Se instala Open Shot 2.1.0.

			- sudo add-apt-repository ppa:openshot.developers/ppa
			- sudo apt-get update
			- sudo apt-get install openshot-qt


************************************************************************************************************
************************************************************************************************************

13. Configuración de SSH.

	* vim /etc/ssh/sshd_config editar y dejar igual:

************************************************************************************************************
# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
HostKey /etc/ssh/ssh_host_ed25519_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 1024

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

************************************************************************************************************
************************************************************************************************************


14. Aplicar configuración en dconf-editor

	- Entramos al editor de configuraciones dconf-editor tecleando esto en terminal.

		- dconf-editor

			- Scrollbars visibles 
			
				- Buscamos la opcion scrollbar-mode en la ruta:

					- com.canonical.desktop.interface

				- Editamos y dejamos la opcion: normal

			- Configuración de Menu para cierre de sesión (solo para usuarios enova y socios)

				- Buscamos la ruta:

					-apps.indicator-session

				- Editamos dejando de la siguiente manera todas las opciones:

					- show-real-name-on-panel == desactivado
					- supress-logout-menuitem == desactivado
					- supress-logout-restart-shutdown == desactivado
					- supress-logout-restart-menuitem == activado
					- supress-logout-menuitem == activado
					- user-show-menu == desactivado


			- Cambiar botones minimizar,maximizar,cerrar del lado derecho.
			
				- Buscamos la opcion button-layout en la ruta:

					- org.gnome.desktop.wm.preferences
				
				- Editamos poniendo la siguiente linea:

					- menu:minimize,maximize,close

			- Quitar botón de lock screen de cambio de usuario. 
			
				- Buscamos la opción user-switch-enabled en la ruta:

					- org.gnome.desktop.screensaver
				
				- Desactivar opción.

			- Permitir y habilitar las conexiones VNC. 
			
				- Buscamos la opción require-encryption en la ruta:

					- org.gnome.desktop.remote-access
				
				- Desactivar opción.


			- Habilitar y visualizar los mensajes de la impresora Kyocera. 
			
				- Buscamos la opción active en la ruta:

					- org.gnome.settings-daemon.plugins.print-notifications
				
				- Activar opción.


15. Visualizar unidades montadas

	- sudo apt install gnome-tweak-tool
	
	- Ejecutar desde terminal: gnome-tweak-tool

		-Entrar a " Aplicaciones-> Herramientas del sistema -> Preferencias --> Herramienta de retoque", seleccionamos la opción " 			Escritorio" y seleccionar la opción "volumenes montados" para mostrar las unidades USB.

http://erroresysoluciones.blogspot.mx/2011/10/ver-las-unidades-montadas-en-el.html


16. Se cambia wallpaper por el generico para RIA (tapizGenericoRIA-2016.jpg) 

	- Se realiza cambio de WP desde la VM Repo, en esta solo se modifica la llave ssh con el comando ssh-keygen -R 10.1.XXX.YYY

	- Se corre script de cambio de WP ejecutandolo solo en  la PC de prueba, se ejecuta con exito.



17. Quitar los puntos blancos, cambiar WP y eliminar iconos de la pantalla de acceso (lightdm): 

	- Cambiar de usuario a lightdm para que los cambios tengan efecto.

		- sudo xhost +SI:localuser:lightdm
		- sudo su lightdm -s /bin/bash

	- Entramos al editor de configuraciones dconf-editor tecleando esto en terminal.

		- dconf-editor

			- Configuración de lightdm 
			
				- Buscamos la opcion draw-grid en la ruta:

					- com.canonical.unity-greeter

				- Editamos y dejamos la opcion:  draw-grid = false
				- Editamos y dejamos la opcion: Background = /usr/share/backgrounds/ria.jpg
				- Editamos y dejamos la opcion: indicators = ['com.canonical.indicator.datetime']


	http://gnulinuxvagos.es/topic/2845-tips-para-ubuntu-1404-lts/



18.  Se crean las particiones con gparted en pc desde usb live.

	- /dev/sda1    70 gb  -->> /
	- /dev/sda3    60 gb  -->> /VMs
	- /dev/sda2     4 gb  -->> Swap


19. Modificación de fstab 

	- vim /etc/fstab

	- Se reinicia y debe de levantar la PC.


20. Se elimina network manager, esta aplicación realiza la gestion de las interfaces de red graficamente, se desinstala para poder usar el archivo /etc/network/interfaces por default

	- Se edita y guarda el archivo /etc/network/interfaces, quedando de la siguiente manera:

		- vim /etc/network/interfaces


************************************************************************************************************
************************************************************************************************************

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
dns-nameservers 4.2.2.2


************************************************************************************************************
************************************************************************************************************


	- Se ejecuta el siguiente comando:

		- apt-get purge network-manager network-manager-gnome

	- Se ejecuta el comando ifup eth0 para que tome nuevamente ip la PC.


	- Se reinicia la PC y debe de tomar por default IP mediante DHCP.


http://blog.desdelinux.net/como-eliminar-por-completo-el-applet-network-manager/


21. Configuración de scripts de mako.

	- Copiar carpeta procs a la ruta /root/

		- scp -rp  root@10.1.XX.124:/root/procs/ /root/

	- Dar permisos de ejecución a scripts de mako.

		- chmod 777 /root/procs/*

	- Listar los archivos para validar permisos.

		- ls -lh /root/procs/

************************************************************************************************************

root@enova-OptiPlex-3011-AIO:~# ls -lh /root/procs/
total 24K
-rwxrwxrwx 1 root root 4.1K abr 15 12:35 registroxmpp
-rwxrwxrwx 1 root root 3.2K abr 15 12:35 setmakoconfig
-rwxrwxrwx 1 root root 9.3K abr 15 12:35 trackware

************************************************************************************************************

	- Copiar el archivo de concentrado de centros para configuración de hostname en los clientes "mako.conf" 
	  en la ruta /etc/

		- scp  root@10.1.XX.124:/etc/mako.conf /etc/

	- Copiar el archivo que ejecuta los archivos de configuración mako en la carga del sistema operativo "setmako.conf"
	  en la ruta /etc/init.d/

		- scp  root@10.1.XX.124:/etc/init.d/setmako.conf /etc/init.d/

	- Dar permisos de ejecución al archivo /etc/init.d/setmako.conf 

		- chmod 777 /etc/init.d/setmako.conf

	- Generar el servicio setmako.conf

		- update-rc.d setmako.conf defaults

	- Reiniciar la PC para validar que toma nombre.


22. Validar los archivos de usuarios y grupos para agregar el grupo 513 Socios.

	- Editamos y comparamos el archivo group.

		- vim /etc/group

	- Editamos y comparamos el archivo gshadow.

		- vim /etc/gshadow

	- Editamos y comparamos el archivo passwd.

		- vim /etc/passwd

	- Editamos y comparamos el archivo shadow.

		- vim /etc/shadow


23. Configuración cliente LDAP

	- Actualizamos el sistema e instalamos los paquetes para LDAP.

		- apt-get update
		- apt-get full-upgrade
		- DEBIAN_FRONTEND=noninteractive apt-get install libnss-ldapd libpam-mount libpam-foreground

	- Recuperamos las librerias de la carpeta /lib/security
		
		- scp -rp root@10.1.1XX.124:/lib/security/ /lib/

	- Se edita el archivo nsswitch.conf, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/nsswitch.conf

	- Se crea el archivo ldap.conf, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/ldap.conf
		- Para recuperar el archivo: scp -p root@10.1.XX.124:/etc/ldap.conf /etc/

	- Se edita el archivo nslcd.conf, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/nslcd.conf
		- Para recuperar el archivo: scp -p root@10.1.XX.124:/etc/nslcd.conf /etc/

	- Se editan los archivos de la carpeta pam.d, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/pam.d/common-auth
		- Para recuperar los archivos: scp -rp root@10.1.13.124:/etc/pam.d/ /etc/

	- Se editan los archivos de la carpeta pam.d, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/pam.d/common-account

	- Se editan los archivos de la carpeta pam.d, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/pam.d/common-password

	- Se editan los archivos de la carpeta pam.d, para agregar la configuración de todos los proyectos, quedando de la siguiente manera.

		- vim /etc/pam.d/common-session

	- Se copian todos los archivos restantes de la carpeta /etc/pam.d/
	
	- Se arranca el servicio nslcd en modo debug.

		- service nslcd stop
		- nslcd -d

	- En otra consola, verificamos la conexion al servidor ldap local.

		- getent passwd
		- getent group

	- En otra consola, validamos la conexión a la PC con una cuenta de LDAP.

		- ssh david.nieto@10.1.XX.126

	- Si todo funciona bien, arranquamos nslcd en modo normal

		- service nslcd start

Información obtenida de la Wiki (FRancois Trachez)


24. Deshabilitar opciones “Reiniciar y Apagar” del sistema operativo.

	- Se edita y guarda el arcvhivo org.freedesktop.consolekit.policy

		* vim /usr/share/polkit-1/actions/org.freedesktop.consolekit.policy

		
************************************************************************************************************
************************************************************************************************************

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">

<!--
Policy definitions for ConsoleKit
-->

<policyconfig>

  <action id="org.freedesktop.consolekit.system.stop">
    <description>Stop the system</description>
    <message>System policy prevents stopping the system</message>
    <defaults>
      <allow_inactive>yes</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.stop-multiple-users">
    <description>Stop the system when multiple users are logged in</description>
    <message>System policy prevents stopping the system when other users are logged in</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>auth_admin_keep</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart">
    <description>Restart the system</description>
    <message>System policy prevents restarting the system</message>
    <defaults>
      <allow_inactive>yes</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.consolekit.system.restart-multiple-users">
    <description>Restart the system when multiple users are logged in</description>
    <message>System policy prevents restarting the system when other users are logged in</message>
    <defaults>
      <allow_inactive>yes</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

</policyconfig>

************************************************************************************************************
************************************************************************************************************


25. Deshabilitar opciones “Hibernar y Suspender” del sistema operativo.


	- Se edita y guarda el arcvhivo org.freedesktop.upower.policy

		* vim /usr/share/polkit-1/actions/org.freedesktop.upower.policy


************************************************************************************************************
************************************************************************************************************

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC
 "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
  <vendor>The UPower Project</vendor>
  <vendor_url>http://upower.freedesktop.org/</vendor_url>
  <icon_name>system-suspend</icon_name>

  <action id="org.freedesktop.upower.suspend">
    <description>Suspend the system</description>
    <description xml:lang="fr">Mettre le système en veille</description>
    <description xml:lang="it">Sospende il sistema</description>
    <description xml:lang="pl">Wstrzymanie systemu</description>
    <description xml:lang="sv">Försätt systemet i vänteläge</description>
    <message>Authentication is required to suspend the system</message>
    <message xml:lang="fr">Vous devez vous identifier pour mettre le système en veille</message>
    <message xml:lang="it">È richiesto autenticarsi per sospendere il sistema</message>
    <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby wstrzymać system</message>
    <message xml:lang="sv">Autentisering krävs för att försätta systemet i vänteläge</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

  <action id="org.freedesktop.upower.hibernate">
    <description>Hibernate the system</description>
    <description xml:lang="fr">Mettre le système en hibernation</description>
    <description xml:lang="it">Iberna il sistema</description>
    <description xml:lang="pl">Hibernacja systemu</description>
    <description xml:lang="sv">Försätt systemet i viloläge</description>
    <message>Authentication is required to hibernate the system</message>
    <message xml:lang="fr">Vous devez vous identifier pour mettre le système en hibernation</message>
    <message xml:lang="it">È richiesto autenticarsi per ibernare il sistema</message>
    <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zahibernować system</message>
    <message xml:lang="sv">Autentisering krävs för att försätta systemet i viloläge</message>
    <defaults>
      <allow_inactive>no</allow_inactive>
      <allow_active>no</allow_active>
    </defaults>
  </action>

</policyconfig>


************************************************************************************************************
************************************************************************************************************


26. Modificar archivo /etc/login.defs para no almacenar usuarios.


	- Se edita y guarda el arcvhivo /etc/login.defs

		- vim /etc/login.defs

	- Ubicar y cambiar las lineas UID_MAX y  GID_MAX de 60000 a 6000 para que no almacene usuarios de staff, quedando el archivo de la siguiente manera.


************************************************************************************************************
************************************************************************************************************

#
# Min/max values for automatic uid selection in useradd
#
UID_MIN                  1000
UID_MAX                  6000
# System accounts
#SYS_UID_MIN              100
#SYS_UID_MAX              999

#
# Min/max values for automatic gid selection in groupadd
#
GID_MIN                  1000
GID_MAX                  6000
# System accounts
#SYS_GID_MIN              100
#SYS_GID_MAX              999

************************************************************************************************************
************************************************************************************************************

http://www.linuxtotal.com.mx/index.php?cont=info_admon_008


27. Se agregan reglas Udev de video, cd-rom,usb y audio en la carpeta /etc/udev/rules.d/

	  - Se recuperan los archivos de otra PC configurada:

		- 25-name-video-devices.rules

			- scp -p root@10.1.12.124:/etc/udev/rules.d/25-name-video-devices.rules /etc/udev/rules.d/		

		- 30-name-audio-devices.rules

			- scp -p root@10.1.12.124:/etc/udev/rules.d/30-name-audio-devices.rules /etc/udev/rules.d/

		- 40-name-cd-rom-devices.rules

			- scp -p root@10.1.12.124:/etc/udev/rules.d/40-name-cd-rom-devices.rules /etc/udev/rules.d/
			
		- 90-usb-disks.rules

			- scp -p root@10.1.12.124:/etc/udev/rules.d/90-usb-disks.rules /etc/udev/rules.d/


28. Se agrega archivo de politicas de unidades USB en /usr/share/polkit-1/actions/

	- Se sustituye el archivo org.freedesktop.udisks2.policy

		- scp -p root@10.1.12.124:/usr/share/polkit-1/actions/org.freedesktop.udisks2.policy /usr/share/polkit-1/actions/


29. Desactivar actualizaciones  LTS del sistema:

	- Editar y guardar el siguiente archivo para deshabilitar las actualizaciones LTS:

		- vim /etc/update-manager/release-upgrades

		- Editar la última linea del archivo, donde aparece "Prompt"se cambia a"Prompt=never". 


30. Creación de carpeta "cineria"

	- mkdir /var/cineria
	- chmod 777 /var/cineria/


31. Modificamos diferentes politicas para que no se ejecute el apagado y suspendido, ademas de que se iniba el uso del boton fisico del apagado.

	- Se modifica el archivo org.freedesktop.login1.policy de la ruta.

		- vim /usr/share/polkit-1/actions/org.freedesktop.login1.policy
		- Quedando de la siguiente manera

************************************************************************************************************
********************************  org.freedesktop.login1.policy   *****************************************


<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN"
        "http://www.freedesktop.org/standards/PolicyKit/1/policyconfig.dtd">
<policyconfig>

        <vendor>The systemd Project</vendor>
        <vendor_url>http://www.freedesktop.org/wiki/Software/systemd</vendor_url>

        <action id="org.freedesktop.login1.inhibit-block-shutdown">
                <description>Allow applications to inhibit system shutdown</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymywanie wyłączenia systemu</description>
                <message>Authentication is required to allow an application to inhibit system shutdown.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie wyłączenia systemu.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>no</allow_inactive>
                        <allow_active>no</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.inhibit-delay-shutdown org.freedesktop.login1.inhibit-block-sleep org.freedesktop.login1.inhibit-delay-sleep org.freedesktop.login1.inhibit-block-idle</annotate>
        </action>

        <action id="org.freedesktop.login1.inhibit-delay-shutdown">
                <description>Allow applications to delay system shutdown</description>
                <description xml:lang="pl">Zezwolenie programom na opóźnienie wyłączenia systemu</description>
                <message>Authentication is required to allow an application to delay system shutdown.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na opóźnienie wyłączenia systemu.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>no</allow_inactive>
                        <allow_active>no</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.inhibit-delay-sleep</annotate>
        </action>

        <action id="org.freedesktop.login1.inhibit-block-sleep">
                <description>Allow applications to inhibit system sleep</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymanie uśpienia systemu</description>
                <message>Authentication is required to allow an application to inhibit system sleep.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie uśpienia systemu.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>no</allow_inactive>
                        <allow_active>no</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.inhibit-delay-sleep org.freedesktop.login1.inhibit-block-idle</annotate>
        </action>

        <action id="org.freedesktop.login1.inhibit-delay-sleep">
                <description>Allow applications to delay system sleep</description>
                <description xml:lang="pl">Zezwolenie programom na opóźnienie uśpienia systemu</description>
                <message>Authentication is required to allow an application to delay system sleep.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na opóźnienie uśpienia systemu.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>no</allow_inactive>
                        <allow_active>no</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.inhibit-block-idle">
                <description>Allow applications to inhibit automatic system suspend</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymanie automatycznego uśpienia systemu</description>
                <message>Authentication is required to allow an application to inhibit automatic system suspend.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie automatycznego uśpienia systemu.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>no</allow_inactive>
                        <allow_active>no</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.inhibit-handle-power-key">
                <description>Allow applications to inhibit system handling of the power key</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymanie obsługi klawisza zasilania przez system</description>
                <message>Authentication is required to allow an application to inhibit system handling of the power key.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie obsługi klawisza zasilania przez system.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>yes</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.inhibit-handle-suspend-key org.freedesktop.login1.inhibit-handle-hibernate-key org.freedesktop.login1.inhibit-handle-lid-switch</annotate>
        </action>

        <action id="org.freedesktop.login1.inhibit-handle-suspend-key">
                <description>Allow applications to inhibit system handling of the suspend key</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymanie obsługi klawisza uśpienia przez system</description>
                <message>Authentication is required to allow an application to inhibit system handling of the suspend key.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie obsługi klawisza uśpienia przez system.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>yes</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.inhibit-handle-hibernate-key org.freedesktop.login1.inhibit-handle-lid-switch</annotate>
        </action>

        <action id="org.freedesktop.login1.inhibit-handle-hibernate-key">
                <description>Allow applications to inhibit system handling of the hibernate key</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymanie obsługi klawisza hibernacji przez system</description>
                <message>Authentication is required to allow an application to inhibit system handling of the hibernate key.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie obsługi klawisza hibernacji przez system.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>yes</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.inhibit-handle-lid-switch">
                <description>Allow applications to inhibit system handling of the lid switch</description>
                <description xml:lang="pl">Zezwolenie programom na wstrzymanie obsługi przełącznika pokrywy przez system</description>
                <message>Authentication is required to allow an application to inhibit system handling of the lid switch.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić programowi na wstrzymanie obsługi przełącznika pokrywy przez system.</message>
                <defaults>
                        <allow_any>no</allow_any>
                        <allow_inactive>no</allow_inactive>
                        <allow_active>no</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.set-user-linger">
                <description>Allow non-logged-in users to run programs</description>
                <description xml:lang="pl">Zezwolenie niezalogowanym użytkownikom na uruchamianie programów</description>
                <message>Authentication is required to allow a non-logged-in user to run programs.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zezwolić niezalogowanemu użytkownikowi na uruchamianie programów.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.attach-device">
                <description>Allow attaching devices to seats</description>
                <description xml:lang="pl">Zezwolenie na podłączanie urządzeń do stanowisk</description>
                <message>Authentication is required for attaching a device to a seat.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby podłączyć urządzenie do stanowiska.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.flush-devices</annotate>
        </action>

        <action id="org.freedesktop.login1.flush-devices">
                <description>Flush device to seat attachments</description>
                <description xml:lang="pl">Usunięcie podłączenia urządzeń do stanowisk</description>
                <message>Authentication is required for resetting how devices are attached to seats.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby ponownie ustawić sposób podłączenia urządzeń do stanowisk.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.power-off">
                <description>Power off the system</description>
                <description xml:lang="pl">Wyłączenie systemu</description>
                <message>Authentication is required for powering off the system.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby wyłączyć system.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.power-off-multiple-sessions">
                <description>Power off the system while other users are logged in</description>
                <description xml:lang="pl">Wyłączenie systemu, kiedy są zalogowani inni użytkownicy</description>
                <message>Authentication is required for powering off the system while other users are logged in.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby wyłączyć system, kiedy są zalogowani inni użytkownicy.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.power-off</annotate>
        </action>

        <action id="org.freedesktop.login1.power-off-ignore-inhibit">
                <description>Power off the system while an application asked to inhibit it</description>
                <description xml:lang="pl">Wyłączenie systemu, kiedy program zażądał jego wstrzymania</description>
                <message>Authentication is required for powering off the system while an application asked to inhibit it.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby wyłączyć system, kiedy program zażądał jego wstrzymania.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.power-off</annotate>
        </action>

        <action id="org.freedesktop.login1.reboot">
                <description>Reboot the system</description>
                <description xml:lang="pl">Ponowne uruchomienie systemu</description>
                <message>Authentication is required for rebooting the system.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby ponownie uruchomić system.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.reboot-multiple-sessions">
                <description>Reboot the system while other users are logged in</description>
                <description xml:lang="pl">Ponowne uruchomienie systemu, kiedy są zalogowani inni użytkownicy</description>
                <message>Authentication is required for rebooting the system while other users are logged in.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby ponownie uruchomić system, kiedy są zalogowani inni użytkownicy.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>yes</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.reboot</annotate>
        </action>

        <action id="org.freedesktop.login1.reboot-ignore-inhibit">
                <description>Reboot the system while an application asked to inhibit it</description>
                <description xml:lang="pl">Ponowne uruchomienie systemu, kiedy program poprosił o jego wstrzymanie</description>
                <message>Authentication is required for rebooting the system while an application asked to inhibit it.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby ponownie uruchomić system, kiedy program zażądał jego wstrzymania.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.reboot</annotate>
        </action>

        <action id="org.freedesktop.login1.suspend">
                <description>Suspend the system</description>
                <description xml:lang="pl">Uśpienie systemu</description>
                <message>Authentication is required for suspending the system.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby uśpić system.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.suspend-multiple-sessions">
                <description>Suspend the system while other users are logged in</description>
                <description xml:lang="pl">Uśpienie systemu, kiedy są zalogowani inni użytkownicy</description>
                <message>Authentication is required for suspending the system while other users are logged in.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby uśpić system, kiedy są zalogowani inni użytkownicy.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.suspend</annotate>
        </action>

        <action id="org.freedesktop.login1.suspend-ignore-inhibit">
                <description>Suspend the system while an application asked to inhibit it</description>
                <description xml:lang="pl">Uśpienie systemu, kiedy program poprosił o jego wstrzymanie</description>
                <message>Authentication is required for suspending the system while an application asked to inhibit it.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby uśpić system, kiedy program zażądał jego wstrzymania.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.suspend</annotate>
        </action>

        <action id="org.freedesktop.login1.hibernate">
                <description>Hibernate the system</description>
                <description xml:lang="pl">Hibernacja systemu</description>
                <message>Authentication is required for hibernating the system.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zahibernować system.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
        </action>

        <action id="org.freedesktop.login1.hibernate-multiple-sessions">
                <description>Hibernate the system while other users are logged in</description>
                <description xml:lang="pl">Hibernacja systemu, kiedy są zalogowani inni użytkownicy</description>
                <message>Authentication is required for hibernating the system while other users are logged in.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zahibernować system, kiedy są zalogowani inni użytkownicy.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.hibernate</annotate>
        </action>

        <action id="org.freedesktop.login1.hibernate-ignore-inhibit">
                <description>Hibernate the system while an application asked to inhibit it</description>
                <description xml:lang="pl">Hibernacja systemu, kiedy program zażądał jej wstrzymania</description>
                <message>Authentication is required for hibernating the system while an application asked to inhibit it.</message>
                <message xml:lang="pl">Wymagane jest uwierzytelnienie, aby zahibernować system, kiedy program zażądał jej wstrzymania.</message>
                <defaults>
                        <allow_any>auth_admin_keep</allow_any>
                        <allow_inactive>auth_admin_keep</allow_inactive>
                        <allow_active>auth_admin_keep</allow_active>
                </defaults>
                <annotate key="org.freedesktop.policykit.imply">org.freedesktop.login1.hibernate</annotate>
        </action>

</policyconfig>


************************************************************************************************************
************************************************************************************************************
  

32. Modificar las opciones de apagado para root, enova y socios.

	* Ejecutar desde consola dconf-editor
	* Seguir la ruta:
		- org.gnome.settings-daemon.plugins.power
		- En la opción "button-power" seleccionar la cadena nothing
	* Este procedimiento se tienen que hacer en las cuentas root y enova, posteriormente de la cuenta enova se genera el skel para que 		  se guarden las opciones para todos los usuarios.


33. Instalación y configuración de impresora Kyocera.

	- Opción 1:

		- Se configura impresora desde system-config-printer con el driver de la impresora Kyocera-MITA-KM-3050-KPDL

		- Se aplica el dns "printer" a la impresora, entrando a sus propiedades se sustituyen los valores de "Ubicación" y "URI 		  del Dispositivo", cambiando la dirección IP por la palabra printer.

		- En "Opciones de la impresora", buscar la opción "Job Settings" y cambiar el parametro a "Job Storage".

	- Opción 2:

		- Se descarga el driver PPD de la pagina de Kyocera Mita y se agrega al instalar desde system-config-printer.

			- https://www.kyoceradocumentsolutions.es/index/support/descargas.false.driver.ECOSYSM3550IDN._.ES.html#

		- Se aplica el dns "printer" a la impresora, entrando a sus propiedades se sustituyen los valores de "Ubicación" y "URI 		  del Dispositivo", cambiando la dirección IP por la palabra printer.

		- En "Opciones de la impresora", buscar la opción "Trabajo en cola" y cambiar el parametro a "Almacenar Trabajos".

	- Se quita la opción de "Compartir" a la impresora

	- En la ventana de Impresoras se da clic en "Servidor" --->> "Configuración" y se habilitan las opciones:

		- Publicar impresoras compartidas conectadas a este sistema.
		- Permitir la impresión desde Internet.

	- Se configura impresora Kyocera en libre office, debido a que al mandar a imprimir desde el icono impresion rapida manda error el 		  "No se puede iniciar la impresora. Compruebe la configuración."

		- Ir al Administrador de Impresión de LibreOffice
		- Identificar la impresora, seleccionar Propiedades y luego ir a la viñeta Dispositivo
		- En el Tipo de idioma de la impresora, cambiar Automático PDF por PostScript Nivel 2

			http://www.ubuntu-es.org/node/175887#.U5D1fYZFQX4


	- Se configura impresora para todos los usuarios y cualquier documento.

		- Ejecutar en una terminal como root el comando 

			- /usr/lib/libreoffice/program/spadmin 

			- Seleccionar la impresora y dar clic en Propiedades.
			- Ir a la pestaña Dispositivo y seleccionar en la opcion "Tipo de lenguaje de la impresora" PostScript Nivel2
			- Ir a la pestaña "Sustitución tipografica" y activar la casilla "Activar sustitución tipografica"
			- Dar clic en Aceptar y posteriormente en Cerrar.

		https://lists.ubuntu.com/archives/ubuntu-ar/2011-November/040506.html

		https://help.libreoffice.org/Common/Setting_up_Printer_and_Fax_Under_UNIX_Based_Platforms/es



34. Se agregan los scripts de Virtual Box, VNC, Wallpaper en la carpeta /usr/local/bin/

	- Se recupera la carpeta que contiene los scripts de otra PC:

		- scp -pr root@10.1.12.124 /usr/local/bin/  /usr/local/		


	- Quedando la carpeta de la siguiente manera

************************************************************************************************************
************************************************************************************************************

root@pc16-l-ecat4:/home/enova# ls -lh /usr/local/bin/

-r-xr-xr-x 1 root root  14K sep 20 16:56 ipdiscover
-rw-r--r-- 1 root root 2.3K may 26  2014 My_DB.pm
-r-xr-xr-x 1 root root 9.2K sep 20 16:56 ocsinventory-agent
-rwxrwxrwx 1 root root 8.6K jun 12  2014 vbox_wrapper.pl
-rwxrwxrwx 1 root root 5.1K nov 19  2015 vnc_wrapper.pl
-rwxrwxrwx 1 root root 2.6K may  9 15:41 wall
-rwxrwxrwx 1 root root 6.4K may 10 13:36 wallmontar

************************************************************************************************************
************************************************************************************************************


35. Instalación del Agente Mako (Cliente PC Watcher)

	- Crear la Ruta en la pc /var/www/agente-pcwatcher

		- mkdir -p /var/www/agente-pcwatcher

	- Copiar todo el contenido de la carpeta agent a la carpeta creada en el paso anterior

		- cp -rp Agent/* /var/www/agente-pcwatcher/

	- Entrar a la carpeta /var/www/agente-pcwatcher/install/

		- cd /var/www/agente-pcwatcher/install/

	- Establecer los permisos de ejecución al script install3.sh con el comando 

		- chmod 777 install3.sh

	- Ejecutar el script install3.sh, pasando el parámetro del DNS del proyecto: RIA:mako-ria, PMC:mako-pmc, BD:mako-bd

		- sudo ./install3.sh mako-ria

	- Validar que el demonio mako_agent se encuentre en la ruta /etc/init.d/

		- ls -lh /etc/init.d/mako_agent 

			- Mostrará en salida:

************************************************************************************************************

		-rwxr-xr-x 1 root root 1.2K jul 27 11:06 /etc/init.d/mako_agent

************************************************************************************************************

	- Validar que el proceso mako_agent se esté ejecutando

		- ps aux | grep agent

			- Mostrará en salida:

************************************************************************************************************

root  7562  0.8  0.6 1253904 51188 ?  Sl   11:06   0:14 /usr/bin/java -jar /var/www/agente-pcwatcher/target/Agent-1.0-SNAPSHOT-jar-with-dependencies.jar

************************************************************************************************************

	-  Validar que en el archivo de configuración esté correctamente declarado el DNS de Mako, entrando a la carpeta 
	   /var/www/agente-pcwatcher/target


		- Visualizar el archivo config.properties con el comando:

			- less /var/www/agente-pcwatcher/target/config.properties 

				- Mostrará en salida:

************************************************************************************************************

url=http://mako-ria/index.php/restpcwatcher
retry=5000
threads=5
/var/www/agente-pcwatcher/target/config.properties (END)

************************************************************************************************************


	- Validar que la URL del archivo /var/www/agente-pcwatcher/target sea correcta mediante el comando:

    		- curl http://mako-bd/index.php/restpcwatcher


IMPORTANTE: Revisar que el nombre del URL resuelva correctamente y tenga el DNS de mako de forma correcta y de acuerdo al proyecto.
 


36. Se cambia la contraseña estandar para la cuenta Enova, añadiendo el sufijo del proyecto y quedando de la siguiente manera.

	- ria3n0v4!!!.
  
37. Se eliminanan Kernels viejos.

	- dpkg --get-selections | grep linux-image
	- apt-get remove --purge "paquete"
		- Donde paquete es el nombre del kernel por ejemplo: ¨linux-image-2.6.24-19-generic¨
		- NO desinstalar el kernel linux-image-generic ya que es necesario para recibir actualizaciones del kernel.

	http://www.guia-ubuntu.com/index.php?title=Borrar_kernels_antiguos


38. Se integra el script de Wallpaper.

	- Se recuperan los script (wall y wallmontar) de otra PC: 

		- scp -p root@10.1.12.124 /usr/local/bin/wal*  /usr/local/bin/

	- Se dan permisos de ejecución a los scripts

		- chmod 777 /usr/local/bin/wal*

	- Se crea la carpeta /var/wall/, con permisos 777 y sin grupo ni propietario

		- mkdir -m 777 /var/wall

		- chown nobody:nogroup /var/wall

	- Se generan los archivos de ejecución de los scripts, para Wall en PreSession

		- vim /usr/share/lightdm/lightdm.conf.d/PreSession/Wall

		- chmod 777 /usr/share/lightdm/lightdm.conf.d/PreSession/Wall

************************************************************************************************************
************************************************************************************************************
/usr/local/bin/wall &

exit 0
************************************************************************************************************
************************************************************************************************************

	- Se generan los archivos de ejecución de los scripts, para Wallmontar en PostSession

		- vim /usr/share/lightdm/lightdm.conf.d/PostSession/PostWall

		- chmod 777 /usr/share/lightdm/lightdm.conf.d/PostSession/PostWall

************************************************************************************************************
************************************************************************************************************
pkill wall
((/usr/local/bin/wallmontar 0))
exit 0
************************************************************************************************************
************************************************************************************************************


	- Se descomentan las lineas que hacen referencia al script de wallpaper en el PreSession y PostSession.


		- PreSession

************************************************************************************************************
************************************************************************************************************

#Instruccion para Wallpaper
((/usr/share/lightdm/lightdm.conf.d/PreSession/Wall & ))

************************************************************************************************************
************************************************************************************************************

		- PostSession

************************************************************************************************************
************************************************************************************************************

#Instruccion para detener el proceso del Wallpaper
((/usr/share/lightdm/lightdm.conf.d/PostSession/PostWall & ))

************************************************************************************************************
************************************************************************************************************


	- Se genera y agrega en rc.local la instrucción para el montaje de la carpeta wall y scanner(solo recepción) a inicio del SO.

		- vim /etc/rc.local

************************************************************************************************************
************************************************************************************************************
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#Inicializa el proceso para cambio de Wallpaper Automatico
#Monta la carpeta compartida del repo
/usr/local/bin/wallmontar 0
mount -a
exit 0

************************************************************************************************************
************************************************************************************************************

	- Se reinicia la PC y ya debe de ejecutarse el script de wallmontar y wall sin problemas rotando los Wallpapers cada 5 min,


39. Se configura chrome para que no ejecute el guardado automatico de contraseñas en la aplicación seahorse, agregando la instrucción 
	--password-store=basic en el lanzador de la aplicación.

	- vim /usr/share/applications/google-chrome.desktop

		- Esto se agrega en los tres modos de lanzar la aplicación incluidos en el mismo archivo (siempre donde diga Exec)

************************************************************************************************************
************************************************************************************************************

Exec=/usr/bin/google-chrome-stable %U --password-store=basic
Terminal=false
Icon=google-chrome
Type=Application
Categories=Network;WebBrowser;

************************************************************************************************************
************************************************************************************************************


40. Se genera Skel con configuracion de marcadores en Firefox y Chrome, se edita menu principal, se dan permisos para VNC, se edita barra de indicadores, se crea tarea al inicio para que abra firefox al iniciar la sesion, se crean botones de VNC facilitadores, Windows_RIA y acceso directo de firefox.


41. Eliminamos error de apt update "La suma hash difiere"

	- sudo rm -Rf /var/lib/apt/lists/*

https://windtux.com/solventando-el-error-la-suma-hash-difiere-al-buscar-actualizaciones-en-ubuntu


42. Implementación de archivos de configuración para CUPS.

	- Editamos el archivo vim /etc/cups/cups-browsed.conf, para evitar que el sistema busque impresoras por DNS en la red.

		- vim vim /etc/cups/cups-browsed.conf

	- Cambiamos la palabra DNSSD por none y guardamos el archivo, quedando de la siguienta manera.

************************************************************************************************************
************************************************************************************************************

# Which protocols will we use to discover printers on the network?
# Can use DNSSD and/or CUPS, or 'none' for neither.
BrowseRemoteProtocols none

************************************************************************************************************
************************************************************************************************************

	- Recuperamos el archivo de configuración de CUPS /etc/cups/cupsd.conf de una maquina ya funcional.

		- scp root@10.1.13.124:/etc/cups/cupsd.conf /etc/cups/

	- Reiniciamos el servicio CUPS.

		- sudo service cups restart



43. Recuperación de imagenes para mensajes de cierre de sesión sin tiempo y advertencias.

	- Recuperamos las dos imagenes y su archivos de configuración de la carpeta /usr/share/icons/gnome/scalable/emblems/ desde una pc 		  ya funcional.

		- scp -p root@10.1.13.124:/usr/share/icons/gnome/scalable/emblems/emblem-important.icon /usr/share/icons/gnome/scalable/emblems/

		- scp -p root@10.1.13.124:/usr/share/icons/gnome/scalable/emblems/emblem-important.svg /usr/share/icons/gnome/scalable/emblems/

		- scp -p root@10.1.13.124:/usr/share/icons/gnome/scalable/emblems/emblem-urgent.icon /usr/share/icons/gnome/scalable/emblems/

		- scp -p root@10.1.13.124:/usr/share/icons/gnome/scalable/emblems/emblem-urgent.svg /usr/share/icons/gnome/scalable/emblems/

	- Validar que se muestren las imagenes y que sea correcto el proceso de cierre de sesión en las PCs con un socio con un tiempo de 	    15 min.



44. Agregamos el usuario Reinicio en la PC.

	- Se crea el usuario reinicio.

		- useradd reinicio

	- Se genera la contraseña para el usuario (Passwd=reinicio).

		- passwd reinicio

	- Iniciar sesión con el usuario para validar que funcione.

	- Modificar el archivo /etc/sudoers, para dar permisos al usuario reinicio.

		- vim /etc/sudoers

			- Agregamos las siguientes lineas al final y guardamos.

************************************************************************************************************
************************************************************************************************************

#Usario reinicio
reinicio ALL = (root) NOPASSWD: /sbin/shutdown
reinicio ALL = (root) NOPASSWD: /sbin/reboot

************************************************************************************************************
************************************************************************************************************

	- Modificar o crear el archivo /home/reinicio/.profile, para indicar al incio de sesión que reincie el equipo.

		- vim /home/reinicio/.profile

			- Si no existe el archivo gregamos las siguientes lineas y guardamos, en caso contrario solo agregar las últimas 4 				  lineas y guardar.


************************************************************************************************************
************************************************************************************************************

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

# usuario REINICIO
if [ $USER = "reinicio" ]; then
sudo reboot
fi

************************************************************************************************************
************************************************************************************************************


	- Validamos que el usuario funcione.

http://www.ite.educacion.es/formacion/materiales/85/cd/linux/m1/administracin_de_usuarios_y_grupos.html


45. Instalación de paqueteria de prueba y desinstalación de Unity.

	-Instalación de drivers para Impresora

		- apt-get install bluez-cups* cups* indicator-printers* printer-driver-gutenprint*

	- Desinstalación de Unity

		- sudo apt-get remove unity unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-asset-pool unity-common unity-lens-applications unity-lens-files unity-lens-music unity-lens-video unity-scope-musicstores unity-scope-video-remote unity-services indicator-messages indicator-status-provider-mc5 appmenu-qt appmenu-gtk appmenu-gtk3 lightdm unity-greeter overlay-scrollbar zeitgeist zeitgeist-core zeitgeist-datahub activity-log-manager-common activity-log-manager-control-center

http://www.diolinux.com.br/2013/04/omo-remover-o-unity-completamente-do-ubuntu-sem-quebrar-o-sistema.html

	- sudo apt-get remove unity unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-5.0 unity-common libnux-2.0-0 nux-tools libunity-misc4 unity-2d-common

http://www.elblogderigo.info/2014/01/08/desinstalar-unity-e-instalar-gnome-classic/
