---
layout: post
title: Replace temp with query to achieve cleaner and more maintainable code
subtitle: Find a temporary variable in a function body and extract it out as a method
tags: [development, clean code, code smell]
comments: true
---

An easy way to reduce functions/methods length and stick to single responsibility principle is to extract a portion of the function body as a separate function/method.

Use caching to serve faster, time-consuming expressions.

In general, favor readability over minor performance gain. These days most compilers are smart enough to make the code perform better.

Not good:

```ruby
def show
    is_allowed = current_user.is_admin || page.author == current_user.id

    return error unless is_allowed

    page
end
```

Better:

```ruby
def show
    return error unless is_allowed

    page
end

def is_allowed
    current_user.is_admin || page.author == current_user.id
end
```

Not good:

```javascript
function getTotalWithDiscount(items) {
  let discount = 0;
  if (items.length > 100) {
    discount = 0.5;
  } else if (items.length > 50) {
    discount = 0.2;
  } else {
    discount = 0;
  }

  totalBeforeDiscount = items.reduce(
    (a, b) => a.price * a.quantity + b.price * b.quantity
  );

  return totalBeforeDiscount * (1 - discount);
}
```

Better:

```javascript
function getTotalWithDiscount(items) {
  return getTotalWithoutDiscount(items) * (1 - discount(items));
}

function getTotalWithoutDiscount(items) {
  return items.reduce((a, b) => a.price * a.quantity + b.price * b.quantity);
}

function discount(items) {
  if (items.length > 100) {
    return 0.5;
  }

  if (items.length > 50) {
    return 0.2;
  }

  return 0;
}
```
