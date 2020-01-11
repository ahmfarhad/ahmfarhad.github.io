---
layout: post
title: Some of important PHP 7.* features
subtitle: List of important PHP code syntax changes from PHP 7.0 to 8.0
tags: [development, php]
comments: true
---

New PHP features let the code to be safer, faster and less error prone.

PHP 7.0 to PHP 7.3:

- Spaceship operator: `<=>`

```php
// if first operator is correct it returns -1, second 0 and third +1
echo 1 <=> 2; // -1
echo 1 <=> 1; // 0
echo 2 <=> 1; // 1
```

- intdiv: integer division

```php
echo intdiv(10, 3); // 3
```

- Type hinting
- Group Use Declarations:

  ```php
  use FooLibrary\Bar\Baz\{ ClassA, ClassB, ClassC as Fizbo }
  ```

- Return Type Declarations
- Multi catch
- Void Return Type; no return or just return; NULL is not a valid return value for a void function
- Nullable types:
  ```php
  function test(?string $name){
      var_dump($name);
  }
  ```
- Argon2 in password hash
- Null checking operator:
  `??`
- const array using define
- safe unserialize for untrusted data using whitelist classes
- NULL is not a valid return value for a void function
- Support for negative string offsets:
  ```php
  "abcdef"[-2] // 'e'
  ```
- New object type:
  ```php
  function test(object $obj) : object {
    return new SplQueue();
  }
  ```

PHP 7.4:

- Preloading: Preload PHP functions and classes once and use them in the context of any future request without overhead
- Declare types for class properties; forcing developers to instead use getter and setter methods
- Weak refs: allow keeping a reference to an object and preventing the object from being destroyed
- Null Coalescing Assignment Operator:
  ```php
  $data['comments']['user_id'] ??= 'value';
  ```

PHP 8.0

- Just in Time Compiler:
  - Let the codes run directly by CPU
  - Improves speed of application which use a lot of CPU time
  - Great for machine learning, data analysis,... applications
  - It doesn't speed up much I/O bound applications
