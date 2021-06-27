# How I setup nix package manager on void

## Introduction
Nix package manager is awesome, and it has the most number of packages! And it's also cross platform, so it'd work on any linux distribution. I had tried building aseprite but it was such a PITA, and then I found about Nix!

## Steps to download

First install the ``nix`` package.

Enable the ``nix-daemon`` service

```bash
sudo ln -s /etc/sv/nix-daemon /var/service/
```

Start the service
```bash
sudo sv up nix-daemon
```

You can now either re-login your user or re-read /etc/profile
```bash
source /etc/profile
```

After this the nix package manager is fully functional and can be used by any user.

You can then subscribe to the Nix packages channel to query or install any available package:
```bash
nix-channel --add http://nixos.org/channels/nixpkgs-unstable
nix-channel --update
```
## Using Nix

See what installable packages are currently available in the channel: 

```bash title="nix-env -qa"
docbook-xml-4.3
docbook-xml-4.5
firefox-33.0.2
hello-2.9
libxslt-1.1.28
...
```

Install some packages from the channel:

```bash
nix-env -i hello
```

This should download pre-built packages; it should not build them locally (if it does, something went wrong).

Test that they work: 

```bash title="which hello"
/home/eelco/.nix-profile/bin/hello
```

```bash title="hello"
Hello, world!
```

Uninstall a package: 

```bash 
nix-env -e hello
```

You can also test a package without installing it: 

```bash
nix-shell -p hello
```

This builds or downloads GNU Hello and its dependencies, then drops you into a Bash shell where the hello command is present, all without affecting your normal environment: 

```bash
[nix-shell:~]$ hello
Hello, world!

[nix-shell:~]$ exit

$ hello
hello: command not found
```

To keep up-to-date with the channel, do: 

```bash
nix-channel --update nixpkgs
nix-env -u '*'
```
The latter command will upgrade each installed package for which there is a “newer” version 

If you're unhappy with the result of a nix-env action 

```bash 
nix-env --rollback
```

You should periodically run the Nix garbage collector to get rid of unused packages, since uninstalls or upgrades don't actually delete them: 

```bash
nix-collect-garbage -d
```

## References

1. https://voidlinux.org/news/2014/01/Using-the-Nix-package-manager.html
2. https://nixos.org/manual/nix/stable/#chap-quick-start
