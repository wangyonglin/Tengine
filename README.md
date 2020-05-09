# Tengine
# 增加组
`  groupadd nginx`
# 增加用户
`  useradd -r -g nginx -M nginx -s /sbin/nologin -d /var/www`
# 安装开发组件
`  yum groupinstall "Development Tools"`
# 安装Tengine依赖组件
`  yum install -y vim lrzsz tree screen psmisc lsof tcpdump wget  ntpdate  gcc gcc-c++ glibc glibc-devel pcre pcre-devel openssl  openssl-devel systemd-devel net-tools iotop bc  zip unzip zlib-devel bash-completion nfs-utils automake libxml2  libxml2-devel libxslt libxslt-devel perl perl-ExtUtils-Embed`

# 安装Tengine 编译参数
`./configure --prefix=/usr/local/nginx  \
	--user=nginx   --group=nginx`
# Tengine 配置参数

	if ( $http_user_agent ~ "(MIDP)|(WAP)|(UP.Browser)|(Smartphone)|(Obigo)|(Mobile)|(AU.Browser)|(wxd.Mms)|(WxdB.Browser)|(CLDC)|(UP.Link)|(KM.Browser)|(UCWEB)|(SEMC-Browser)|(Mini)|(Symbian)|(Palm)|(Nokia)|(Panasonic)|(MOT-)|(SonyEricsson)|(NEC-)|(Alcatel)|(Ericsson)|(BENQ)|(BenQ)|(Amoisonic)|(Amoi-)|(Capitel)|(PHILIPS)|(SAMSUNG)|(Lenovo)|(Mitsu)|(Motorola)|(SHARP)|(WAPPER)|(LG-)|(LG/)|(EG900)|(CECT)|(Compal)|(kejian)|(Bird)|(BIRD)|(G900/V1.0)|(Arima)|(CTL)|(TDG)|(Daxian)|(DAXIAN)|(DBTEL)|(Eastcom)|(EASTCOM)|(PANTECH)|(Dopod)|(Haier)|(HAIER)|(KONKA)|(KEJIAN)|(LENOVO)|(Soutec)|(SOUTEC)|(SAGEM)|(SEC-)|(SED-)|(EMOL-)|(INNO55)|(ZTE)|(iPhone)|(Android)|(Windows CE)|(Wget)|(Java)|(curl)|(Opera)" ) {
				rewrite  ^/(.*)$	http://m.wangyonglin.com$1 permanent;
			}
			
		if ($http_host !=	www.wangyonglin.com) {
				rewrite ^/(.*)$		http://www.wangyonglin.com/$1 permanent;
		}

#配置nginx开机启动，切换到/lib/systemd/system目录,创建nginx.service文件：
	[Unit]
	Description=nginx
	After=network.target
	[Service]
	Type=forking
	ExecStart=/usr/local/nginx/sbin/nginx
	ExecReload=/usr/local/nginx/sbin/nginx reload
	ExecStop=/usr/local/nginx/sbin/nginx quit
	PrivateTmp=true
	[Install]
	WantedBy=multi-user.target
# composer 下载失败解决办法
1、更换成阿里镜像：
	`composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/`

2、更换成Laravel China镜像：
`	composer config -g repo.packagist composer https://packagist.laravel-china.org`

3、更换成中国全量镜像：
`composer config -g repo.packagist composer https://packagist.phpcomposer.com`
