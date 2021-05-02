# built on ubuntu 20.04 focal

apt-get install xserver-xorg-dev nasm xrdp libgbm-dev autoconf automake libtool pkg-config libepoxy-dev
# also required: xrdp needs to be built and installed first
export PKG_CONFIG_PATH=/opt/xrdp/lib/pkgconfig
git clone https://github.com/neutrinolabs/xorgxrdp.git
cd xorgxrdp
git checkout v0.2.16
patch -p1 < /compile/doc/xrdp-xorgxrdp-build/fix-mouse-buttons.patch
./bootstrap 
./configure --enable-glamor
make

result:
./module/.libs/libxorgxrdp.so
./xrdpkeyb/.libs/xrdpkeyb_drv.so
./xrdpdev/.libs/xrdpdev_drv.so
./xrdpmouse/.libs/xrdpmouse_drv.so

tar czf /tmp/xorgxrdp-0.2.16-focal-armv7l.tar.gz /usr/lib/xorg/modules/*/*xrdp* /usr/lib/xorg/modules/libxorgxrdp* /etc/X11/xrdp/xorg.conf
tar czf /tmp/xorgxrdp-0.2.16-focal-aarch64.tar.gz /usr/lib/xorg/modules/*/*xrdp* /usr/lib/xorg/modules/libxorgxrdp* /etc/X11/xrdp/xorg.conf
tar czf /tmp/xorgxrdp-0.2.16-focal-x86_64.tar.gz /usr/lib/xorg/modules/*/*xrdp* /usr/lib/xorg/modules/libxorgxrdp* /etc/X11/xrdp/xorg.conf
