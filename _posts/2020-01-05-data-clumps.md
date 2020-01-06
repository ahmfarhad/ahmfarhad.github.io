---
layout: post
title: What is data clumps and how to refactor it?
subtitle: When more than one data are passed around the code together, make an object out of it
tags: [development, clean code, code smell]
comments: true
---

Data clumps happens when two or more data are often passed around the code together.

Data clumps might be an indicator of something wrong, deeper in the application code or architecture.

You need to check if one data in isolation can make sense or no, to identify data clumps.

Benefits of fixing data clumps:

- functions and methods parameters become shorter
- avoids code repetition
- makes codes shorter and more readable

Not good:

```javascript
function calculateDistance(x1, y1, x2, y2)
```

Better:

```javascript
class Coordinate {
  constructor(x, y) {
    this.x = x;
    this.y = y;
  }
}

coordinate1 = new Coordinate(1, 2)
coordinate2 = new Coordinate(3, 4)

function calculateDistance(coordinate1, coordinate2)
```

Not good:

```javascript
function isExpired(start_date, end_date)
```

Better:

```javascript
class DateRange {
  constructor(start_date, end_date) {
    ...
  }
}

function calculateLength(dateRange)
```

Not good:

```javascript
function welcomeMessage(firstname, lastname, age, job)
```

Better:

```javascript
function welcomeMessage(user)
```
