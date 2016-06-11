# Tengine
#增加组
groupadd html
#增加用户
useradd -g html -s /sbin/nologin -d /var/www wangyan
#安装开发组件
yum groupinstall "Development Tools"
#安装Tengine依赖组件
yum install pcre-devel openssl-devel libxml2-devel libxslt-devel gd-devel lua-devel geoip-devel

#安装Tengine 编译参数
./configure --prefix=/usr/local/nginx --user=wangyan --group=html --enable-mods-shared=all
