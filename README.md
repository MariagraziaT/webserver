
# Documentazione della repository serverweb

1.Utilizzare una macchina virtuale:Ubuntu 20-04 64 Bit

2.Fare login con utente :adminuser e password:adminuser

3.Inserire i seguenti comandi

>sudo -i ; //per diventare amministratore
>
>apt install openssh-server
>
4.Definisci un ip statico per la tua macchina
>nano /etc/netplan/00-installer-config.yaml
>
>network:
> version: 2
> renderer: networkd
> ethernets:
>   enp0s3:
>     addresses: [10.10.10.2/24]
>     gateway4: 10.10.10.1
>     nameservers:
>         search: [mydomain, otherdomain]
>         addresses: [10.10.10.1, 1.1.1.1]
>
>netplan try
>netplan apply //solo nel caso in cui try non funzionasse
>
>ip link set eth1 up
>ip link set eth1 down

5. Collegarsi alla macchina con modalità ssh da putty oppure continuare con la macchina

>apt install apache2
>
>apt install mc
>
>mcedit /etc/hosts
>
>mcedit /etc/hostname
>
>apt install net-tools
>
