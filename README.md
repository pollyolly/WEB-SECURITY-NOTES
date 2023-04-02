# WEB-SECURITY

### SECURITY HEADERS
```
#APACHE
<VirtualHost *:443>
        <Directory /var/www/html/flipbook/>
                FileETag None
                Header unset ETag
                Header unset Pragma
                Header unset Cache-Control
                Header unset Last-Modified
                Header set Pragma "no-cache"
                Header set Cache-Control "max-age=0, no-cache, no-store, must-revalidate"
                Header set Expires "Thu, 1 Jan 1970 00:00:00 GMT" 
                Header always set Content-Security-Policy "\
default-src 'self' https://dev.filpbookilc.com;\
frame-src dev.flipbookilc.com;\
font-src 'self';\
img-src 'self' data:;\
connect-src www.google-analytics.com www.googletagmanager.com dev.flipbookilc.com;\
script-src 'self' 'unsafe-inline' www.googletagmanager.com www.google-analytics.com;\
style-src 'self' 'unsafe-inline';"
                 Header always set X-Content-Type-Options nosniff
        </Directory>
</VirtualHost>
```
