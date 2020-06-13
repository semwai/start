# Полезности для работы с маршрутизацией

#### [link](https://laravel.demiart.ru/routing-advanced-tips/)
Простейший пример и двух страничек, для второй посылается переменная. Внутри шаблона к ней можно достучаться изнутри `{{...}}`
```
Route::get('/', function () {
    return view('welcome');
});

Route::get('/second', function () {
    return view('welcome', ["param1" => 1, "param2" => "second"]);
});
```




Ограничить количество запросов в минуту. Для не авторизованного - 1, для авторизованного - 59
```
Route::middleware('throttle:2|60,1')->group(function () {
    Route::get('/home', function () {
        return view('home');
    });
});
```