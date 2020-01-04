---
layout: post
title: PHP magic methods for object oriented programming
subtitle: They don't exist but they work for you
tags: [development, php]
comments: true
---

You can make your PHP classes dynamic by using magic methods.

Example usages:
- a model class which fetches a database record can use magic properties to return each record's field value.
- a model class which fetches a database record can use magic methods to get custom criteria for each field. 
  - `whereAge(10)` where age = 10,
  - `whereCity('london')` where city = 'london'


```php
class Example {
    public $test = 'My Test Property';
    public function __get($property_name){
        return "$property_name doesn't exists but you still can handle it.";
    }

    public function __call($method_name, $args){
        return "$method_name doesn't exists but you still can handle it.";
    }

    public static function __callStatic($static_method_name, $arguments){
        return "$static_method_name doesn't exists but you still can handle it.";
    }

    function __toString() {
        return "you can use a class as an string";
    }
}

$example = new Example();

// prints some_property doesn't exists but you still can handle it.
echo $example->some_property;

// prints some_method doesn't exists but you still can handle it.
echo $example->some_method();

// prints some_static_method doesn't exists but you still can handle it.
echo $example::some_static_method();

// prints you can use a class as an string
echo $example;
```

[More PHP magic methods on official documentation](https://www.php.net/manual/en/language.oop5.magic.php)
