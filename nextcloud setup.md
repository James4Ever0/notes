# Nextcloud self-hosting tips

do not use nextcloud aio

use nextcloud-fpm, or some docker compose with this image

build and install apps manually in the mounted volume

```yaml
version: '3'

# Define network.
networks:
  main_network:

# Define services.
services:
  web:
    image: nginx:alpine
    restart: always
    depends_on:
      - app
    volumes:
      - ./config/nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - ./config/nginx/uploadsize.conf:/etc/nginx/conf.d/uploadsize.conf
      - ./config/nginx/private.conf:/etc/nginx/private.conf
      - ./config/nginx/ssl-cert-snakeoil.pem:/etc/nginx/ssl-cert-snakeoil.pem:ro
      - ./config/nginx/ssl-cert-snakeoil.key:/etc/nginx/ssl-cert-snakeoil.key:ro

    volumes_from:
      - app
    networks:
      - main_network
    ports:
      - 80:80
      - 443:443
  app:
    image: nextcloud:fpm
    restart: always
    depends_on:
      - db
      - redis
    volumes:
      - ${NEXTCLOUD_ROOT}/app/html:/var/www/html
      # Store data in service data directory.
      - ${NEXTCLOUD_ROOT}/app/html/data:/srv/nextcloud/data
    networks:
      - main_network
    environment:
      - NEXTCLOUD_TRUSTED_DOMAINS=<self_hosted_ip>
      - NEXTCLOUD_ADMIN_USER=admin
      - NEXTCLOUD_ADMIN_PASSWORD=<admin_password>
      - NEXTCLOUD_DATA_DIR=/srv/nextcloud/data
      - MYSQL_PASSWORD=nextcloud
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=db
      - REDIS_HOST=redis
      - REDIS_HOST_PASSWORD=redispass
      - PHP_MEMORY_LIMIT=10000M
      - PHP_UPLOAD_LIMIT=10000M
  redis:
    image: redis:alpine
    restart: always
    command: redis-server --requirepass redispass
    networks:
      - main_network
  db:
    image: mariadb
    restart: always
    command: --transaction-isolation=READ-COMMITTED --binlog-format=ROW --skip-innodb-read-only-compressed
    volumes:
      - ${NEXTCLOUD_ROOT}/database/mariadb:/var/lib/mysql
    networks:
      - main_network
    environment:
      - MYSQL_ROOT_PASSWORD=nextcloud
      - MYSQL_PASSWORD=nextcloud
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - NEXTCLOUD_ADMIN_USER=admin
      - NEXTCLOUD_ADMIN_PASSWORD=password
```
