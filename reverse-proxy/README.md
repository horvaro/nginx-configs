# NGINX Reverse Proxy Config

Create folder for configs to include
```bash
mkdir /etc/nginx/configs
```

 - `nginx.conf`: Main nginx config file with some TLS tuning and inclusion of the sub-configs  
 - `configs/acme-challange.conf`: Set rule for LE ACME challange  
 - `configs/proxy.conf`: Proxy headers
 - `configs/security.conf`: Security headers
 - `conf.d/mysite.com.conf`: Reverse proxy configuration for mysite.com


To create LE certificates, you need to comment out the HTTPS Part inside the mysite.com.conf and run the certbot command:  
```bash
certbot certonly --nginx -d mysite.com
```
After that, you can activate the HTTPS part again.

For automation, the certbot renewal process can be added to the crontab:
```bash
echo "0 0,12 * * * root python -c 'import random; import time; time.sleep(random.random() * 3600)' && certbot renew" | sudo tee -a /etc/crontab > /dev/null
```
