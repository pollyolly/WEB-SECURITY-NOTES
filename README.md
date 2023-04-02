# WEB-SECURITY

### SECURITY HEADERS
[Content Security Policy](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP)
```
#APACHE
<VirtualHost *:443>
        <Directory /var/www/html/flipbook/>
                #Remove on page cache
                FileETag None
                Header unset ETag
                Header unset Pragma
                Header unset Cache-Control
                Header unset Last-Modified
                Header set Pragma "no-cache"
                Header set Cache-Control "max-age=0, no-cache, no-store, must-revalidate"
                Header set Expires "Thu, 1 Jan 1970 00:00:00 GMT"
                
                #Whitelisting allowed external URLS and on page style and scripts.
                Header always set Content-Security-Policy "\
default-src 'self' https://dev.filpbookilc.com;\
frame-src dev.flipbookilc.com;\
font-src 'self';\
img-src 'self' data:;\
connect-src www.google-analytics.com www.googletagmanager.com dev.flipbookilc.com;\
script-src 'self' 'unsafe-inline' www.googletagmanager.com www.google-analytics.com;\
style-src 'self' 'unsafe-inline';"

                 #Validate if text/javascript and css/stylesheet are used
                 Header always set X-Content-Type-Options nosniff
        </Directory>
</VirtualHost>
```
### SESSION COOKIES
```
a. Set an SSL (https://) certificate
For example:
<VirtualHost *:443>
        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/apache-selfsigned.crt
        SSLCertificateKeyFile /etc/ssl/private/apache-selfsigned.key
</VirtualHost>

b. Set the following on php.ini
   session.cookie_secure = 1
```
