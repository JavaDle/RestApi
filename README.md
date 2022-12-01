# Простой RestApi на Laravel

## Laravel RestApi Конфигурация

- composer require laravel/sanctum
- php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"
- php artisan migrate

## app/Http/Kernel.php

    'api' => [
        \Laravel\Sanctum\Http\Middleware\EnsureFrontendRequestsAreStateful::class,
        'throttle:api',
        \Illuminate\Routing\Middleware\SubstituteBindings::class,
    ]
- раскомментировать EnsureFrontendRequestsAreStateful::class
## Добавляем в класс User

- HasApiTokens

## extend BaseController

- для api контроллеров делаем extend BaseController
- создаем ресурс для возврата данных в виде массива (не обязательно)
- php artisan make:resource

## Создание новых таблиц и моделей
- Чтобы создать новую таблицу выполняем команду ```bash php artisan make:model Payment -m ```
- -m в конце создать таблицу для базы данных которая создастся в папке database/migrations
- а также создастся модель в папке app/Models
- для того чтобы мы могли работать с данными должны добавлять все поля внутри переменной $fillable
#### Пример
    protected $fillable = [
        'name', 'detail'
    ];
- в папке миграций(таблиц) есть файл для примера по пути database/migrations
## Работа с Api
    'headers' => [
        'Accept' => 'application/json',
        'Authorization' => 'Bearer '.$accessToken,
    ]
- маршрут авторизации api/login
- маршрут регистрации api/register
- в запросах отправляем Bearer token с accept application/json

## Конфигурация
- Все контроллеры api находятся в папке app/Controllers/Api
- Все ресурсы для изменения вида response находятся в папке app/Resources
- маршруты находятся в папке routes/api.php

## Развертывание

- после git clone выполняем команду ```bash composer install ```
- в файле .env.example убираем .example
- настраиваем подключение к базе данных в файле .env
- для созданий таблиц выполняем команду ```bash php artisan migrate ```
- наслаждаемся.
