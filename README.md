# WIP

# Laravel IP middleware

[![Latest Stable Version](https://poser.pugx.org/orkhanahmadov/laravel-ip-middleware/v/stable)](https://packagist.org/packages/orkhanahmadov/laravel-ip-middleware)
[![Latest Unstable Version](https://poser.pugx.org/orkhanahmadov/laravel-ip-middleware/v/unstable)](https://packagist.org/packages/orkhanahmadov/laravel-ip-middleware)
[![Total Downloads](https://img.shields.io/packagist/dt/orkhanahmadov/laravel-ip-middleware)](https://packagist.org/packages/orkhanahmadov/laravel-ip-middleware)
[![License](https://img.shields.io/github/license/orkhanahmadov/laravel-ip-middleware.svg)](https://github.com/orkhanahmadov/laravel-ip-middleware/blob/master/LICENSE.md)

[![Build Status](https://img.shields.io/travis/orkhanahmadov/laravel-ip-middleware.svg)](https://travis-ci.org/orkhanahmadov/laravel-ip-middleware)
[![Test Coverage](https://api.codeclimate.com/v1/badges/57f7522d9788782e3246/test_coverage)](https://codeclimate.com/github/orkhanahmadov/laravel-ip-middleware/test_coverage)
[![Maintainability](https://api.codeclimate.com/v1/badges/57f7522d9788782e3246/maintainability)](https://codeclimate.com/github/orkhanahmadov/laravel-ip-middleware/maintainability)
[![Quality Score](https://img.shields.io/scrutinizer/g/orkhanahmadov/laravel-ip-middleware.svg)](https://scrutinizer-ci.com/g/orkhanahmadov/laravel-ip-middleware)
[![StyleCI](https://github.styleci.io/repos/209357635/shield?branch=master)](https://github.styleci.io/repos/209357635)

Laravel middleware for whitelisting incoming client IP addresses

## Installation

You can install the package via composer:

```bash
composer require orkhanahmadov/laravel-ip-middleware
```

## Usage

Register middleware in `$routeMiddleware` in `app/Http/Kernel.php` file:

```php
protected $routeMiddleware = [
    // ...
    'ip_whitelist' => Orkhanahmadov\LaravelIpMiddleware\WhitelistMiddleware::class,
];
```

Use middleware in any of your routes and pass whitelisted IP address:

```php
Route::middleware('ip_whitelist:1.1.1.1')->get('/', 'HomeController@index');
// you can also pass multiple IP addresses with comma:
Route::middleware('ip_whitelist:1.1.1.1,2.2.2.2')->get('/', 'HomeController@index');
```

This will block all requests where client IP not matching whitelisted IP list.

## Configuration

Run this command to publish package config file:

```bash
php artisan vendor:publish --provider="Orkhanahmadov\LaravelIpMiddleware\LaravelIpMiddlewareServiceProvider"
```

`ip-middleware.php` config file contains following settings:

* `ignore_environments` - Middleware ignores IP checking when application is running in listed environments.
* `error_code` - HTTP code that shown when request gets rejected.

### Testing

``` bash
composer test
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email ahmadov90@gmail.com instead of using the issue tracker.

## Credits

- [Orkhan Ahmadov](https://github.com/orkhanahmadov)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.
