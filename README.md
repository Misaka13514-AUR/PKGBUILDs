# [PKGBUILDs](https://wiki.archlinux.org/index.php/PKGBUILD) for [Arch User Repository](https://aur.archlinux.org)

This repository contains the packages I maintain in [AUR](https://aur.archlinux.org/packages/?K=Misaka13514&SeB=M), checked into git as subtrees for easier management and pull requests.

Powered by [nvchecker](https://github.com/lilydjwg/nvchecker) & [aurpublish](https://github.com/eli-schwartz/aurpublish).

[![Maintainer](https://img.shields.io/static/v1?label=maintainer&message=Misaka13514&color=333333)](https://aur.archlinux.org/account/Misaka13514)

## Pre-built AUR packages (experimental)

Pre-built versions of the AUR packages are also available.

Add the following lines to `/etc/pacman.conf`:

```ini
[atri]
Server = https://repo.atri.tk/$arch
```

Add and trust my GPG key in pacman keyring:

```sh
sudo pacman-key --recv-keys 293B93D8A471059F85D716A65BA92099D9BE2DAA
sudo pacman-key --lsign-key 293B93D8A471059F85D716A65BA92099D9BE2DAA
```
