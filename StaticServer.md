# 配置静态资源服务

## install apache2

```bash
apt update
apt install apache2
```

## edit apache2 config file

```bash
cd /etc/apache2/sites-available
vim statics-tk20230607.xyz.conf
```

## config content

> 假设我的资源文件夹在/home/ubuntu/statics下的话需要进行下面的配置

```xml statics-tk20230607.xyz.conf
<VirtualHost *:80>
  DocumentRoot "/home/ubuntu/statics-demo"
  ServerName statics.tk20230607.xyz
</VirtualHost>
```

## 重启apache2服务

```bash
a2enmod statics-tk20230607.xyz.conf
systemctl restart apache2 && systemctl status apache2
```

# 修改文件夹权限

如果映射的目录是 /var/www 的话无需修改权限
如果修改的是其他目录的话需要修改权限,否则访问会出现 Forbidden 的错误

[https://fiko.me/apache-2-you-dont-have-permission-to-access-this-resource](https://fiko.me/apache-2-you-dont-have-permission-to-access-this-resource)

Forbidden

You don't have permission to access this resource.

```bash
sudo chmod -R +x /home
sudo chmod -R +x /home/ubuntu/
sudo chmod -R +x /home/ubuntu/statics-demo
```