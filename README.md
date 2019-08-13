# arch-black-screen

This is my system:

```bash
[sakib@fullbrick ~]$ neofetch 
                   -`                    sakib@fullbrick 
                  .o+`                   --------------- 
                 `ooo/                   OS: Arch Linux x86_64 
                `+oooo:                  Host: HP Pavilion Notebook 
               `+oooooo:                 Kernel: 5.2.8-arch1-1-ARCH 
               -+oooooo+:                Uptime: 1 min 
             `/:-:++oooo+:               Packages: 817 (pacman) 
            `/++++/+++++++:              Shell: bash 5.0.7 
           `/++++++++++++++:             Resolution: 1366x768 
          `/+++ooooooooooooo/`           DE: KDE 
         ./ooosssso++osssssso+`          WM: KWin 
        .oossssso-````/ossssss+`         Theme: Breeze Dark [KDE], Breeze [GTK2/3] 
       -osssssso.      :ssssssso.        Icons: Numix-Circle [KDE], breeze [GTK2/3] 
      :osssssss/        osssso+++.       Terminal: konsole 
     /ossssssss/        +ssssooo/-       Terminal Font: Hack 10.5 
   `/ossssso+/:-        -:/+osssso+-     CPU: Intel i5-5200U (4) @ 2.700GHz 
  `+sso+:-`                 `.-/+oso:    GPU: Intel HD Graphics 5500 
 `++:.                           `-/+/   GPU: NVIDIA GeForce 940M 
 .`                                 `/   Memory: 834MiB / 11930MiB 

```

When I Installed nvidia GPU driver using 

```bash
sudo pacman -S nvidia
```
It just worked out of the box. I was able to get output of ```nvidia-smi```.   
There was a problem, When I boot my laptop, when the login page was shown the screen turned black. I had to write my password blindly. It was a problem. 

## Solve

Install [xorg-xrandr](https://www.archlinux.org/packages/?name=xorg-xrandr):   
```bash
sudo pacman -S xorg-xrandr
```

at ```/usr/share/sddm/scripts/Xsetup``` add the following lines:   
```bash
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto
```

and reboot. ***We are done.*** 

