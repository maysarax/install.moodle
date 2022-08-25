# install.moodle
 
 
 
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

