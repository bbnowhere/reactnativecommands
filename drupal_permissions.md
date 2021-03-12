	
find /var/www/html/name -type d -exec chmod ug=rx,o= '{}' \;
find /var/www/html/name -type f -exec chmod ug=r,o= '{}' \;
find /var/www/html/name/sites/default/files -type d -exec chmod ug=rwx,o= '{}' \;
find /var/www/html/name/sites/default/files -type f -exec chmod ug=rw,o= '{}' \;

