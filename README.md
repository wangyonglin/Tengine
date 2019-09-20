# Tengine
#增加组
  groupadd nginx
#增加用户
  useradd -r -g nginx -M nginx -s /sbin/nologin -d /var/www
#安装开发组件
  yum groupinstall "Development Tools"
#安装Tengine依赖组件
  yum install pcre-devel openssl-devel libxml2-devel libxslt-devel gd-devel lua-devel geoip-devel

#安装Tengine 编译参数
./configure --prefix=/usr/local/nginx --user=nginx --group=nginx --enable-mods-shared=all
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

server {
    listen       80;
    server_name mage.dev;
    root /var/www/www.eeob.com/pub;
   
    location / {
        index index.php; #跳转到www.example.com/index.php
        autoindex on;
    }   

    #当请求网站下php文件的时候，反向代理到php-fpm
    location ~ \.php$ {
        include /usr/local/nginx/conf/fastcgi.conf; #加载nginx的fastcgi模块
        fastcgi_intercept_errors on;
        fastcgi_pass   127.0.0.1:9000; #nginx fastcgi进程监听的IP地址和端口
    }
}
