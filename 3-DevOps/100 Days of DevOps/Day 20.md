
## **Step 1: SSH into App Server 2**

`ssh root@stapp02`

(or use your sudo user)

---

## **Step 2: Install Nginx**

`sudo yum install -y epel-release sudo yum install -y nginx`

### **Configure Nginx to listen on 8095 and use /var/www/html**

1. Edit default config:
    

`sudo nano /etc/nginx/nginx.conf`

2. Add a server block (or modify the existing one):
    

`server {     listen 8095;     server_name stapp02;     root /var/www/html;     index index.php index.html index.htm;      location / {         try_files $uri $uri/ =404;     }      location ~ \.php$ {         include fastcgi_params;         fastcgi_pass unix:/var/run/php-fpm/default.sock;         fastcgi_index index.php;         fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;     } }`

3. Test Nginx and start it:
    

`sudo nginx -t sudo systemctl enable nginx sudo systemctl restart nginx`

---

## **Step 3: Install PHP-FPM 8.3**

PHP 8.3 isn’t in CentOS default repos, so we need **Remi’s repo**:

`sudo yum install -y yum-utils sudo yum install -y https://rpms.remirepo.net/enterprise/remi-release-8.rpm sudo yum module enable php:remi-8.3 -y sudo yum install -y php php-fpm`

---

## **Step 4: Configure PHP-FPM to use the Unix socket**

1. Create parent directory for socket:
    

`sudo mkdir -p /var/run/php-fpm sudo chown nginx:nginx /var/run/php-fpm`

2. Edit pool config (default pool):
    

`sudo nano /etc/php-fpm.d/www.conf`

Change these lines:

`listen = /var/run/php-fpm/default.sock listen.owner = nginx listen.group = nginx listen.mode = 0660`

3. Enable and restart PHP-FPM:
    

`sudo systemctl enable php-fpm sudo systemctl restart php-fpm`

---

## **Step 5: Test Nginx + PHP-FPM integration**

1. Create a test PHP file:
    

`echo "<?php phpinfo(); ?>" | sudo tee /var/www/html/index.php`

2. From the jump host:
    

`curl http://stapp02:8095/index.php`

✅ You should see the PHP info page.

---

💡 **Tip:**

- Make sure firewalld allows port 8095:
    

`sudo firewall-cmd --permanent --add-port=8095/tcp sudo firewall-cmd --reload`