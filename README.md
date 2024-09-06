# UPT Please

UPT Please is a fork of [Upt][], which provides a unified command interface to manage packages for any operating system.

Just like Upt, UPT Please relies on the platform’s package management tool to perform the task, it’s more like a wrapper or adaptive alias.

## Install

**Use Cargo**

UPT Please is written in the Rust so you can install it using [Cargo][]:

```sh
cargo install upt-please
```

## Features

### Unified command interface

Each operating system has its own package management tool, which requires different commands to complete the same operation. This can be inconvenient when switching between or trying new OSs.

```sh
apt install $pkg          # Ubuntu, Debian, Linux Mint...
apk add $pkg              # Alpine
yay -S $pkg               # Arch, Manjaro...
nix-env -i $pkg           # Nixos
xbps-install $pkg         # Voidlinux
emerge $pkg               # Gentoo
```

With `please`, You just need to remember one command:

```sh
please install $pkg          # Works on any OS
```

UPT Please identifies the OS type and runs the appropriate package management tool to install `$pkg`.

At the moment I’m editing this document, the only addition over Upt is [Yay][] support for Arch Linux and variants.

### OS Tools

```
+------------------------------------------------------+----------------------+
| OS                                                   | Tools                |
+------------------------------------------------------+----------------------+
| windows                                              | scoop, choco, winget |
+------------------------------------------------------+----------------------+
| macos                                                | brew, port           |
+------------------------------------------------------+----------------------+
| ubuntu, debian, linuxmint, pop, deepin, elementary   | apt                  |
| kali, raspbian, aosc, zorin, antix, devuan, bodhi    |                      |
| lxle, sparky                                         |                      |
+------------------------------------------------------+----------------------+
| fedora, redhat, rhel, amzn, ol, almalinux, rocky     | dnf, yum             |
| oubes, centos, qubes, eurolinux                      |                      |
+------------------------------------------------------+----------------------+
| arch, manjaro, endeavouros, arcolinux, garuda        | pacman, yay          |
| antergos, kaos                                       |                      |
+------------------------------------------------------+----------------------+
| alpine, postmarket                                   | apk                  |
+------------------------------------------------------+----------------------+
| opensuse, opensuse-leap, opensuse-tumbleweed         | zypper               |
+------------------------------------------------------+----------------------+
| nixos                                                | nix-env              |
+------------------------------------------------------+----------------------+
| gentoo, funtoo                                       | emerge               |
+------------------------------------------------------+----------------------+
| void                                                 | xbps                 |
+------------------------------------------------------+----------------------+
| mageia                                               | urpm                 |
+------------------------------------------------------+----------------------+
| slackware                                            | slackpkg             |
+------------------------------------------------------+----------------------+
| solus                                                | eopkg                |
+------------------------------------------------------+----------------------+
| openwrt                                              | opkg                 |
+------------------------------------------------------+----------------------+
| nutyx                                                | cards                |
+------------------------------------------------------+----------------------+
| crux                                                 | prt-get              |
+------------------------------------------------------+----------------------+
| freebsd, ghostbsd                                    | pkg                  |
+------------------------------------------------------+----------------------+
| android                                              | pkg(termux)          |
+------------------------------------------------------+----------------------+
| haiku                                                | pkgman               |
+------------------------------------------------------+----------------------+
| windows/msys2                                        | pacman               |
+------------------------------------------------------+----------------------+
| *                                                    | apt, dnf, pacman     |
+------------------------------------------------------+----------------------+
```

UPT Please will determine which package management tool to use based on the above table.

Some platforms may support multiple package management tools, upt selects one of them in order.

You can specify the package manager that UPT should use by setting the `UPT_TOOL` environment variable.

```sh
UPT_TOOL=brew upt install $pkg            # equal to `brew install $pkg`
UPT_TOOL=nix-env upt install $pkg         # equal to `nix-env -i $pkg`
```

## License

Copyright (c) 2024 Rodrigo Cacilhas <montegasppa@cacilhas.info>

UPT Please is made available under the terms of the MIT License in respect to [Upt license][].

See the [LICENSE-MIT][] files for license details.

Original credits to [sigoden][].

[Cargo]: https://doc.rust-lang.org/stable/cargo/
[LICENSE-MIT]: https://github.com/cacilhas/upt-please/blob/master/LICENSE-MIT
[sigoden]: https://crates.io/users/sigoden
[Upt]: https://crates.io/crates/upt
[Upt license]: https://github.com/sigoden/upt?tab=readme-ov-file#license
[Yay]: https://github.com/Jguer/yay
