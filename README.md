# Tengine
# 增加组
  groupadd nginx
# 增加用户
  useradd -r -g nginx -M nginx -s /sbin/nologin -d /var/www
# 安装开发组件
  yum groupinstall "Development Tools"
# 安装Tengine依赖组件
  yum install -y vim lrzsz tree screen psmisc lsof tcpdump wget  ntpdate  gcc gcc-c++ glibc glibc-devel pcre pcre-devel openssl  openssl-devel systemd-devel net-tools iotop bc  zip unzip zlib-devel bash-completion nfs-utils automake libxml2  libxml2-devel libxslt libxslt-devel perl perl-ExtUtils-Embed

# 安装Tengine 编译参数
./configure --prefix=/usr/local/nginx  \
       --user=nginx   --group=nginx 
# composer 下载失败解决办法
1、更换成阿里镜像：
composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

2、更换成Laravel China镜像：
composer config -g repo.packagist composer https://packagist.laravel-china.org

3、更换成中国全量镜像：
composer config -g repo.packagist composer https://packagist.phpcomposer.com
