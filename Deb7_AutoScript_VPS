#!/bin/bash
#
# Original script by fornesia, rzengineer and fawzya
# Mod by Bustami Arifin
# Translation by _PakTam_
# ==================================================

# Initializing Var
export DEBIAN_FRONTEND=noninteractive
OS=`uname -m`;
MYIP=$(wget -qO- ipv4.icanhazip.com);
MYIP2="s/xxxxxxxxx/$MYIP/g";

# Details of _PakTam_
country=MY
state=Kuala_Lumpur
locality=Kuala_Lumpur
organization=Bystander
organizationalunit=Bystander
commonname=Bystander
email=arelift.sgs4@gmail.com

# go to root
cd

# disable ipv6
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
sed -i '$ i\echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6' /etc/rc.local

# install wget and curl
apt-get update;apt-get -y install wget curl;

# set time GMT +8
ln -fs /usr/share/zoneinfo/Asia/Kuala_Lumpur /etc/localtime

# set locale
sed -i 's/AcceptEnv/#AcceptEnv/g' /etc/ssh/sshd_config
service ssh restart

# set repo

# update
apt-get update

# install webserver
apt-get -y install nginx

# install essential package
apt-get -y install nano iptables dnsutils openvpn screen whois ngrep unzip unrar


# install squid3
cd
apt-get -y install squid3
wget -O /etc/squid3/squid.conf "https://raw.githubusercontent.com/PakTam/Deb7AutoScriptVPS/master/squid3.conf"
sed -i $MYIP2 /etc/squid3/squid.conf;
service squid3 restart

# install fail2ban
apt-get -y install fail2ban;
service fail2ban restart

# install ddos deflate
cd
apt-get -y install dnsutils dsniff
wget https://github.com/PakTam/Deb7AutoScriptVPS/raw/master/ddos-deflate-master.zip
unzip ddos-deflate-master.zip
cd ddos-deflate-master
./install.sh
rm -rf /root/ddos-deflate-master.zip

#xml parser
cd
apt-get -y --force-yes -f install libxml-parser-perl

# finishing
cd
service squid3 restart
rm -rf ~/.bash_history && history -c
echo "unset HISTFILE" >> /etc/profile

# install neofetch
echo "deb http://dl.bintray.com/dawidd6/neofetch jessie main" | tee -a /etc/apt/sources.list
curl "https://bintray.com/user/downloadSubjectPublicKey?username=bintray"| apt-key add -
apt-get update
apt-get install neofetch


# info
clear
echo "Deb7AutoScriptVPS Includes:" | tee log-install.txt
echo "===========================================" | tee -a log-install.txt
echo ""  | tee -a log-install.txt
echo "Service"  | tee -a log-install.txt
echo "Squid3   : 8000, 8080 (limit to IP SSH)"  | tee -a log-install.txt
echo ""  | tee -a log-install.txt
echo "Other Features"  | tee -a log-install.txt
echo "----------"  | tee -a log-install.txt
echo "DDoS Deflate   : Anti-DDOS"  | tee -a log-install.txt
echo "Timezone       : Asia/Kuala_Lumpur (GMT +8)"  | tee -a log-install.txt
echo "IPv6           : [off]"  | tee -a log-install.txt

echo ""  | tee -a log-install.txt
echo "Original Script by Fornesia, Rzengineer & Fawzya"  | tee -a log-install.txt
echo "Modified by Bustami Arifin"  | tee -a log-install.txt
echo "Translation by _PakTam_"  | tee -a log-install.txt
echo ""  | tee -a log-install.txt
echo "Installation Logs --> /root/log-install.txt"  | tee -a log-install.txt
echo ""  | tee -a log-install.txt
echo "VPS Auto Reboot at 12 AM"  | tee -a log-install.txt
echo ""  | tee -a log-install.txt
echo "==========================================="  | tee -a log-install.txt
cd
rm -f /root/Deb7AutoScriptVPS
