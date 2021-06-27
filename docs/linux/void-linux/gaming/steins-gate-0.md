---
sidebar_position: 3
---

# How to install Steam improvement patch for Steins;Gate 0

## Introduction

I got the patch from here
https://github.com/CommitteeOfZero/zero-patch/releases

## Steps to install patch

1. After downloading the patch, I went and saw the instructions to install this in the game. I saw that i already had ``winetricks`` installed.

2. I unzipped the patch in my home directory.

3. Then I went to the place I unzipped, and opened a terminal there and ran this command.

   ```bash
   WINEPREFIX=~/.local/share/Steam/steamapps/compatdata/825630/pfx winetricks vcrun2017
   ```

   I faced some issues, realized I was missing ``wine-32bit`` package so installed it.

   And then I tried again and faced some issue. Looking up on protondb I realised had to install ``vcrun2017`` in the steam prefix of the game.

4. So I navigated to this directory.

   ```bash
   /home/pixelfog/.steam/steam/steamapps/compatdata/825630/pfx
   ```

5. And tried installing ``vcrun2017`` (I already had protontricks)
   
   ```bash
   protontricks 825630 vcrun2017
   ```

6. But ``protontricks`` wouldnt work and always show some error. Some googling later I realised that its because the package on void was outdated.
   I then removed it and reinstalled ``protontricks`` with ``pipx``   

6. But it didn't work and would always show me an error. Somehow I realized that it was because of the proton version Steins;Gate 0 was running with. 
   I changed it to ``5.0-10`` and then it fucking worked!
   Although it showed as ``5.0`` in ``~/.steam/steam/steamapps/common/``

7. I tried rerunning the command in the SG0package i had unzipped in home directory

   ```bash
   WINEPREFIX=~/.local/share/Steam/steamapps/compatdata/825630/pfx winetricks vcrun2017
   ```
8. Then I ran this command

   ```bash
   STEAM_COMPAT_DATA_PATH=~/.local/share/Steam/steamapps/compatdata/825630 ~/.local/share/Steam/steamapps/common/Proton\ 5.0/proton run SG0Patch-Installer.exe
   ```
9. After this a launcher came and I just followed the steps and got the game installed!!

## References

1. http://sonome.dareno.me/projects/sg0-linux.html
2. https://www.protondb.com/app/825630#iCD1udMluw
