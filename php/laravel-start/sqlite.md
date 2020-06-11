# Запуск и настройка sqlite для laravel + авторизация

`sudo apt-get install php7.4-sqlite3 -y`  


`touch database/database.sqlite`
.env:
``` 
DB_CONNECTION=sqlite
DB_DATABASE=/mnt/d/web/app/database/database.sqlite # абсолютный путь
DB_FOREIGN_KEYS=true
```


`php artisan migrate:install`

установим средства для авторизации

`composer require laravel/ui`  

создадим страницу

`php artisan ui vue --auth`  
`npm install && npm run dev`   
после каждого обновления базы и добавления модулей(?)  
`php artisan migrate`

