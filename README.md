# nextcloud-nginx-docker
This Repository shows how I managed my nextcloud installation.

I had problems installing nextcloud in a docker container and the upstream local nginx server. This is how I managed to get it working.

Server conf:
- Ubuntu 18.04.
- docker, docker-compose
- nginx
- nextcloud:fpm image
- certbot for https certificates

It works like this:
- Internet --> local nginx --> nextcloud nginx --> nextcloud --> mariadb

Here are some explanations for the files:

## docker-compose.yaml
- This compose file starts mariadb, nextcloud and a ngnix-web-proxy.
- You need a .env file for the secrets an environment.

## nginx.conf
- This is the config file for the ngnix-web-proxy. Its almost equal to the config file from the nextcloud documentation. It's linked in the compose file.

## local_ngnix
- Configuration for the "local" ngnix server. It links the request to http://127.0.0.1:<contanier_port>.
- certbot manage the certificates and it will look different from this file. This is just to show how the container link works. (/etc/nginx/sites-avaliable/example.com)
