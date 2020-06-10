## Создание laravel проектa

### Базовая настройка

Проверено для wsl ubuntu20.04 LTS

`sudo apt-get update`
`sudo apt-get install curl -y`
`sudo apt-get install php7.4 -y`
`sudo apt-get install php7.4-zip -y`
`sudo apt-get install php-gd php-xml php7.4-mbstring -y`
`sudo apt install nodejs -y`
`sudo apt install npm -y`
`sudo curl -s https://getcomposer.org/installer | php`
`sudo mv composer.phar /usr/local/bin/composer`
`composer global require laravel/installer`

### Создание проекта


`laravel new app`
`cd app`
Иногда он сам выполняет следующие 3 команды:
`cp .env.example .env`
`composer install`
`php artisan key:generate`

`npm install`
`php artisan serve`
[click](https:\\127.0.0.1:8000)
