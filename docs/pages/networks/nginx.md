# NGINX Configuration

## Install NGINX on Ubuntu

```bash
sudo apt update && sudo apt install nginx -y && sudo nginx -v
```

!!! info ""
    Reference: [linode - Installing NGINX Open Source](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/)

## The Basic Terms

!!! info ""
    Reference: [linode - How to Configure NGINX](https://www.linode.com/docs/guides/how-to-configure-nginx/)

## Configure NGINX to serve static files

```nginx
server {
    listen 80;
    
    location / {
        # static files
        root /usr/share/nginx/html;
        server_name domain.com;
        index index.html index.htm;
        try_files $uri $uri/ /index.html =404;
    }
}
```

!!! info ""
    Reference: [NGINX Docs - Serving Static Content](https://docs.nginx.com/nginx/admin-guide/web-server/serving-static-content/)

## Configure NGINX as a reverse proxy

```nginx
server {
    listen 80;
    
    location / {
        # static files
        root /usr/share/nginx/html;
        server_name domain.com;
        index index.html index.htm;
        try_files $uri $uri/ /index.html =404;
    }

    location /api {
        proxy_pass http://127.0.0.1:8080;
    }

}
```

!!! info ""
    Reference: [NGINX Docs - NGINX Reverse Proxy](https://docs.nginx.com/nginx/admin-guide/web-server/reverse-proxy/)


## HTTP Basic Authentication

Install password file creation utility 

```bash
sudo apt update && sudo apt install apache2-utils -y
```

Create password file & the first user

```bash
sudo htpasswd -c /etc/nginx/.htpasswd username
```

Add the second user to the password file

```bash
sudo htpasswd /etc/nginx/.htpasswd username2
```

NGINX config

```nginx
server {
    auth_basic "Protected Area";
    auth_basic_user_file /etc/nginx/.htpasswd;

    location /public/ {
        auth_basic off;
    }
}
```

!!! info ""
    Reference: [NGINX Docs - Restricting Access with HTTP Basic Authentication](https://docs.nginx.com/nginx/admin-guide/security-controls/configuring-http-basic-authentication/)