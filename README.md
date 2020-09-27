# st - simple terminal

st is a simple terminal emulator for X which sucks less.


## Requirements

In order to build `st` you need the `Xlib` header files.


## Installation

Edit `config.mk` to match your local setup (st is installed into
the `/usr/local` namespace by default).

Afterwards enter the following command to build and install `st` (if
necessary as `root`):

```
$ make clean install
```

## Updating `config.h`  After Install

Edit `config.def.h` to update miscellaneous configuration options.
For example:

```diff
unsigned int tabspaces = 8;

/* bg opacity */
- float alpha = 0.99;
+ float alpha = 0.55;

```

Once your changes have been saved/committed, you can run the following to
update your `st` installation.

```
$ rm config.h; make clean; make -j8 ; sudo make -j8 install
rm -f st st.o x.o boxdraw.o hb.o st-0.8.3.tar.gz
cp config.def.h config.h
st build options:
c99 -I/usr/include/X11  `pkg-config --cflags fontconfig`  `pkg-config --cflags freetype2`  `pkg-config --cflags harfbuzz` -DVERSION=\"0.8.3\" -D_XOPEN_SOURCE=600  -O -c st.c
c99 -I/usr/include/X11  `pkg-config --cflags fontconfig`  `pkg-config --cflags freetype2`  `pkg-config --cflags harfbuzz` -DVERSION=\"0.8.3\" -D_XOPEN_SOURCE=600  -O -c x.c
c99 -I/usr/include/X11  `pkg-config --cflags fontconfig`  `pkg-config --cflags freetype2`  `pkg-config --cflags harfbuzz` -DVERSION=\"0.8.3\" -D_XOPEN_SOURCE=600  -O -c boxdraw.c
c99 -I/usr/include/X11  `pkg-config --cflags fontconfig`  `pkg-config --cflags freetype2`  `pkg-config --cflags harfbuzz` -DVERSION=\"0.8.3\" -D_XOPEN_SOURCE=600  -O -c hb.c
CFLAGS  = -I/usr/include/X11  -I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16  -I/usr/include/freetype2 -I/usr/include/libpng16  -I/usr/include/harfbuzz -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -DVERSION="0.8.3" -D_XOPEN_SOURCE=600  -O
LDFLAGS = -L/usr/lib/X11 -lm -lrt -lX11 -lutil -lXft -lXrender -lfontconfig -lfreetype  -lfreetype  -lharfbuzz
CC      = c99
c99 -o st st.o x.o boxdraw.o hb.o -L/usr/lib/X11 -lm -lrt -lX11 -lutil -lXft -lXrender `pkg-config --libs fontconfig`  `pkg-config --libs freetype2`  `pkg-config --libs harfbuzz`
mkdir -p /usr/local/bin
cp -f st /usr/local/bin
chmod 755 /usr/local/bin/st
mkdir -p /usr/local/share/man/man1
sed "s/VERSION/0.8.3/g" < st.1 > /usr/local/share/man/man1/st.1
chmod 644 /usr/local/share/man/man1/st.1
tic -sx st.info
7 entries written to /etc/terminfo
Please see the README file regarding the terminfo entry of st.
mkdir -p /usr/local/share/applications
cp -f st.desktop /usr/local/share/applications
update-desktop-database /usr/local/share/applications

```


## Running st

If you did not install st with make clean install, you must compile
the st terminfo entry with the following command:

```
$ tic -sx st.info
```

See the man page for additional details.

## Credits

Based on Aurélien APTEL <aurelien dot aptel at gmail dot com> bt source code.


