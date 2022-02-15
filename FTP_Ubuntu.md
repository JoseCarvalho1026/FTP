# FTP
### In "www.inova.pt"
◻️ `apt install vsftpd` ;

◻️ `systemctl status vsftpd` ;

◻️ `nano /etc/vsftpd.conf` ;

Certificates:
```
Uncomment "write_enable=YES"
Change certificate names
```
Insecure FTP:
```
To add:
pasv_enable=YES
pasv_min_port=10000
pasv_max_port=10100
```
Explicit FTP:
```
To alter "ssl_enable=YES"
To add:
pasv_enable=YES
pasv_min_port=10000
pasv_max_port=10100

allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH
```
Implicit FTP:
```
To alter "ssl_enable=YES"
To add:
pasv_enable=YES
pasv_min_port=10000
pasv_max_port=10100

allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
require_ssl_reuse=NO
ssl_ciphers=HIGH

implicit_ssl=YES
listen_port=990
```
◻️ `systemctl restart vsftpd` ;

◻️ `systemctl status vsftpd` .

To use "FTP", you will need to install [Graphical_Interface](https://github.com/JoseCarvalho1026/Graphical_Interface) on "remote.client.pt" and where it says `sudo apt install -y xrdp chromium-browser` you will need add `filezilla` at the end.

In addition to the "Graphical Interface", you will need to add the necessary ports in [iptables](https://github.com/JoseCarvalho1026/Iptables/blob/main/Ubuntu.md) for "FTP" to work correctly, so you must go to "control.inova.pt" and add the commands for "FTP"; 
