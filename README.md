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

## Routes

- все маршруты находятся в папке routes/api.php

## Работа с Api
    'headers' => [
        'Accept' => 'application/json',
        'Authorization' => 'Bearer '.$accessToken,
    ]
- маршрут авторизации api/login
- маршрут регистрации api/register
- в запросах отправляем Bearer token с accept application/json

