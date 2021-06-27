---
sidebar_position: 1
---

# How I setup gaming on Void

## Initial setup
So I have an NVIDIA optimus laptop, which has both an intel gpu and a nvidia gpu 

First I installed the drivers for nvidia, by installing the ``nvidia`` package from non free repo.

I was able to find it by installing the package for non free repo ``void-repo-nonfree``. 

I also installed ``void-repo-multilib`` and ``void-repo-multilib-nonfree`` because why not?

Then while the ``nvidia`` package was installing, I noticed that linux-headers for kernel 5.12 was being installed, while my kernel was 5.10, even though I had updated, so I stopped installing and rebooted to get the current kernel, and then installed nvidia

Then I checked if nvidia is running by doing 

```bash title="nvidia-smi"
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 460.84       Driver Version: 460.84       CUDA Version: 11.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  GeForce GTX 1650    Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   49C    P8     2W /  N/A |      6MiB /  3911MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|    0   N/A  N/A       871      G   /usr/libexec/Xorg                   4MiB |
+-----------------------------------------------------------------------------+
```

Perfect! Now comes the hard part.

## Installing Steam and its dependencies

Well I first installed the ``steam`` package, and when I tried running it, it would say that some 32 bit libraries are fucking missing. I looked it up on youtube and found a guy who had installed steam, and just followed what he did. Installed these packages!

1. ``glibc-32bit`` (Steam mentioned it as libc though both are the same thing, a quick google search could tell you that)
2. ``libdrm-32bit``
3. ``libglapi-32bit``
4. ``libva-glx-32bit``
5. ``nvidia-gtklibs-32bit``
6. ``nvidia-libs-32bit``

The last 2 are downloaded because ``nvidia`` contains 64 bit versions of them, and steam requires 32 bit versions

Steam had finally installed, but it wouldnt launch properly, and I'd still get the ``Badlength X error`` sometimes, I then googled a bit and found that someone solved it by running ``steam`` through ``prime-run``, thats when it clicked for me.

Nvidia was running but it wasn't being used for launching the applications, intel had first priority. But I hadn't installed Intel drivers yet! It made sense why Steam wouldnt launch then.

## Installing Intel graphics drivers

I went to the directory ``/usr/share/doc/steam`` and opened the file ``README.voidlinux`` which contained some information. From there I realized that I had to install ``mesa-dri-32bit`` to run steam, and thats what I did!! After that ``steam`` would run without ``prime-run`` !! Fucking wow

## Result

Fucking WOW!

![My Steam Library](https://cdn.discordapp.com/attachments/750250354771361805/858433416697741342/unknown.png)

## References
1. [Nvidia](https://docs.voidlinux.org/config/graphical-session/graphics-drivers/nvidia.html)
2. [Repositories](https://docs.voidlinux.org/xbps/repositories/index.html#repositories)
3. [Installing Steam on Void Linux](https://youtu.be/IYosS84xSfM)