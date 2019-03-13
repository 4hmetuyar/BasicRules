# "indexOf" checks should not be for positive numbers


> Most checks against an `indexOf` call against a string or array compare it with -1 because 0 is a valid index. Any checks which look for values > 0 ignore the first element, which is likely a bug. If you're merely checking the presence of the string, consider using `includes` instead.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```javascript
var color = "blue";
var name = "ishmael";
var number = 123;

var arr = [color, name];

if (arr.indexOf("blue") > 0) { // Noncompliant
  // ...
}
if (arr[0].indexOf("ish") > 0 { // Noncompliant
  // ...
}
```

### Compliant Solution (Uygun Kod Örneği) :

```javascript
var color = "blue";
var name = "ishmael";
var number = 123;

var arr = [color, name];

if (arr.indexOf("blue") >= 0) {
  // ...
}
if (arr[0].includes("ish")) {
  // ...
}
```

