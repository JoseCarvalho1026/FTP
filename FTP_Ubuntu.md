# FTP
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

To use "FTP", you will need to install the [Graphical_Interface](https://github.com/JoseCarvalho1026/Graphical_Interface) and where it says `sudo apt install -y xrdp chromium-browser` you will need to add at the end `filezilla` .

In addition to the "Graphical Interface" you will need to install "netfilter-persistant" and "iptables-persistan" because of "ports":

◻️ `apt install netfilter-persistant iptables-persistant` ;

◻️ `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE` ;

◻️ `iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 20
-j DNAT --to-destination PRIVATE_IP` ;

◻️ `iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 21
-j DNAT --to-destination PRIVATE_IP` ;

◻️ `iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 10000:10100
-j DNAT --to-destination PRIVATE_IP` ;

◻️ `iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 990
-j DNAT --to-destination PRIVATE_IP` ;

◻️ `iptables -t nat -L -nv` ;

◻️ `netfilter-persistant save` ;

◻️ `nano /etc/sysctl.conf` ;

Uncomment:
```
net.ipv4.ip_forward=1
```
◻️ `sysctl -p` (confirm) .
