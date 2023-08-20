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

```
# Setoolkit Tool
https://github.com/trustedsec/social-engineer-toolkit
```

Linux test.deskstop
```
[Desktop Entry]
Type=Application
Name=Update
Exec=/bin/bash ls -la
Icon=/usr/share/yelp-xsl/xslt/common/icons/yelp-note-important.svg
```

[Linux test.desktop generator](https://github.com/password-reset/LinDrop/tree/master)




# PowerShell for Pentesters

```
# PowerSploit
https://github.com/PowerShellMafia/PowerSploit 
```

## PowerShell Fundamentals

```
# Executable Folders
C:\Windows\System32\WindowsPowerShell        # 64 Bit OS
C:\Windows\SysWOW64\WindowsPowerShell        # 32 Bit OS

# PS History file
%AppData%\Microsoft\Windows\PowerShell\PSReadLine

# Check if PS Process is running as 64 Bit
PS > [environment]::Is64BitOperatingSystem

# PS Help menu
PS > powershell /?

# ExecutionPolicy Bypass
PS > Get-ExecutionPolicy
PS > Set-ExecutionPolicy Bypass -Scope Process

C:\> powershell -ExecutionPolicy Bypass .\script.ps1
C:\> powershell -ExecutionPolicy Unrestricted .\script.ps1


# Hides PS Window
C:\> powershell -WindowStyle Hidden .\script.ps1


# Specify Command or Script Block
C:\> powershell -Command [Command or Script Block]
C:\> powershell -Command Invoke-Command -ScriptBlock { Get-Process }
C:\> powershell -Command Invoke-Command -ScriptBlock { Get-EventLog -LogName security }"

PS > Invoke-Command -ScriptBlock { param($p1, $p2)
    "p1: $p1"
    "p2: $p2"
    } -ArgumentList "First", "Second"


# Execute Base64 encoded script
PS > $string = {Get-Process}
PS > $encodedcommand = [Convert]::ToBase64String([Text.Encoding]::Unicode.GetBytes($string))
PS > powershell.exe -EncodedCommand $encodedcommand


# Execute Script with NoProfile Parameter
C:\ > powershell -NoProfile .\script.ps1


# Downgrade PS Version to 2
C:\ > powershell -Version 2


# Abbreviated above commands

powershell.exe -ep Bypass         # ExecutionPolicy Bypass
powershell.exe -ex by             # ExecutionPolicy Bypass

powershell.exe –enco              # EncodedCommand
powershell.exe –ec                # EncodedCommand

powershell.exe –W h               # WindowStyle Hidden
powershell.exe –Wi hi             # WindowStyle Hidden



# Get-Help - Obtain Information
PS > Get-Help Get-Help
PS > Get-Help Get-Process -Full
PS > Get-Help Get-Process -Examples
PS > Get-Help Get-Process -Online
PS > Get-Update


# List all Cmdlets, Alliases, Functions, Workflows, Filters, Scripts
PS > Get-Command 
PS > Get-Command -Name *Firewall*

```

Cmdlets
```
# List all Properties of Cmdlets
PS > Get-Process | Format-List *
PS > Get-Process | Select-Object -Property *

# Pipeline 
PS > Get-Process | Select-Object -Property Processname
PS > Get-Process | Select-Object -First 10
PS > Get-Process | Sort-Object -Unique 
PS > Get-Process | Sort-Object -Unique | Select-Object -First 10

# List All Aliases
PS > Get-Alias
PS > Get-Alias -Definiton -Get-Process 

# WMI Objects - Operating System
PS > Get-WmiObject -Class win32_operatingsystem  | Select-Object -Property 

# WMI Objects - Services
PS > Get-WmiObject -Class win32_service  | fl *
PS > Get-WmiObject -Class win32_service  | Sort-Object -Unique PathName | fl PathName

# List all Services
PS > Get-Service | Sort-Object Status -Descenting

# Export-CSV
PS > Get-Process | Export-Csv C:\Process.csv

# Exploring Windows Registry
PS > cd HKLM:\
PS > cd .\SOFTWARE\Microsoft\Windows\CurrentVersion

# Find *.txt files in Directory with Pattern - pass*
PS > Select-String -Path C:\Directory\*.txt -Pattern pass*

# Find with Recursively - Root Directory - C:\ | Pattern - pass* | File Extension - *.txt
PS > ls -r C:\ -File *.txt | % {Select-String -Path $_ -Pattern pass*}

```

Modules
```
# List of Imported Modules
PS > Get-Module
PS > Get-Module -ListAvailable

# Import Module
PS > Import-Module .\script.psm1

# PowerSploit
https://github.com/PowerShellMafia/PowerSploit

PS > Improt-Module PowerSploit             # Import Module
PS > Get-Module                            # Check
PS > Get-Command -Module Powersploit # List All Available Commands of PowerSplloit


PS > Get-Help Invoke-PrivescAudit       # Help on cmdlet
PS > Get-Help Wrtie-HijackDll           # Help on cmdlet


```

[Writing a Windows PowerShell Module
](https://learn.microsoft.com/en-us/powershell/scripting/developer/module/writing-a-windows-powershell-module?view=powershell-7.3&viewFallbackFrom=powershell-7)



Scripts
```
# Script which takes an Argument and list files
Param(
    [Parameter(mandatory=$true)][string]$file
)
Get-Content "$file"

# Alternate of code above
PS > $file = "script.txt"
PS > Get-Content $file

# Foreach Loop
PS > $services = Get-Service
PS > ForEach-Object ($service in $services) { $service.Name }
```






