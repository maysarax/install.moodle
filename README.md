# install.moodle
 
 
 
 
 How to Install Moodle 3.5 on Centos 7 with nginx
Prepare the environment
Step 1 — Installing Nginx on CentOS 7

Since Nginx is not available in default CentOS repositories, we will install EPEL repository by running this command:

yum install epel-release -y

Install nginx

yum install nginx -y

After installation completes, enable nginx start on boot and run it:

systemctl start nginx
systemctl enable nginx
Step 2 — Installing MySQL (MariaDB)

yum install mariadb-server mariadb -y
After finishing the installation, enable and start the service:

systemctl start mariadb
systemctl enable mariadb
  
 CREATE DATABASE moodledb;
 GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,CREATE TEMPORARY TABLES,DROP,INDEX,ALTER ON moodledb.* TO 'moodleadmin'@'localhost' IDENTIFIED BY 'p@zzwd0L2';
  FLUSH PRIVILEGES;
  exit
  
  chmod 775 -R /var/www/html/moodle
chown nginx:nginx -R /var/www/html/moodle

 chmod 777 -R /var/www/html/moodledata
 chown :nginx -R /var/www/html/moodledata


 yum install php-bcmath php-cli php-common php-devel php-fpm php-gd php-gmp php-intl php-json php-mbstring php-mysqlnd 

yum install php-opcache php-pdo php-pgsql php-process  php-soap  php-xml php-pecl-apcu  php-pear php-mysqlnd 
 
yum install  php-pecl-zip 
yum install php-pspell
yum install php-sodium 
yum install  php-xmlrpc
yum install php-zip   php-curl php-mysql 

yum install php-iconv php-openssl php-tokenizer php-ctype  php-simplexml  php-spl  php-pcre  php-dom php-xmlrpc 


yum install php-common php-iconv php-curl php-mbstring php-xmlrpc php-soap php-zip php-gd php-xml php-intl php-json  graphviz aspell ghostscript clamav



 chmod 775 -R /usr/share/nginx/html
 chown nginx:nginx -R /usr/share/nginx/html
 chmod 770 -R /usr/share/nginx/faadata
 chown :nginx -R /usr/share/nginx/faadata
 
  chmod 0777 -R /usr/share/nginx/faadata
server{
   listen 80;
    server_name ;
    root        /usr/share/nginx/html;
    index       index.php;

    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }

    location ~ ^(.+\.php)(.*)$ {
        fastcgi_split_path_info ^(.+\.php)(.*)$;
        fastcgi_index           index.php;
        fastcgi_pass            php-fpm;
        include                 /etc/nginx/mime.types;
        include                 fastcgi_params;
        fastcgi_param           PATH_INFO       $fastcgi_path_info;
        fastcgi_param           SCRIPT_FILENAME $document_root$fastcgi_script_name;
}
}

 nginx -t
 systemctl restart nginx
 systemctl restart php-fpm

* * * * *    /usr/bin/php /path/to/moodle/admin/cli/cron.php >/dev/null


