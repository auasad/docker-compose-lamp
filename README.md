# Docker Compose LAMP stack
Based on the Docker images, built to be fast, small and extendable LAMP stack.

## Stack
* [PHP-FPM](https://github.com/a-kom/alpine-php_fpm)
* [Apache2 with MPM mode](https://github.com/a-kom/alpine-apache)
* [NGINX](https://github.com/a-kom/alpine-nginx)
* [Node.js](https://github.com/nodejs/docker-node)
* [MailHog](https://github.com/a-kom/alpine-mailhog)
* [NGROK](https://github.com/a-kom/alpine-ngrok)
* [Solr](https://github.com/docker-solr/docker-solr)
* [PhpMyAdmin](https://github.com/phpmyadmin/phpmyadmin)
* [Adminer](https://github.com/TimWolla/docker-adminer)
* [MariaDB](https://github.com/docker-library/mariadb)
* [PostgreSQL](https://github.com/docker-library/postgres)
* [MongoDB](https://github.com/docker-library/mongo)
* [Redis](https://github.com/docker-library/redis)
* [Memcached](https://github.com/docker-library/memcached)
* [StandaloneFirefoxDebug](https://github.com/SeleniumHQ/docker-selenium/tree/master/StandaloneFirefoxDebug)


The LAMP stack consists of the following containers:

| Container | Versions | Service name | Image | Enabled by default |
| --------- | -------- | ------------ | ----- | ------------------ |
| PHP-FPM                   | php-7, php-5       | php-fpm     | [lordius/alpine-php_fpm]                     | ✓ |
| Apache                    | latest             | apache2_mpm | [lordius/alpine-apache]                      | ✓ |
| Nginx                     | latest             | nginx       | [lordius/alpine-nginx]                       | ✓ |
| Node.js                   | node:8.4.0-alpine  | node        | [node]                                       |   |
| Mailhog                   | latest             | mailhog     | [lordius/alpine-mailhog]                     | ✓ |
| NGROK                     | latest             | ngrok       | [lordius/alpine-ngrok]                       | ✓ |
| Solr                      | 6.5.1              | solr        | [solr]                                       |   |
| PhpMyAdmin                | latest             | phpmyadmin  | [phpmyadmin/phpmyadmin]                      | ✓ |
| Adminer                   | latest             | adminer     | [adminer]                                    |   |
| MariaDB                   | 10.0               | mariadb     | [mariadb]                                    | ✓ |
| PostgreSQL                | latest             | postgres    | [postgres]                                   |   |
| MongoDB                   | latest             | mongo       | [mongo]                                      |   |
| Redis                     | latest             | redis       | [redis]                                      |   |
| Memcached                 | latest             | memcached   | [memcached]                                  |   |
| PHP-FPM-DATA              | php-7, php-5       | php-fpm-data| [lordius/alpine-php_fpm]                     |   |
| StandaloneFirefoxDebug    | 2.48.2             | selenium    | [selenium/standalone-firefox-debug]          |   |

## Requirements
### Linux

Install [Docker](https://docs.docker.com/engine/installation) and [Docker Compose](https://docs.docker.com/compose/install).

### Windows, MacOS
#### Docker Toolbox (Recommend)

Install [Docker Toolbox](https://docs.docker.com/toolbox/overview).

##  Introduction
### Linux
Run inside folder with **docker-compose.yml**: `docker-compose up -d`

To view **PHP** info with **Apache2 in MPM mode** use a link the IP: **http://172.55.0.2/info.php**.

To view **PHP** info with **NGINX** use the IP: **http://172.55.0.3/info.php**.

**MailHog** is available under **http://172.55.0.5:8025**

**NGROK** is available under **http://172.55.0.6:4040**

**PhpMyAdmin** is available under **http://172.55.0.8**

You could edit your system host file for accessing containers via domain names by adding lines (or something like this based on your IP and domains, don't forget to change `extra_hosts` in `docker-compose.yml`):

`172.55.0.8 phpmyadmin.dockerlamp`

`172.55.0.3 site.dockerlamp`

`172.55.0.5 mailhog.dockerlamp`

`172.55.0.6 ngrok.dockerlamp`

### Docker Toolbox
#### Windows
* Download and extract [Docker Compose LAMP](https://github.com/a-kom/docker-compose-lamp/releases) into your user directory.
Like `C:\Users\UserName\docker-compose-lamp`.
* Launch Docker Quickstart Terminal.
* Go to the [docker-compose-lamp directory](/docs/screenshots/Docker-Quickstart-Terminal-LAMP-directory.jpg): `cd /c/Users/UserName/docker-compose-lamp`.
* Run `docker-compose up -d`
* Launch [Kitematic (Alpha)](/docs/screenshots/Kinematic-launch.jpg).
* Go to *NGINX* container and press *Settings* [tab](/docs/screenshots/Kinematic-NGINX-check.jpg).
* Press Hostname/Ports [subtab](/docs/screenshots/Kinematic-NGINX-Hostname-Ports.jpg).
* Update *Published IP:PORT* with your value, e.g. `192.168.99.100:80` and press Save.
* Navigate to a browser http://192.168.99.100/info.php and check that NGINX container is available from a [browser](/docs/screenshots/Docker-Compose-LAMP-check-in-browser.jpg).
* Do the same thing with all other containers that you need to access in a browser. Don't forget, that `80` port is now busy, so
you could attach other containers to some other ports, like `8080`, `9080`, etc...

You could edit your system host file for accessing some containers via domain name by adding line (or something like this based on your IP and domains, don't forget to change `extra_hosts` in `docker-compose.yml`) like this:
`192.168.99.100 site.dockerlamp`

#### MacOS
Similar to Windows section instruction.

### Common for all OS

To enable **Selenium** check **docker-compose.yml** and uncomment related **selenium** and **php-fpm-data** sections.

To enable custom configs from files, please, check image info and uncomment related image volumes section.


For running multiple instances on your local machine you could update IP range or port inside **docker-compose.yml**. For this, on your instance change IPs to another range, e.g. from `172.55` to `172.54.*`. The same are for ports.


## Documentation
See READMEs for more details, like environment variables for images:

* [PHP-FPM](https://github.com/a-kom/alpine-php_fpm/blob/php-7/README.md)
* [Apache2 with MPM mode](https://github.com/a-kom/alpine-apache/blob/master/README.md)
* [NGINX](https://github.com/a-kom/alpine-nginx/blob/master/README.md)
* [Node.js](https://github.com/nodejs/docker-node)
* [MailHog](https://github.com/a-kom/alpine-mailhog/blob/master/README.md)
* [NGROK](https://github.com/a-kom/alpine-ngrok/blob/master/README.md)
* [Solr](https://github.com/docker-solr/docker-solr)
* [PhpMyAdmin](https://github.com/phpmyadmin/phpmyadmin)
* [Adminer](https://github.com/TimWolla/docker-adminer)
* [MariaDB](https://github.com/docker-library/mariadb)
* [PostgreSQL](https://github.com/docker-library/postgres)
* [MongoDB](https://github.com/docker-library/mongo)
* [Redis](https://github.com/docker-library/redis)
* [Memcached](https://github.com/docker-library/memcached)
* [StandaloneFirefoxDebug](https://github.com/SeleniumHQ/docker-selenium/tree/master/StandaloneFirefoxDebug)

## License

This project is licensed under the MIT open source license.
