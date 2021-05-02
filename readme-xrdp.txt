# built on ubuntu 20.04 focal

apt-get install git autoconf libtool pkg-config gcc g++ make  libssl-dev libpam0g-dev libjpeg-dev libx11-dev libxfixes-dev libxrandr-dev  flex bison libxml2-dev intltool xsltproc xutils-dev python-libxml2 g++ xutils libfuse-dev libmp3lame-dev nasm libpixman-1-dev xserver-xorg-dev
git clone https://github.com/neutrinolabs/xrdp
cd xrdp/
git checkout v0.9.16
git submodule update --init --recursive
./bootstrap
./configure --enable-fuse --enable-mp3lame --enable-pixman --prefix=/opt/xrdp
make
make install

tar czf /tmp/opt-xrdp-0.9.16-focal-armv7l.tar.gz /opt/xrdp /etc/init.d/xrdp /etc/pam.d/xrdp-sesman /etc/xrdp
tar czf /tmp/opt-xrdp-0.9.16-focal-aarch64.tar.gz /opt/xrdp /etc/init.d/xrdp /etc/pam.d/xrdp-sesman /etc/xrdp
tar czf /tmp/opt-xrdp-0.9.16-focal-x86_64.tar.gz /opt/xrdp /etc/init.d/xrdp /etc/pam.d/xrdp-sesman /etc/xrdp
