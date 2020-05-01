apt-get install git autoconf libtool pkg-config gcc g++ make  libssl-dev libpam0g-dev libjpeg-dev libx11-dev libxfixes-dev libxrandr-dev  flex bison libxml2-dev intltool xsltproc xutils-dev python-libxml2 g++ xutils libfuse-dev libmp3lame-dev nasm libpixman-1-dev xserver-xorg-dev
git clone https://github.com/neutrinolabs/xrdp
cd xrdp/
git checkout v0.9.13
git submodule update --init --recursive
./bootstrap
# ./configure --enable-fuse --enable-mp3lame --enable-pixman --prefix=/opt/xrdp-armv7l
# ./configure --enable-fuse --enable-mp3lame --enable-pixman --prefix=/opt/xrdp-aarch64
make
make install

tar czf /tmp/opt-xrdp-armv7l.tar.gz /opt/xrdp-armv7l /etc/xrdp/xrdp* /etc/xrdp/s* /etc/xrdp/reconnectwm.sh /etc/xrdp/pulse /etc/xrdp/km-*
tar czf /tmp/opt-xrdp-aarch64.tar.gz /opt/xrdp-aarch64 /etc/xrdp/xrdp* /etc/xrdp/s* /etc/xrdp/reconnectwm.sh /etc/xrdp/pulse /etc/xrdp/km-*
