# Docker image with Nginx + OpenSSL 3 + GOST engine

The docker image with nginx 1.23.2 + openssl 3.0.5 + gost engine 3.0.1
Supports GOST ciphers and up to TLSv1.2

## Build
```
git clone https://github.com/vheathen/docker-nginx-openssl3-gost.git
cd docker-nginx-openssl3-gost
docker build nginx-openssl3-gost --tag nginx-openssl3-gost
```

## Nginx config
Use the following settings for virtual hosts which require to be accessible with GOST TLS session:

```
    listen [::]:443 ssl;
    listen 443 ssl;
    ssl_certificate /etc/ssl/gost.cert.cer;
    ssl_certificate_key /etc/ssl/gost.secret.pem;
    ssl_ciphers GOST2012-GOST8912-GOST8912:HIGH:MEDIUM;
    ssl_protocols TLSv1.2;
    ssl_prefer_server_ciphers  on;
```

*It is necessary to disable TLSv1.3 for all virtual hosts!*

# Credits
Thanks for the initial work to Roman Nix (@rnixik) [https://github.com/rnixik/docker-openssl-gost](https://github.com/rnixik/docker-openssl-gost)