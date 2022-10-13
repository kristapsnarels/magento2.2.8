# Magento 2.2.8

1. Nginx 1.23.1;
2. PHP 7.2;
3. MySQL 5.7;
4. Redis;
5. RabbitMQ;
6. Node.js 6.11;

## Example project: [sportyme](https://convert.atlassian.net/wiki/spaces/DEVOPS/pages/85301190/sportyme.dev.convert.no+demo.convert.no)
To change the project:
1. Update `docker/nginx/config/default.conf`, reference: [convertteam/docker-magento2](https://bitbucket.org/convertteam/docker-magento2/src/danil-composer/docker_data/sites-enabled/)
   1. Update the `CONVERT_PROJECT_NAME` variable
2. Update `CONVERT_PROJECT_NAME` in `.env` file to the same as in nginx configuration file

## Setup
1. Clone this repository
2. Clone the Magento project inside this repository
3. run: `docker compose up -d`
4. Install Composer dependencies:
   1. `cd` to Magento 2.2.8 project root
   2. run: `docker compose exec php composer install`