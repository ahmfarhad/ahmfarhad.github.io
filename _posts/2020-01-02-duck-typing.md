---
layout: post
title: What is Duck Typing in computer programming?
subtitle: In duck typing, the type of object is not important, what it can do or what properties it has are important.
tags: [development, golang, javascript]
comments: true
---

> If it walks like a duck and it quacks like a duck, then it must be a duck

When the programming language tries to do the job with the given object. The compiler/interpreter determines if an object is suitable for the operation by checking its methods and properties.

Duck typing happens a lot in dynamic typed languages (PHP, JavaScript, Ruby,...) but it's not limited to them.

In duck typing, the type of object is not important, what it can do or what properties it has are important.

Example in JavaScript:

```javascript
function add(val1, val2) {
  return val1 + val2;
}

// when the given value is numeric it uses math addition
// returns 3
add(1, 2);

// when the given value is string it use string concat
// returns HelloWorld
add("Hello", "World");
```

Example in Go:

```go
type Flyer interface {
	Fly(to string)
}

type Bird struct{}
type Person struct{}

func (p *Person) Fly(to string) {
	fmt.Println("Flying to", to, "using airplane.")
}

func (b *Bird) Fly(to string) {
	fmt.Println("Flying to", to, "using wings.")
}

func FlyLondon(flyer Flyer) {
	flyer.Fly("London")
}

func main() {
  // prints "Flying to London using wings."
  FlyLondon(&Bird{})

  // prints "Flying to London using airplane."
  FlyLondon(&Person{})
}
```
