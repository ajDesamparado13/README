# How to Setup a Webserver

## Setting UP Apache,Nginx, PHP-FPM with user-group permission

1. Create user group

   `sudo groupadd laravel`

2. Add ssh-user to group

   `sudo gpasswd -a ssh-user laravel`

3. Add web server user to group

   - for nginx

     `sudo gpasswd -a nginx laravel`

   - for apache either of the following command

     `sudo gpasswd -a apache laravel`

     `sudo gpasswd -a httpd laravel`

4. Navigate to your Application directory

   `sudo cd /path/to/your/beautiful/laravel-application`

5. This is an optional steps for resetting file and directory permissions to default

   `sudo find ./ -type d -exec chmod 755 {} \;`

   `sudo find ./ -type f -exec chmod 644 {} \;`

6. Give users part of the group the standard RW and RWX

   `sudo chown -R :laravel ./storage`

   `sudo chown -R :laravel ./bootstrap/cache`

   `sudo find ./storage -type d -exec chmod 775 {} \;`

   `sudo find ./bootstrap/cache -type d -exec chmod 775 {} \;`

   `sudo find ./storage -type f -exec chmod 664 {} \;`

   `sudo find ./bootstrap/cache -type f -exec chmod 664 {} \;`

7. Give the newly created files/directories the group of the parent directory

   `sudo find ./bootstrap/cache -type d -exec chmod g+s {} \;`

   `sudo find ./storage -type d -exec chmod g+s {} \;`

8. Let newly created files/directories inherit the default owner
   This set permissions up to maximum permission of rwx e.g. new files get 664 and olders get 775

   `sudo setfacl -R -d -m g::rwx ./storage`

   `sudo setfacl -R -d -m g::rwx ./bootstrap/cache`

9. Update the web server config to use the appropriate user and group
   - For Apache: update config commonly at `/etc/httpd`
   - For Nginx: update nginx config commonly at `/etc/nginx`
   - For PHP-FPM: update pool config commonly at `/etc/php/fpm/pool.d`
10. Test your application
