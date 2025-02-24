Problem:
	I found the volume to be significantly lower on opensuse when compared to windows. 
1. Find which multimedia service is being used. My system which is suse tumbleweed gnome, uses pipewire as default.
	1.1: check if you use pipewire or pulseaudio
```
		systemctl --user status pipewire
```

```
		systemctl --user status pulseaudio
```

**Note to run this without sudo**

[[Issues]]