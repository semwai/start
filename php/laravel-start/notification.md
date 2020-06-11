# Уведомления

####  [Ссылка на источник](https://laravel.demiart.ru/laravel-notifications/)

Это специальный инструмент для отправки сообщений пользователю.  
Изначально доступно отправление через: mail, sms, slack. Также можно сохранять их в базе данных.   
#### [Можно подключить телеграм бота](https://github.com/laravel-notification-channels/telegram)


`php artisan make:notification NewUser`

 
```
//меняем канал связи на более простой.
public function via($notifiable)
{
    return [/*'mail', */'database'];
}
```

## Пример - отправка уведомления каждый раз при заходе на /, уведомления отображаются в /home 


routes/web.php
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
views/home.blade.php
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