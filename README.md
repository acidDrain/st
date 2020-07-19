# My Personal Fork of `st`, the suckless-terminal

 - [`st` - simple terminal](#st---simple-terminal)
 - [Differences](#differences)
 - [Requirements](#requirements)
 - [Installation](#installation)
 - [Running st](#running-st)
 - [Credits](#credits)

## `st` - simple terminal

`st` is a simple terminal emulator for `X` which sucks less.

`st` is one of the few terminal emulators for [Linux that supports ligatures](https://github.com/tonsky/FiraCode#terminal-compatibility-list).
My favorite font to work in, [Fira Code](https://github.com/tonsky/FiraCode), requires ligatures. I personally find that it makes code easier to follow and generally more legible.

There are other choices out there, but I prefer to have a performant terminal versus something that may consume more resources like something based on Electron, etc.

## Differences

This repository includes patches that:

- [add ligature support](https://st.suckless.org/patches/ligatures/)
- [boxdraw support](https://st.suckless.org/patches/ligatures/0.8.3/st-ligatures-boxdraw-20200430-0.8.3.diff) (fixes rendering of lines and drawing glyphs)
- "[font2](https://st.suckless.org/patches/font2/)" var support to enable backup/spare font configuration addresses issues where specific glyphs can't be present in default font settings and must be included separately
- [desktop entries specification](https://developer.gnome.org/integration-guide/stable/desktop-files.html.en) that gets copied to the appropriate path, enabling Gnome and KDE to display a desktop-style launcher for st
- configures `st` to use the _Fira Code_ font
- [gruvbox color scheme](https://camo.githubusercontent.com/cdb2f2e986c564b515c0c698e6c45b4ab5d725a9/687474703a2f2f692e696d6775722e636f6d2f776136363678672e706e67) via [patch st-gruvbox-dark-0.8.2.diff](https://st.suckless.org/patches/gruvbox/st-gruvbox-dark-0.8.2.diff)

There are other choices out there, but I prefer to have a performant terminal versus something that may consume more resources like something based on electron, etc.

## Requirements

In order to build `st` you need the `Xlib` header files.

## Installation

Edit `config.mk` to match your local setup (`st` is installed into
the `/usr/local` namespace by default).

Afterwards enter the following command to build and install `st` (if
necessary as `root`):

```sh
$ make clean install
```

## Running st

If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

```sh
tic -sx st.info
```

See the `man` page for additional details.

## Credits

Based on Aurélien APTEL <aurelien dot aptel at gmail dot com> bt source code.


