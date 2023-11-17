# 配置端口反向代理

## install apache2

```bash
apt update
apt install apache2
```

## 反向代理需要使用apache2的模块来启动

```bash
a2enmod proxy proxy_balancer proxy_http
```

## edit apache2 config file

```bash
cd /etc/apache2/sites-available
vim admin-tk20230607.xyz.conf
```

## config content

> 假设我的服务运行在3000端口的话需要以下的配置

```xml admin-tk20230607.xyz.conf
<VirtualHost *:80>
  ServerName admin.tk20230607.xyz

  ProxyRequests Off
  ProxyPreserveHost On

  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>
  ProxyPass / http://localhost:3000/
  ProxyPassReverse / http://localhost:3000/
</VirtualHost>
```

## 加载模块后重启apache2服务

```bash
a2enmod admin-tk20230607.xyz.conf
systemctl restart apache2 && systemctl status apache2
```