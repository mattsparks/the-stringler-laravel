# The Stringler Laravel Package

A Laravel package for [The Stringler](https://github.com/mattsparks/the-stringler), a string manipulation class.

## Install
Compsoser:
```
composer require thestringler-laravel/manipulator
```

After composer has done its thing, add the package service provider to the array in `/config/app.php`:

```php
TheStringlerLaravel\Manipulator\ManipulatorServiceProvider::class
```

Then add the facade to the aliases array, also in `config/app.php`:

```php
'Manipulator' => TheStringlerLaravel\Manipulator\ManipulatorFacade::class,
```

Helper function:
```php
$string = manipulate('hello')->toUpper();
```

## Methods
### append($string)
```php
manipulate('Freak')->append(' Out!');
// Freak Out!
```

### camelToSnake
```php
manipulate('camelCase')->camelToSnake();
// camel_case
```

### camelToClass
```php
manipulate('className')->camelToClass();
// ClassName
```

### capitalize
```php
manipulate('hello')->capitalize();
// Hello
```
### capitalizeEach
```php
manipulate('i like toast!')->capitalizeEach();
// I Like Toast!
```

### eachCharacter($closure)
```php
manipulate('hello')->eachCharacter(function($char) {
    return strtoupper($char);
});
// HELLO
```

### eachWord($closure, $preserveSpaces = false)
```php
manipulate('hello moto')->eachWord(function($word) {
    return strrev($word);
});
// ollehotom

manipulate('hello moto')->eachWord(function($word) {
    return strrev($word);
}, true);
// olleh otom
```

### getPossessive
```php
manipulate('Bob')->getPossessive();
// Bob's
manipulate('Silas')->getPossessive();
// Silas'
```

### htmlEntities($flags = ENT_HTML5, $encoding = 'UTF-8', $doubleEncode = true)
```php
manipulate('&')->htmlEntities();
// &amp;
```

### htmlEntitiesDecode($flags = ENT_HTML5, $encoding = 'UTF-8')
```php
manipulate('&amp;')->htmlEntitiesDecode();
// &
```

### htmlSpecialCharacters($flags = ENT_HTML5, $encoding = 'UTF-8', $doubleEncode = true)
```php
manipulate('&<>')->htmlSpecialCharacters();
// &amp;&lt;&gt;
```

### lowercaseFirst
```php
manipulate('HELLO')->lowercaseFirst();
// hELLO
```

### pad($length, $string, $type = null)
```php
manipulate('Hello')->pad(2, '!!', STR_PAD_RIGHT);
// Hello!!
```

### prepend($string)
```php
manipulate('is the one.')->prepend('Neo ');
// Neo is the one.
```

### pluralize($items = null)
```php
manipulate('Potato')->pluralize();
// Potatoes
```

You can optionally pass an array or numeric value to `pluaralize` to determine if the given string should be pluaralized.

```php
$dogs = ['Zoe', 'Spot', 'Pickles'];
manipulate('Dog')->pluralize($dogs);
// Dogs

$cats = ['Whiskers'];
manipulate('Cat')->pluralize($cats);
// Cat
```

### nthCharacter($nth, $closure)
```php
manipulate('Wordpress')->nthCharacter(5, function($character) {
    return mb_strtoupper($character);
});
// WordPress
```

### nthWord($nth, $closure, $preserveSpaces = true)
```php
manipulate('Oh hello there!')->nthWord(2, function($word) {
    return mb_strtoupper($word);
});
// Oh HELLO there!
```

### remove($string, $caseSensitive = true)
```php
manipulate('Dog Gone')->remove('Gone');
// Dog
```

### removeSpecialCharacters($exceptions = [])
```php
manipulate('Hello!!')->removeSpecialCharacters();
// Hello
manipulate('Hello!!')->removeSpecialCharacters(['!']);
// Hello!!
```

### repeat($multiplier = 1)
```php
manipulate('la')->repeat(3);
// lalala
```

### replace($find, $replace = '', $caseSensitive = true)
```php
manipulate('Pickles are good.')->replace('good', 'terrible');
// Pickles are terrible.
```

### reverse
```php
manipulate('Whoa!')->reverse();
// !aohW
```

### snakeToCamel
```php
manipulate('snake_case')->snakeToCamel();
// snakeCase
```

### snakeToClass
```php
manipulate('class_name')->snakeToClass();
// ClassName
```

### stripTags($allowed = '')
```php
manipulate('<i>Hello</i>')->stripTags();
// Hello
```

### toCamelCase
```php
manipulate('camel case')->toCamelCase();
// camelCase
```

### toL33t
```php
manipulate('Hack The Planet!')->toL33t();
// (-)@{|< +/-/€ |O7@|\|€][!
```

### toLower
```php
manipulate('LOWER')->toLower();
// lower
```

### toSlug
```php
manipulate('This is a slug!')->toSlug();
// this-is-a-slug
```

### toSnakeCase
```php
manipulate('snake case')->toSnakeCase();
// snake_case
```

### toString
This method just returns the string.

### toUpper
```php
manipulate('upper')->toUpper();
// UPPER
```

### trim
```php
manipulate('  trimmed  ')->trim();
// trimmed
```

### trimBeginning
```php
manipulate('  trimmed')->trimBeginning();
// trimmed
```

### trimEnd
```php
manipulate('trimmed  ')->trimEnd();
// trimmed
```

### truncate($length = 100, $append = '...')
```php
manipulate('This is a sentence and will be truncated.')->truncate(10, '...');
// This is a ...
```

### urlDecode
```php
manipulate('hello%21')->urlDecode();
// hello!
```

### urlEncode
```php
manipulate('hello!')->urlEncode();
// hello%21
```
## Chainable

All of these methods (minus `toString`) can be chained.

```php
manipulate('hello')->toUpper()->reverse();
// OLLEH
```
