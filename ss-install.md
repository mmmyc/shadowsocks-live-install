**Debian**
```sh
cd /tmp
# 下载源码
git clone https://github.com/madeye/shadowsocks-libev.git
# 开始编译
cd shadowsocks-libev
./configure --prefix=/usr && make
make install
# 准备必须的文件
mkdir -p /etc/shadowsocks
cp ./debian/shadowsocks.init /etc/init.d/shadowsocks
cp ./debian/shadowsocks.default /etc/default/shadowsocks
cp ./debian/config.json /etc/shadowsocks/config.json
chmod +x /etc/init.d/shadowsocks
# 编辑配置文件
vim /etc/shadowsocks/config.json
# 启动服务
service shadowsocks start
```

**CentOS**
```sh
cd /tmp
# 编译环境准备&安装依赖包
yum install -y gcc automake autoconf libtool make build-essential autoconf libtool
yum install -y curl curl-devel unzip zlib-devel openssl-devel perl perl-devel cpio expat-devel gettext-devel
# 下载源码
wget https://github.com/madeye/shadowsocks-libev/archive/master.zip
unzip master.zip
# 开始编译
cd shadowsocks-libev*
./configure && make
make install
# 准备必须的文件
mkdir -p /etc/shadowsocks
cp ./rpm/SOURCES/etc/init.d/shadowsocks /etc/init.d/shadowsocks
cp ./debian/config.json /etc/shadowsocks/config.json
chmod +x /etc/init.d/shadowsocks
# 编辑配置文件
vim /etc/shadowsocks/config.json
# 启动服务
service shadowsocks start
```