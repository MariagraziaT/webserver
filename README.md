
# Documentazione della repository serverweb

1.Utilizzare una macchina virtuale:Ubuntu 20-04 64 Bit

2.Fare login con utente :adminuser e password:adminuser

3.Inserire i seguenti comandi

>sudo -i ; //per diventare amministratore
>
>apt install openssh-server //installa il server openssh
>
4.Definisci un ip statico per la tua macchina

>nano /etc/netplan/00-installer-config.yaml //modifico il file di configurazione

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

>apt install apache2 //installa il server apache
>
>apt install mc 
>
>mcedit /etc/hosts
>
>mcedit /etc/hostname
>
>apt install net-tools
>
