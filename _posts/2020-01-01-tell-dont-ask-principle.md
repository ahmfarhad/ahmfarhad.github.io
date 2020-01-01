---
layout: post
title: Tell don't ask principle in object oriented programming
subtitle: An easy OOP design rule on communication between objects in OOP
tags: [development, clean code, oop]
comments: true
---

You should tell the objects what you want them to do instead of querying them multiple times to be able to make a decision on behalf.

Since each object have access to its data and internal state; it can do its job, make decisions and take actions internally.

Tell don't ask principle bring a few benefits including `code reuse`, `testability` and reduce `control coupling`.

Not good:

```php
if (user.is_admin()){
  print user.admin_greeting();
}else{
  print user.user_greeting();
}
```

Better:

```php
// greeting method will decide what is the proper message
print current_user.greeting();
```

Not good:

```php
if (user.is_hungry()){
  user.eat();
}
```

Better:

```php
// eat method will check if user is hungry and decide on the action
print user.eat();
```
