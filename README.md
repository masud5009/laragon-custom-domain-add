# laragon-custom-domain-add
🚀 Setting Up a Custom Domain in Laragon

**1️⃣ Navigate to Apache Configuration :**  
```plaintext
C:\laragon\etc\apache2\sites-enabled\
```
**2️⃣ Create a Virtual Host Configuration File :**

Create a new `.conf` file `(e.g., myproject.conf)` inside `sites-enabled` and add the following content:
```plaintext
define ROOT "D:/laragon/www/myproject/public"
define SITE "myproject.test"

<VirtualHost *:80> 
    DocumentRoot "${ROOT}"
    ServerName ${SITE}
    ServerAlias *.${SITE}
    <Directory "${ROOT}">
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>

<VirtualHost *:443>
    DocumentRoot "${ROOT}"
    ServerName ${SITE}
    ServerAlias *.${SITE}
    <Directory "${ROOT}">
        AllowOverride All
        Require all granted
    </Directory>

    SSLEngine on
    SSLCertificateFile      D:/laragon/etc/ssl/laragon.crt
    SSLCertificateKeyFile   D:/laragon/etc/ssl/laragon.key
 
</VirtualHost>
```
**3️⃣ Edit the Hosts File :**
Open the `hosts` file using any code editor following this directory

```plaintext
C:\Windows\System32\drivers\etc\
```
Add the following line :
```plaintext
127.0.0.1 myproject.test
```
