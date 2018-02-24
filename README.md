# cara-menggunakan-workbench
Cara menggunakan workbench untuk membuat laravel packages


## Install & Config Workbench
Untuk lebih memahami packages ini silahkan pelajari dari git [JackieDo/workbench](https://github.com/JackieDo/workbench) yang dipakai ini.

1. Install package `jackiedo/workbench`

```bash
$ composer require jackiedo/workbench "5.4.*"
```

2. Edit `config/app.php` pada bagian `providers`

```php

'providers' => [
    ...
    Jackiedo\Workbench\WorkbenchServiceProvider::class,
],

```

3. Edit `bootstrap/autoload.php`

```php
define('LARAVEL_START', microtime(true));

/*
|--------------------------------------------------------------------------
| Register The Composer Auto Loader
|--------------------------------------------------------------------------
|
| Composer provides a convenient, automatically generated class loader
| for our application. We just need to utilize it! We'll require it
| into the script here so we do not have to manually load any of
| our application's PHP classes. It just feels great to relax.
|
*/

require __DIR__.'/../vendor/autoload.php';

// tambahkan script di bawah : 

if (is_dir($workbench = __DIR__.'/../workbench'))
{
    Jackiedo\Workbench\Starter::start($workbench);
}

```
4. Jalankan artisan command :

```bash
$ php artisan vendor:publish --provider="Jackiedo\Workbench\WorkbenchServiceProvider" --force
```

## Usage 

1. Membuat package :

```bash
$ php artisan workbench bantenprov/pendaftaran --resources

>>> Please step by step provide following informations:

 1. What is your name?:
 > bantenprov

 2. Hi bantenprov! What is your e-mail address?:
 > developer.bantenprov@gmail.com

 3. You can provide a short descripton for your package here if you want: [The Pendaftaran package]:
 > 

 4. Do you want PSR-4 autoloading standard for namespace Bantenprov\Pendaftaran in the composer.json file is pointed to the src/Bantenprov/Pendaftaran directory (if say no, this will be pointed to the src directory)? (yes/no) [yes]:
 > n

 5. Which of the following resources would you like to generate?

  - Facade? (yes/no) [yes]:
 > y

  - Interface? (yes/no) [yes]:
 > y

  - Abstract? (yes/no) [yes]:
 > y

  - Exception? (yes/no) [yes]:
 > y

  - Controller? (yes/no) [yes]:
 > y

  - Middleware? (yes/no) [yes]:
 > y

  - Model? (yes/no) [yes]:
 > y

  - Console? (yes/no) [yes]:
 > y

  - Config? (yes/no) [yes]:
 > y

  - Migration? (yes/no) [yes]:
 > y

  - Asset? (yes/no) [yes]:
 > y

  - Lang? (yes/no) [yes]:
 > y

  - View? (yes/no) [yes]:
 > y

  - Route? (yes/no) [yes]:
 > y

  - Helper? (yes/no) [yes]:
 > y


>>> Thanks for your informations. Package is being generated, please wait...

>>> Wow! Your package workbench is created and storaged at /home/demon/work/workbench/workbench/bantenprov/pendaftaran

Generating autoload files

```





