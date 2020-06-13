# Уведомления

####  [Ссылка на источник](https://laravel.demiart.ru/laravel-notifications/)

Это специальный инструмент для отправки сообщений пользователю.  
Изначально доступно отправление через: mail, sms, slack. Также можно сохранять их в базе данных.   
#### [Можно подключить телеграм бота](https://github.com/laravel-notification-channels/telegram)


## Требования:
Установленная авторизация.

`php artisan make:notification NewUser`  
`php artisan notifications:table`  
`php artisan migrate`  
 

app/Notifications/NewUser.php :
```
//меняем канал связи на более простой.
public function via($notifiable)
{
    return [/*'mail', */'database'];
}

public function toArray($notifiable)
{
    return [
        'message' => 'Аккаунт успешно зарегистрирован.'
    ];
}
```

## Пример - отправка уведомления каждый раз при заходе на /, уведомления отображаются в /home 


routes/web.php :
```
Route::get('/', function () {
    $user = Auth::user();
    $user->notify(new App\Notifications\NewUser);
    return view('welcome');
});

Route::get('/home', function () {
    $user = Auth::user();
    return view('home', ["notifications" => $user->unreadNotifications] );
});
```

`Auth::user()` != `null`, если произведена авторизация. 

views/home.blade.php :
```
...
@foreach ($notifications as $notification)
    <div class="alert alert-success">
        {{$notification->updated_at}} : 
        {{$notification->data['message']}}
    </div>
@endforeach
...
```