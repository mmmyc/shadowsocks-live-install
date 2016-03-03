谢嵩岭
411522199805162415
18338635025

cn4t.hxg.cc

**Debian**
```sh
cd /tmp
# 下载源码
git clone https://github.com/shadowsocks/shadowsocks-libev.git
# 开始编译
cd shadowsocks-libev
./autogen.sh
./configure --prefix=/usr && make
make install
# 准备必须的文件
mkdir -p /etc/shadowsocks-libev
cp ./debian/shadowsocks-libev.init /etc/init.d/shadowsocks-libev
cp ./debian/shadowsocks-libev.default /etc/default/shadowsocks-libev
cp ./debian/config.json /etc/shadowsocks-libev/config.json
chmod +x /etc/init.d/shadowsocks-libev
# 编辑配置文件
vim /etc/shadowsocks-libev/config.json
# 启动服务
service shadowsocks-libev start
```

**CentOS**
```sh
cd /tmp
# 编译环境准备&安装依赖包
yum install -y gcc automake autoconf libtool make build-essential autoconf libtool
yum install -y curl curl-devel unzip zlib-devel openssl-devel perl perl-devel cpio expat-devel gettext-devel
# 下载源码
wget https://github.com/shadowsocks/shadowsocks-libev/archive/master.zip
unzip master.zip
# 开始编译
cd shadowsocks-libev*
./autogen.sh
./configure --prefix=/usr && make
make install
# 准备必须的文件
mkdir -p /etc/shadowsocks-libev
cp ./rpm/SOURCES/etc/init.d/shadowsocks-libev /etc/init.d/shadowsocks-libev
cp ./debian/config.json /etc/shadowsocks-libev/config.json
chmod +x /etc/init.d/shadowsocks-libev
# 编辑配置文件
vim /etc/shadowsocks-libev/config.json
# 启动服务
service shadowsocks-libev start
```