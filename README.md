# NGINX Configurations

## Basic
You'll need an installed nginx.  
For CentOS:
```bash
cat <<EOF >> /etc/yum.repos.d/nginx.repo
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/centos/7/$basearch/
gpgcheck=0
enabled=1
EOF

yum install nginx

# Additional certbot
yum install certbot python2-certbot-nginx
```
