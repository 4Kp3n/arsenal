# OSEP 
% OSEP 

## Performant RDP connection
#platform/linux #target/remote #cat/Misc
```
xfreerdp /cert:ignore /bpp:8 /compression +clipboard -themes -wallpaper /auto-reconnect /h:800 /w:1400 /u:Offsec /p:'lab' /v:<ip_address|192.168.1.1>
```

## Lower the MTU for tun0
#platform/linux #target/remote #cat/Misc
```
sudo ip link set dev tun0 mtu 1250
```
