# Array-mutating methods should not be used misleadingly


> Many of JavaScript's Array methods return an altered version of the array while leaving the source array intact. reverse and sort do not fall into this category. Instead, they alter the source array in addition to returning the altered version, which is likely not what was intended.

> This rule raises an issue when the return values of these methods are assigned, which could lead maintainers to overlook the fact that the original value is altered.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```javascript
var b = a.reverse(); // Noncompliant
var d = c.sort(); // Noncompliant
```

### Compliant Solution (Uygun Kod Örneği) :

```javascript
var b = [...a].reverse();  // de-structure and create a new array, so reverse doesn't impact 'a'
a.reverse();

c.sort(); // this sorts array in place
```