## Anonymous


HTTP Proxies
```
# Tests
https://hide.me/en/proxy

# Proxy lists
https://hidemy.name/en/proxy-list/

# Anonymous Tools
http://www.all-nettools.com/
https://centralops.net/co/
http://do-know.com/privacy-test.html
https://pentest-tools.com/


# TOR
https://www.torproject.org/ 

NOTE : TOR only works for TCP streams and can be used by any application with SOCKS support
```

HTTP_VIA / HTTP_X_FORWRDED_FOR
```
# Standart HTTP Communication string
REMOTE_ADDR = 98.10.50.155              # Target IP 
HTTP_ACCEPT_LANGUAGE = en
HTTP_USER_AGENT = Mozilla/4.0 (compatible; MISE 5.0; Windows 98)
HTTP_HOST = www.elearnsecurity.com
HTTP_VIA = not determined
HTTP_X_FORWARD = not determined

# Proxy Communication String
REMOTE_ADDR = 94.86.100.1               # Proxy IP
HTTP_ACCEPT_LANGUAGE = en
HTTP_USER_AGENT = Mozilla/4.0 (compatible; MISE 5.0; Windows 98)
HTTP_HOST = www.elearnsecurity.com
HTTP_VIA = 94.86.100.1 (Squid/5.4.STABLE7)    # Proxy IP
HTTP_X_FORWARD = 98.10.50.155                 # Target IP

# High Anonymity Proxy Communication String
REMOTE_ADDR = 94.86.100.1                     # Proxy IP
HTTP_ACCEPT_LANGUAGE = en
HTTP_USER_AGENT = Mozilla/4.0 (compatible; MISE 5.0; Windows 98)
HTTP_HOST = www.elearnsecurity.com
HTTP_VIA = not determined
HTTP_X_FORWARD = not determined
```


Tunneling For Anonymity
```
# There are specifically 2 effective types for anonymity: SSH and IPSEC VPNs

# Local Port Forwarding Through SSH
ssh -L [LOCAL PORT TO LISTEN ON]:[REMOTE MACHINE]:[REMOTE PORT] [USERNAME]@[SSHSERVER]

# Create a tunnel from our local port 3000, to the localhost address on the SSH server, on port 3306
ssh -L 3000:localhost:3306 els@192.168.231.135

```

## Social Engineering
