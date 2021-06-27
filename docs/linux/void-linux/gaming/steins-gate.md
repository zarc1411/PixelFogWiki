---
sidebar_position: 2
---

# How to install Steam improvement patch for Steins;Gate


## Introduction
I was able to run Steins;Gate just fine, but the font was terrible, and later I found out I could download a patch that would fix it. This is the patch

http://sonome.dareno.me/projects/sghd.html

## Steps to Install Patch

1. Go to the link above and download the zip file.
2. Then extract it to this directory
   ```bash
   ~/.steam/steam/steamapps/common/'STEINS;GATE'/
   ```
3. Install the ``wine`` package if you haven't already
4. Now you need to run a command in the game's prefix. For this navigate to the directory
   ```bash
   ~/.steam/steam/steamapps/compatdata/412830/pfx/drive_c/windows/system32/
   ```

   ``412830`` is the game ID of the steam. ``pfx`` is the windows prefix.
5. Now in this directory run this command
   ```bash
   STEAM_COMPAT_DATA_PATH=~/.steam/steam/steamapps/compatdata/412830/ ~/.steam/steam/steamapps/common/Proton\ 3.16/proton run winecfg
   ```

   You will probably get a warning which is just a log message.
6. Now ``winecfg`` opens, now all you have to do is go to Libraries section

   ![winecfg](https://cdn.discordapp.com/attachments/750250354771361805/858626706290114570/unknown.png)

   And then add the ``dinput8`` library by choosing ``dinput8`` in the space provided by 'New Override by Library` and Click Add and then okay.
   It should look like this

   ![dinput8](https://cdn.discordapp.com/attachments/750250354771361805/858627350525771776/unknown.png)

7. Congrats, now the patch should have been applied. Launch the game from steam!
