
# Documentazione della repository serverweb

1.Utilizzare una macchina virtuale:Ubuntu 20-04 64 Bit
2.Fare login con utente :adminuser e password:adminuser
3.Inserire i seguenti comandi
>sudo -i ; //per diventare amministratore
>apt install openssh-server

fix ip

nano /etc/netplan/

netplan try o netplan apply

network:
  version: 2
  renderer: networkd
  ethernets:
    eth1:
      addresses: [10.10.10.2/24]
      gateway4: 10.10.10.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [10.10.10.1, 1.1.1.1]
ip link set eth1 up
ip link set eth1 down
ssh da putty

apt install apache2
apt install mc
mcedit /etc/hosts
mcedit /etc/hostname
apt install net-tools
