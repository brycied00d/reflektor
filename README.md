reflektor is a cache of caches. It contacts a set of given caches until it finds one that contains the requested info_hash, and then caches the request locally before serving it.

Set up your own
--

reflektor requires:

-   PHP 5.4
-   nginx
-   linux


Configuration
--

<VirtualHost *:80>
        DocumentRoot "/var/www/reflektor/public/"   
        ServerName reflektor.karmorra.info
        RewriteEngine On
        RewriteRule ^/torrent/([A-Fa-f0-9]{40})\.[Tt][Oo][Rr]{2}[Ee][Nn][Tt]$ /serve.php?ih=$1 [L]
        RewriteRule ^/torrent/?$ / [L]
        DirectoryIndex index.html
        <Directory /var/www/reflektor/public/>
                AllowOverride None
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>
    
Dotdeb.org sources are recommended for an easy and painless setup.

Make sure permissions are correct, and that both PHP and nginx are allowed to read and write in the cache folder.
