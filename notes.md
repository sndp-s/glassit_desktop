There exists several display servers (for example: Xorg and wayland) these haev their own compositor (the thing that 'composes' the final image (of the various application windows) that we see on the desktop)

Ubuntu made a switch to wayland system in their newer version but maintained a compatibility layer with xorg (probably not perfectly complete compatibiliy)

These two display servers xorg and waylang have different corresponding tool to configure them xtool and sway something respectively.

These is what will help me manipulate the opacity of a window in xorg environment.

Example
```bash
xprop -f _NET_WM_WINDOW_OPACITY 32c -set _NET_WM_WINDOW_OPACITY $(printf 0x%x $((0xffffffff * 80 / 100)))
```
This might work in Ubuntu for now due the presence of that wayland xorg compatibility layer but is not really a right approach to take for the long term so I will add a desktop server name check in my scipt and only issue appropriate desktop server specific commands. 

TODO: figure out the active window from where the shortcut command is issued from.

TODO: tie two above two components (the configurator and the active window identifier) with a driver interface (shortcut keys)


# xbindkeys method
Lets simply install this application and setup config to create my menu driven program
.xbindkeysrc - the config file to bind shortcuts with commands

## reference .xbindkeyssrc
```
"python ~/glassit.py stepdown"
control + alt + z

"python ~/glassit.py reset"
control + alt + x

"python ~/glassit.py stepup"
control + alt + c
```
