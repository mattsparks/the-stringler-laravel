# The Stringler Laravel Package

A Laravel package for [The Stringler](https://github.com/spatie/string).

## Install

After composer has done its thing, add the package service provider to the array in `config.app`:

```php
TheStringler\Manipulator\Manipulator::class
```

Then add the facade to the aliases array, also in `config.php`:

```php
'Manipulator' => TheStringler\Manipulator\ManipulatorFacade::class,
```