# 🐳 Symfony 6.1 Boilerplate (Nginx-Traefik-PHP:8.1.7-Node)

This is my custom config. I'm using this repository for fresh symfony start. Currently I have local dev environment with traefik. This repository automatically connects with my dev environment. If you have traefik locally, you can clone and run this repository easily.

### Container
| name          | contains                                                                                                                                                                  | port       |
|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| php           | [php-fpm](https://hub.docker.com/_/php) 8.1.7, [composer](https://getcomposer.org/) latest, [yarn](https://yarnpkg.com/lang/en/) latest, [node.js](https://nodejs.org/en/) latest | 9000 |
| nginx         | [nginx](https://hub.docker.com/_/nginx) latest                                                                                                                              | 80   |                                                                                                                           | 27017       |                                                                                                                           

## 🚀&nbsp; Quick Setup

```
git clone https://github.com/yahya077/symfony-docker-starter.git
docker-compose up -d && docker exec -it php bash
composer install
