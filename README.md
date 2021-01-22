
# Documentazione della repository serverweb

Indice:
 - [Informazioni preliminari](#Informazioni-iniziali)<br>
 - [Installazione dei pacchetti necessari](#Installiamo-dei-pacchetti)<br> 
 - [Configurazione di rete](#Configuriamo-la-rete)<br>
 - [Controllare il file apache2](#Controlliamo-il-file-apache2)<br>
 - [Creazione degli utenti](#Creiamo-gli-utenti)<br>
 - [Creazione dello spazio per i siti](#Creiamo-lo-spazio-di-lavoro-dei-siti)<br>
 - [Creazione del file di configurazione per i siti](#Creiamo-il-file-di-configurazione-dei-siti)<br>
 - [Crezione del sito](#Esempio-di-html)<br>
 - [Installazione di Samba](#Installiamo-Samba-:woman_dancing:)
 
 ## Informazioni iniziali

1.Utilizzare una macchina virtuale:Ubuntu 20-04 64 Bit

2.Fare login con utente :adminuser e password:adminuser

3.Inserire i seguenti comandi

>sudo -i ; //per diventare amministratore

## Installiamo dei pacchetti

>sudo apt update
>
>sudo apt-get install apache2
>
>sudo apt install openssh-server
>
>sudo apt-get install vsftpd

## Configuriamo la rete

Definisci un ip statico per la tua macchina

>nano /etc/netplan/00-installer-config.yaml //modifica il file di configurazione

>
>
>     network:
>
>       version: 2
>
>       renderer: networkd
>
>       ethernets:
>
>         enp0s3:
>     
>           addresses: [172.16.29.109/16]  //inserire l'indirizzo che si vuole assegnare
>
>           gateway4: 172.16.1.7 //inserire l'indirizzo di default gateway
>
>           nameservers:
>
>               search: [virtual.marconi] // proprio dominio e di un altro dominio
>
>               addresses: [172.16.1.18, 172.16.1.10]  //indirizzo del proprio dominio e dell'altro dominio
>
>netplan try //applica le modifiche sul file
>
>netplan apply //applica le modifiche sul file ,solo nel caso in cui try non funzionasse
>
>ip link set enp0s3 up
>
>ip link set enp0s3 down

## Controlliamo il file apache2

Controllare che vengano gestiti i file dentro apache2

>cat cd /etc/apache2/apache2.conf
>

>
>       <>Directory /var/www/>
>            Options Indexes FollowSymLinks
>            AllowOverride None
>            Require all granted
>       </Directory>
>

## Creiamo gli utenti

Creiamo un utente per accesso unico alla cartella SitoA, SitoB e SitoC (per l'esempio prendiamo il Sito X)

>sudo useradd -s/bin/bash/ -d /var/www/SitoX -m usersitoX
>
> sudo passwd usersitoX
>
Configurare il file vsftp
>
>sudo nano /etc/vsftpd.conf
>
>
>       listen=yes
>
>       listen_ipv6=NO
>
>       anonymous_enable=NO
>
>       local_enable=YES
>
>       write_enable=YES
>
>       local_umask=022
>
>       dirmessage_enable=YES
>
>       use_localtime=YES
>
>       xferlog_enable=YES
>
>       connect_from_port_20=YES
>
>       xferlog_file=/var/log/vsftpd.log
>
>       xferlog_std_format=YES
>
>       ftpd_banner=Welcome to our FTP service.
>
>       chroot_local_user=YES
>
>       local_root=/var/www/$USER
>
>       user_sub_token=$USER
>
>       allow_writeable_chroot=YES
>
>       secure_chroot_dir=/var/run/vsftpd/emty
>
>       pam_service_name=vsftpd
>
>       rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.key
>
>       ssl_enable=NO
>
>       session_support=YES
>
>       log_ftp_protocol=YES
>
>
Salva ed Esci

## Creiamo lo spazio di lavoro dei siti

Creiamo lo spazio di lavoro per i Sito A, Sito B, Sito C(per l'esempio prendiamo il Sito X)
>cd /var/wwww/
>
>sudo mkdir SitoX
>
>cd Sitox
>
>sudo mkdir log
>
>sudo mkdir web
>
>cd web
>
>nano siteX.html
>
Riprendi "esempio html :exclamation:"

## Creiamo il file di configurazione dei siti

Creiamo il file di configurazione del Sito A,Sito B e Sito C (per l'esempio prendiamo il Sito X)
>cd /etc/apache2/sites-available
>
>sudo cp 000-default.com 00x-default.conf //inserisci il numero al posto di x
>
>sudo nano 000x-default1.conf
>
Vai su DocumentRoot /var/wwww/html e sostituisci /var/wwww/SitoX/web

Esci
>
>systemctl reload apache2
>
>sudo a2ensite 00x-default.conf
>


## Esempio di html :exclamation: 
Esempio di Html da scrivere all'interno di /vae/www/SitoX/web

>       <!DOCTYPE html>
>
>       <html>
>
>       <head>
>
>       <h1>Hi there!</h1>
>
>       <h3>html da file</h3>
>
>       </head>
>
>       <body>
>
>       <p> Hello world</p>
>
>       </body>
>
>       </html>
>
>
Salva ed esci

## Installiamo Samba :woman_dancing:


Prima di installare samba, aggiornare la propria macchina
>sudo apt-get update

Successivamente, si passa all'installazione di samba
>sudo apt-get install samba
>
