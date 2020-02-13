# webserver tls configs

Docker container to easily test different configs with nginx and apache2.

https://owasp.org/www-project-cheat-sheets/cheatsheets/TLS_Cipher_String_Cheat_Sheet.html

and

https://bettercrypto.org/#_nginx

should give a good headstart.

## Generate the certs
```bash
cd ./ssl
openssl req -new -newkey rsa:4096 -days 3650 -nodes -x509 -subj "/C=XX/ST=XX/L=XXX/O=XXX/CN=XXXXX.XX" -keyout certificate.key -out certificate.crt
# cheat with dh creation.....
openssl dhparam -out dhparam4096.pem 1024 
```

## nginx/default.conf

Template file for nginx.

## manual testing

```bash
# brew install sslscan
# or
# apt install sslscan
sslscan --sni-name=localhost.localdomain https://localhost:8443
```