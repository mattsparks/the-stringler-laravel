# The Stringler Laravel Package

A Laravel package for [The Stringler](https://github.com/mattsparks/the-stringler), a string manipulation class.

## Install
Compsoser:
```
composer require thestringler-laravel/manipulator
```

After composer has done its thing, add the package service provider to the array in `config.app`:

```php
TheStringlerLaravel\Manipulator\Manipulator::class
```

Then add the facade to the aliases array, also in `config.php`:

```php
'Manipulator' => TheStringlerLaravel\Manipulator\ManipulatorFacade::class,
```

Helper function:
```php
$string = manipulate('hello')->toUpper();
```
