# Active Directory

% Arch Linux

## pacman - switch branch
#platform/Linux #target/local #cat/OWN
```
pacman-mirrors --api --set-branch <branch|unstable>
```
## pacman - rebuild the mirrorlist (after changing branches)
#platform/Linux #target/local #cat/OWN
```
sudo pacman-mirrors --fasttrack 5 && sudo pacman -Syyu
```