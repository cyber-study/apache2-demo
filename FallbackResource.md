
# HistoryFallbackConfig

> /etc/apache2/sites-enabled/gpms-defalut.conf

```xml

<VirtualHost *:80>
  DocumentRoot "/var/www/gpms"
  ServerName gpms.tk20230607.xyz

  ProxyRequests Off
  ProxyPreserveHost On

  <Directory "/var/www/gpms/">
    FallbackResource ./index.html
  </Directory>

  <Proxy "*">
    Order deny,allow
    Allow from all
  </Proxy>
  ProxyPass /server/ http://localhost:6500/server/
  ProxyPassReverse /server/ http://localhost:6500/server/

</VirtualHost>

```