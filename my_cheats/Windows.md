# Windows

## winrm - start winrm service
```
winrm quickconfig
```

## PowerShell - allow winrm connections
```
Enable-PSRemoting -force
```

## netsh - enable network discovery
```
netsh advfirewall firewall set rule group=”network discovery” new enable=yes
```

## PowerShell - set network type to private
```
Set-NetConnectionProfile -NetworkCategory Private
```

## PowerShell - deactivate Windows Defender firewall
```
Set-NetFirewallProfile -Profile Domain,Private,Public -Enabled False
```

## PowerShell - set new password for <user>
```
$Password = ConvertTo-SecureString "<password>" -AsPlainText -Force;
Set-LocalUser -Name "<user>" -Password $Password
```

## PowerShell - disable Microsoft Defender
```
Set-MpPreference -DisableRealtimeMonitoring $true
```


## icacls - list permissions of file
```
icacls <file|C:\>
```

## wmic - list processes detailed
```
wmic process list full
```

## wmic - list services detailed
```
wmic service list full
```

## sc.exe - register a new service
#platform/windows #target/local #cat/[OWN]
```
sc.exe create <ServiceName> binPath= <PathToService|"C:\path\to\MyService.exe">
```

## ipconfig - flush DNS resolver cache
#platform/windows #target/local #cat/[OWN]
```
ipconfig /flushdns
```

## taskkill - kill a specific task based on PID
#platform/windows #target/local #cat/[OWN]
```
taskkill /pid <pid>
```

## schtasks - Show sheduled tasks
#platform/windows #target/local #cat/[OWN]
```
schtasks /query /fo LIST /v
```

## utility - Show nice directory tree
#platform/windows #target/local #cat/[OWN]
```
tree /F /A
```

## utility - Change password of user
#platform/windows #target/local #cat/[OWN]
```
net user <user> <pass>
```

## utility - List dotnet versions
#platform/windows #target/local #cat/[OWN]
```
dotnet --list-sdks
```

## utility - New logon session accessing network services
#platform/windows #target/local #cat/[OWN]
```
runas /user:<domain>\<username> /netonly cmd.exe #access network services
```

% Windows PrivEsc, situational awareness
#platform/windows #target/local #cat/[OWN]
## PowerShell - list all installed 32-bit application via registry
```
Get-ItemProperty "HKLM:\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname
```
#platform/windows #target/local #cat/[OWN]
## PowerShell - list all installed 64-bit application via registry
```
Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\*" | select displayname
```

## PowerShell - list running processes
#platform/windows #target/local #cat/[OWN]
```
Get-CimInstance -ClassName win32_service | Select Name,State,PathName | Where-Object {$_.State -like 'Running'}
```

## Setup - Install Chocolatey (ADMIN)
#platform/windows #target/local #cat/[OWN]
```
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```
