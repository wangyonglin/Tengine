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
#默认配置目录
Configuration summary
  + using system PCRE library
  + using system OpenSSL library
  + md5: using OpenSSL library
  + sha1: using OpenSSL library
  + using system zlib library
  + jemalloc library is disabled

  nginx path prefix: "/usr/local/nginx"
  nginx binary file: "/usr/local/nginx/sbin/nginx"
  nginx configuration prefix: "/usr/local/nginx/conf"
  nginx configuration file: "/usr/local/nginx/conf/nginx.conf"
  nginx pid file: "/usr/local/nginx/logs/nginx.pid"
  nginx error log file: "/usr/local/nginx/logs/error.log"
  nginx http access log file: "/usr/local/nginx/logs/access.log"
  nginx http client request body temporary files: "client_body_temp"
  nginx dso module path: "/usr/local/nginx/modules/"
  nginx http proxy temporary files: "proxy_temp"

