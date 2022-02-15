# ProFTP

◻️ `sudo amazon-linux-extras install epel` ;

◻️ `yum install proftpd` ;

To use the certificates, you must use "easy-rsa" [Certificates_Installation](https://github.com/JoseCarvalho1026/Certificates_Installation) which is installed on "control.inova.pt" . Using the following code `./easyrsa build-server-full proftp.www.enta.pt nopass` will create the certificates for ftp and then copy the "*.crt" and "*.key" to their respective locations.

Put the certificates in:
```
proftp.www.enta.pt.crt in /etc/ssl/certs
proftp.www.enta.pt.key in /etc/ssl/private
```
◻️ `nano /etc/proftpd.conf` ;
To add:
```
# Cause every FTP user except adm to be chrooted into their home directory
DefaultRoot                     ~ !adm
PassivePorts    10000   10100
```
Comment:
```
#<IfDefine TLS>
```
Edit the certificates area with the respective place where they are:
```
TLSRSACertificateFile         /etc/ssl/certs/proftp.www.enta.pt.crt
TLSRSACertificateKeyFile      /etc/ssl/certs/proftp.www.enta.pt.key 
```
Uncomment this line:
```
TLSRenegotiate                ctrl 3600 data 512000 required off timeout 300
```
Comment this 4 following lines:
```
#  <IfModule mod_tls_shmcache.c>
#    TLSSessionCache            shm:/file=/var/run/proftpd/sesscache
#  </IfModule>
#</IfDefine>
```
◻️ `systemctl enable --now proftpd` ;

To use "FTP", you will need to install [Graphical_Interface](https://github.com/JoseCarvalho1026/Graphical_Interface) on "remote.client.pt" and where it says `sudo apt install -y xrdp chromium-browser` you will need add `filezilla` at the end.

In addition to the "Graphical Interface", you will need to add the necessary ports in [iptables](https://github.com/JoseCarvalho1026/Iptables/blob/main/Ec2-user.md) for "FTP" to work correctly, so you must go to "control.enta.pt" and add the commands for "FTP"; 
