# Magento 2.2.8

1. Nginx 1.8;
2. PHP 7.2;
3. MySQL 5.7;
4. Redis;
5. RabbitMQ;
6. MailHog;

## Example project: [sportyme](https://convert.atlassian.net/wiki/spaces/DEVOPS/pages/85301190/sportyme.dev.convert.no+demo.convert.no)
To change the project:
1. update `docker//nginx/config/default.conf`, reference: [convertteam/docker-magento2](https://bitbucket.org/convertteam/docker-magento2/src/danil-composer/docker_data/sites-enabled/)
2. update `CONVERT_PROJECT_NAME` in `.env` file

## Setup
1. Clone this repository
2. Clone the Magento 2.2.8 project inside this repository
3. run: `docker compose up -d`
4. Install Composer dependencies:
   1. `cd` to Magento 2.2.8 project root
   2. run: `docker compose exec php composer install`