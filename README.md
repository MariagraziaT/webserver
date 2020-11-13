
# Documentazione della repository serverweb

1.Utilizzare una macchina virtuale:Ubuntu 20-04 64 Bit

2.Fare login con utente :adminuser e password:adminuser

3.Inserire i seguenti comandi

>sudo -i ; //per diventare amministratore
>
>apt install openssh-server //installa il server openssh
>
4.Definisci un ip statico per la tua macchina

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
>           addresses: [10.10.10.2/24]  //inserire l'indirizzo che si vuole assegnare
>
>           gateway4: 10.10.10.1 //inserire l'indirizzo di default gateway
>
>           nameservers:
>
>               search: [mydomain, otherdomain] // proprio dominio e di un altro dominio
>
>               addresses: [10.10.10.1, 1.1.1.1]  //indirizzo del proprio dominio e dell'altro dominio
>
>netplan try //applica le modifiche sul file
>
>netplan apply //applica le modifiche sul file ,solo nel caso in cui try non funzionasse
>
>ip link set enp0s3 up
>
>ip link set enp0s3 down

5. Collegarsi alla macchina con modalità ssh da putty oppure continuare con la macchina

>sudo apt-get install apache2 //installa il server apache
>
>sudo apt install openssh-server
>
6. Sito A:
>cd /etc/apache2/sites-available
>
>sudo cp 000-default.com 001-default.conf
>
>sudo nano 000-default1.conf
>
Vai su DocumentRoot /var/wwww/html e sostituisci /var/wwww/SitoA
Esci
>
>systemctl reload apache2
>
>sudo a2ensite 001-default.conf
>cd /var/wwww/
>sudo mkdir SitoA
>
>cd SitoA
>
>sudo mkdir internet
>
>cd internet
>
>nano siteA.html
>
>
>
>
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
7. Site B
>cd /etc/apache2/sites-available
>
>sudo cp 000-default.com 001-default.conf
>
>sudo nano 000-default1.conf
>
Vai su DocumentRoot /var/wwww/html e sostituisci /var/wwww/SitoA
Esci
>
>systemctl reload apache2
>
>sudo a2ensite 001-default.conf
>cd /var/wwww/
>sudo mkdir SitoA
>
>cd SitoA
>
>sudo mkdir internet
>
>cd internet
>
>nano siteA.html
>
>
>
>
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
8.Site C
>cd /etc/apache2/sites-available
>
>sudo cp 000-default.com 001-default.conf
>
>sudo nano 000-default1.conf
>
Vai su DocumentRoot /var/wwww/html e sostituisci /var/wwww/SitoA
Esci
>
>systemctl reload apache2
>
>sudo a2ensite 001-default.conf
>cd /var/wwww/
>sudo mkdir SitoA
>
>cd SitoA
>
>sudo mkdir internet
>
>cd internet
>
>nano siteA.html
>
>
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
