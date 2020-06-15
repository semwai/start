# Создание форм.

`composer require "laravelcollective/html"`

config\app.php:

```
'providers' => [
    ...
    Illuminate\View\ViewServiceProvider::class,
    Collective\Html\HtmlServiceProvider::class,
    ...
],


'aliases' => [
    ...
    'Form' => Collective\Html\FormFacade::class,
    'Html' => Collective\Html\HtmlFacade::class,
    
    ...
]
```

views\newproduct.blade.php:
```

@if(!is_null($errors))
{{$errors}}
@endif

{{ Form::open(array('url' => 'newproduct')) }}            
    {{ Form::text('name', 'Название товара', array('class' => 'form-control')) }}
    <br>
    {{ Form::text('price', 'Цена', array('class' => 'form-control')) }}
    <br>
    {{ Form::submit('Добавить', array('class' => 'btn btn-success')) }}
{{ Form::close() }}
```

routes\web.php:
```
use Request;

Route::post('newproduct', array('before' => 'csrf', function () {
    $rules = array(
      'name' => array('required', 'unique:product,name'),
      'price' => array('required'),
       
    );
  
    $validation = Validator::make(Request::all(), $rules);
    
    if ($validation->fails()) {
      // проверка не пройдена.
      return view('newproduct', ['errors' => $validation->errors()]);
    }
    DB::table('product')->insert(['name' => Request::input('name', 'default'), 'price' => Request::input('price', '0')]);
    return "<h1>Товар добавлен</h1>";
  }));
```