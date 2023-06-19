### Information Gathering

##### Search Engines

Google Dork :
```Google
site:[website] filetype:[filetype]
```

```Google
cache:[URL]
```

theHarvester :
```bash
theharvester -d  domain.com -l 100 -b google
```
- **-d** is the domain
- **-l** limits the results to the value specified
- **-b** data source

Interesting Tools :
- [DNSdumpster](https://dnsdumpster.com/)
- [Shodan](https://www.shodan.io)
- [Exploits Shodan](https://exploits.shodan.io)
- [FOCA](https://www.elevenpaths.com/labstools/foca/index.html)
- [Maltego](https://www.maltego.com)

##### DNS Enumeration

Whois :
```bash
whois domain.com
```

IP Resolve :
```bash
dig domain.com
```
```bash
nslookup domain.com
```

Nameserver lookup :
```bash
dig domain.com NS
```
```bash
nslookup -type=NS domain.com
```


Reverse DNS lookup :
```bash
dig domain.com PTR
```
```bash
nslookup -type=PTR domain.com
```

Mail Exchange lookup :
```bash
dig domain.com MX
```
```bash
nslookup -type=MX domain.com
```

Zone transfers :
```bash
dig axfr @DNS_IP domain.com
```
```bash
nslookup
> server [nameserver for domain.com]
> 1s -d domain.com
```


DNS Tools :
```bash
fierce --domain domain.com 
```
```bash
fierce --domain domain.com --dns-servers {IP}
```

```bash
dnsenum domain.com
```
```bash
dnsenum domain.com --dnsserver {DNS IP}
```
```bash
dnsenum domain.com -f {subdomain file}
```

```bash
dnsmap domain.com
```
```bash
dnsmap domain.com -w {subdomain file}
```

```bash
dnsrecon -d domain.com
```
```bash
dnsrecon -d domain.com -n {NS IP}
```
```bash
dnsrecon -d domain.com -{scan option}
```


### Scanning


##### **Host discovery**


```bash
fping -asgq 192.168.1.0/24
```
```bash
nmap -sn 192.168.1.0/24
```
```bash
hping3 -1 192.168.1.x --rand-dest -I eth0
```

```bash
nmap -sS -p53 [NETBLOCK]
```
```bash
nmap -sU -p53 [NETBLOCK]
```


##### **Scanning techniques**

```
nmap -sS target                         # SYN scan
nmap -sA target                         # ACK scan
nmap -sF target                         # FIN scan
nmap -sN target                         # Null scan
nmap -sO target                         # IP Protocol scan
nmap -sX target                         # XMAS scan

hping3 -S target -c 1                         # SYN scan
hping3 -A target -c 1                         # ACK scan
hping3 -F target -c 1                         # FIN scan
hping3 -F -P -U target -c 1                   # XMAS scan
```

Idle/Zombie scan
```
nmap -O -v -n targetZombie
nmap --script ipidsec targetZombie
nmap -Pn -sI [targetZombie]:[port] [target] -p [port] -v
```

```
hping3 -S -r -p [port] [targetZombie]
hping3 -a [targetZombie] -S -p [port] [target]
```

FTP bounce scan :
```
nmap -Pn -b [ftpvulnerable] [target]
```



##### **Service and OS detection**

```
nc [targetIP]:[Port]                      # Banner Grabbing
nmap -sV target                           # Version Scan
nmap -sV -sC target                       # Version/Script Scan
nmap -O target                            # OS Detection
nmap -A target                            # Version/Script/OS/Traceroute Scan
```

```
./p0f -i [interface]
```


##### **Firewall/IDS Evasion**


Fragmentation 
```
nmap -sS -f [target]
nmap -sS -f --data-lenght 100 [target]
```

Decoy 
```
nmap -sS -D [spoofIP],[spoofIP],ME,[spoofIP] [target]
nmap -sS -D RND:10 [target]
```

Source ports
```
nmap -sS --source-port [source port] [target]
hping3 -S -s [source port] [target]
```

Packet header 
```
nmap -sS --data-lenght 10 [target]
hping3 -S --data 24 [target] -p [port]
```

Mac address spoofing
```
nmap -sS --spoof-mac [mac] [target]
```

Timing
```
nmap -iL [hosts.txt] -sS -T [Timing option]

0 - 5 min
1 - 15 sec
2 - 0.4 sec
3 - default
4 - 1 msec
5 - 5 msec
```







### Enumeration


##### NetBIOS 


NetBIOS enumeration from Windows
```
nbtstat -n                                 #NetBIOS names on our machine

nbtstat -A <target_IP>                     #NetBIOS names on target machine
```

NetBIOS enumeration from Linux
```
nbtscan -v <target_IP>                     #NetBIOS names on target machine

nbtscan -v <target_IP>/24                  #NetBIOS names with subnetmask
```



##### SMB Shared folder 

Resource enumeration from Windows
```
net view <target_IP>                       #List shared resources

net use K: \\{target IP}\{Share}           #Connect shared resource 
```

BruteForce attempts for shares with [Nat10bin](https://github.com/Phenomite/Old-tools-to-keep)
```
nat.exe -u <userlist> -p <passlist> <target_IP>
```


Resource enumeration from Linux
```
smbclient -L <target_IP>                   #List shared resources

mount.cifs //{target_IP}/{Share} /media/myshare/ user=,pass=.   #Mount share
```


##### Null Session

Check if system is vulnerable against **Null Session**
```
net use \\<target IP>\IPC$ "" /u:""
```

Tools to enumerate target through **Null Session** - Windows

[Dumpsec](https://www.systemtools.com/somarsoft/index.html)
```
1. Click `Report` -> `Select Computer` -> Insert Target IP
2. Click `Report` -> `Dump Users as column`
3. After everything is set, click `OK`
```
[Winfingerprint](https://github.com/kkuehl/winfingerprint)  

[Winfo](https://www.vidstromlabs.com/freetools/winfo/)
```
winfo <taget_IP> -n
```



Tools to enumerate target through **Null Session** - Linux

```
enum4linux <target_IP>

rpcclient -N -U "" <target_IP>
```



##### SNMP

