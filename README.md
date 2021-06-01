<p align="center"> <img src="https://github.com/dbrax/tigopesa-tanzania/blob/master/Tigopesa%20Laravel%20Library.jpeg"></p>
# 

<h1 align="center">Tigopesa Secure API</h1>

[![Latest Version on Packagist](https://img.shields.io/packagist/v/epmnzava/tigosecure.svg?style=flat-square)](https://packagist.org/packages/epmnzava/tigosecure)
[![Total Downloads](https://img.shields.io/packagist/dt/epmnzava/tigosecure.svg?style=flat-square)](https://packagist.org/packages/epmnzava/tigosecure)
[![Emmanuel Mnzava](https://img.shields.io/badge/Author-Emmanuel%20Mnzava-green)](mailto:epmnzava@gmail.com)
![Build](https://travis-ci.com/alphaolomi/tigopesa-tanzania.svg?branch=master)

This package is created to help developers intergrate with Tigopesa Tanzania secure online api. More information of this can be found [here](https://epmnzava.medium.com/)

## Installation


## Version Matrix

Version | Laravel   | PHP Version
------- | --------- | ------------
1.0.0   | 8.0       | >= 8.0 
1.0.1   | 8.0       | >= 7.3 >= 8.0
1.0.2   | 8.0       | >= 7.2.5 >= 8.0

You can install the package via composer:

```bash
composer require epmnzava/tigosecure
```

## Update your config (for Laravel 5.4 and below)

Add the service provider to the providers array in config/app.php:

```php
Epmnzava\Tigosecure\TigosecureServiceProvider::class,
```
Add the facade to the aliases array in config/app.php:

```php
'Tigosecure' =>\Epmnzava\Tigosecure\TigosecureFacade::class,
```

## Publish the package configuration (for Laravel 5.4 and below)

Publish the configuration file and migrations by running the provided console command:

```bash
php artisan vendor:publish --provider="Epmnzava\Tigosecure\TigosecureServiceProvider"
```
### Enviroment Variables

|Attribute|Description|
|--|--|
|TIGO_CLIENT_ID | Provided Tigopesa Client ID|
|TIGO_CLIENT_SECRET | Provided Tigopesa Client Secret|
|TIGO_API_URL | Provided Tigopesa API Url |
|TIGO_PIN | Provided Tigopesa PIN Number|
|TIGO_ACCOUNT_NUMBER | Provided Tigopesa  Account Number|
|TIGO_ACCOUNT_ID | Provided Tigopesa Account ID |
|TIGO_REDIRECT |  Redirect url|
|TIGO_CALLBACK |  Callback url|
|APP_CURRENCY_CODE | Currency,  `TZS` for Tanzanian Shillings|
|LANG | Language code  `en` for English and `sw` for Swalihi|
## Usage

This release does not come with database tables for transaction or payments you need to create then  After you have filled all necessary variables , providers and facades this is how the package can be used.

On your controller 

``` php
<?php

namespace App\Http\Controllers;

use Tigosecure;

class TransactionController extends Controller
{
    public function customer_transaction()
    {
        $tigopesa_response = Tigosecure::make_payment("jacob", "laizer", "jacob@primeware.co.tz", "3000", "98778835628");
        return redirect($tigopesa_response->redirectUrl);
    }
}

```


On your controller you can also call it through this way.
```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Epmnzava\Tigosecure\Tigosecure;

class TransactionController extends Controller
{

    public function customer_transaction(Request $request)
    {

        $payment = new Tigosecure;
        $response = $payment->make_payment("emmanuel", "mnzava", "epmnzava@gmail.com", 4000, "48fhldplofhf" . rand(5, 100));

        return redirect($response->redirectUrl);
    }
}
    ```

### Testing

``` bash
composer test
```

### Changelog

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

### Security

If you discover any security related issues, please email epmnzava@gmail.com instead of using the issue tracker.

## Credits

- [Emmanuel Mnzava](https://github.com/dbrax)
- [All Contributors](../../contributors)

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

