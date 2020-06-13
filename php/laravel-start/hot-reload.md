# Автоматическое обновление страницы при изменении файликов

Под wsl не работает =(  
Пришлось пользоваться нодой из винды


webpack.mix.js:
```
mix.js('resources/js/app.js', 'public/js')
    .sass('resources/sass/app.scss', 'public/css')
    .browserSync('localhost:8000'); // адрес сервера

```
Как я понял, он открывает некий прокси сервер и запускает сайт на 3000 порту. 

`npm install cross-env`  
`npm run watch`


[Почитать о mix и о сборке фронтенда](https://laravel.su/docs/5.4/mix)