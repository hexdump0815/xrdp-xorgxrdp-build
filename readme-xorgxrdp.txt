apt-get install xserver-xorg-dev nasm xrdp libgbm-dev autoconf automake libtool pkgconfig
git clone https://github.com/neutrinolabs/xorgxrdp.git
cd xorgxrdp
git checkout v0.2.13
patch -p1 < /compile/doc/xorgxrdp/fix-required-xrd-version.patch
patch -p1 < /compile/doc/xorgxrdp/fix-mouse-buttons.patch
./bootstrap 
./configure --enable-glamor
make

result:
./module/.libs/libxorgxrdp.so
./xrdpkeyb/.libs/xrdpkeyb_drv.so
./xrdpdev/.libs/xrdpdev_drv.so
./xrdpmouse/.libs/xrdpmouse_drv.so

tar czf /tmp/xorgxrdp-armv7l.tar.gz /usr/lib/xorg/modules/*/*xrdp* /usr/lib/xorg/modules/libxorgxrdp* /etc/X11/xrdp/xorg.conf
tar czf /tmp/xorgxrdp-aarch64.tar.gz /usr/lib/xorg/modules/*/*xrdp* /usr/lib/xorg/modules/libxorgxrdp* /etc/X11/xrdp/xorg.conf
