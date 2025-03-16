# laragon-custom-domain-add
🚀 Setting Up a Custom Domain in Laragon

## **1. Navigate to Apache Configuration :**  
```plaintext
C:\laragon\etc\apache2\sites-enabled\
```
## **2. Create a Virtual Host Configuration File :**

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
## **3. Edit the Hosts File :**
Open the `hosts` file using any code editor following this directory

```plaintext
C:\Windows\System32\drivers\etc\
```
Add the following line :
```plaintext
127.0.0.1 myproject.test
```
## **4. Restart Laragon :**
`Menu > Apache > Restart`

## **5. Create a Empty Folder Same As Your Domain Name :**
`(e.g., myproject)`

## **6. Test Your Custom Domain :**
After completing the above steps, you can access your project using your custom domain name, such as [http://myproject.test].
If you face any issue, `Restart your pc and open again` [http://myproject.test].
