---
sidebar_position: 4
---

# How to run GTA 5 of Epic Games on Void Linux

## Legendary Launcher

Legendary launcher is a terminal based epic games launcher. And yes, it lives up to the name, it's my favorite FOSS. Very minimal and way better than the og epic launcher!

I found it from here and installed the void linux package.

https://github.com/derrod/legendary

To log in 

```bash
legendary auth
```

To see your games

```bash
legendary list-games
```

This is what it shows me

![epic games list](https://cdn.discordapp.com/attachments/750250354771361805/859292408507400253/unknown.png)


And installing is like

```bash
legendary install [App name]
```

## Steps

Installing GTAV was like this

```bash
legendary install 9d2d0eb64d5c44529cece33fe2a46482
```

And to launch I would just

```bash
prime-run legendary launch 9d2d0eb64d5c44529cece33fe2a46482
```

EDIT- On a new system it worked out of the box. I believe it's because Wine had updated to 6.12. Well if it doesn't launch OOTB you could try the steps below.

But it didn't work out of the box. I first got some error where it would fail to verify my data. After a little bit of googling I found out that I could run it through proton as well. 

[This commment](https://www.reddit.com/r/linux_gaming/comments/ncu4f3/gta_v_doesnt_launch_using_legendary_quits_after/gy77f1l?utm_source=share&utm_medium=web2x&context=3) mentioned that you need to add ``PlayGTAV.exe`` in steam. I then looked up how to add it to steam. Turns out its pretty simple

Then I found [this](https://www.reddit.com/r/linux_gaming/comments/be4e46/how_to_play_nonsteam_games_through_proton_this/) thread, these are the steps

1. Go to add a game and add the game executable from the folder it is contained.

2. Go to the games properties on Steam and force Proton use.

3. Go to Launch options and Add --wine or --proton to the box. ( I added --proton)

I then tried the suggestions of [this](https://www.reddit.com/r/linux_gaming/comments/mwn47f/how_i_got_tony_hawks_pro_skater_1_2_running_on/) thread.

I created a directory ``~/.proton``

Then added the following to ``~/.config/legendary/config.ini``

```bash
[Legendary]

[9d2d0eb64d5c44529cece33fe2a46482]
wrapper = "/home/pixelfog/.steam/steam/steamapps/common/Proton 6.3/proton" run
no_wine = true

[9d2d0eb64d5c44529cece33fe2a46482.env]
STEAM_COMPAT_DATA_PATH = /home/pixelfog/.proton/
STEAM_COMPAT_CLIENT_INSTALL_PATH = .local/share/Steam/
```

(First line was already there, and I had to add the last environment variable as well cuz I'd get some error without it)

I thought I was all done, no. When i tried launching I got this error

```bash
eventfd too many open files
```

I found out that all I had to do was increase my ``ulimit`` by making my system ready for Esync.

https://github.com/lutris/docs/blob/master/HowToEsync.md

my current ``ulimit`` was 4096, I had to increase it to 500000+

I followed the second method

```
Modifying ulimits.conf
On Linux distributions not using Systemd or distributions using pam-limits.conf (Arch Linux, Fedora, Solus,... ), you (with root privileges or sudo) need to edit /etc/security/limits.conf.
Change username to your actual username. Once the file is edited, reboot for the changes to take effect, and verify by running ulimit -Hn to see the new limit (524288).
```

```bash
username hard nofile 524288
```

And after this I had to add the line 

```bash
session required /lib/security/pam_limits.so
```

to ``/etc/pam.d/login`` and ``/etc/pam.d/lxdm`` (my display manager) at the bottom.

After saving and rebooting ``ulimit -Hn`` showed the value I put!

And this time GTA 5 finally worked!!!

## Optional

I installed ``MangoHud`` package to monitor my FPS, I just had to add it like this while launching my game

```bash
prime-run mangohud legendary launch 9d2d0eb64d5c44529cece33fe2a46482
```

![fps](https://cdn.discordapp.com/attachments/750250354771361805/859303923668090890/IMG_20210629_095755.jpg)

I also set my CPU scaling governor to ``performance``, my default was ``powersave`` 

I installed ``cpupower`` package for it. And then I did this

```bash
cpupower -c all frequency-set -g performance
```

This sets all the cores to performance mode(requires sudo previleges).

This really improved my fps, and I turned it off back to powersave after closing the game.

This is how you check the CPU scaling governor

```bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```





