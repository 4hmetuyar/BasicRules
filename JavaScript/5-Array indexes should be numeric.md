# Array indexes should be numeric


> Associative arrays allow you to store values in an array with either numeric or named indexes. But creating and populating an object is just as easy as an array, and more reliable if you need named members.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```javascript
let arr = [];
arr[0] = 'a';
arr['name'] = 'bob';  // Noncompliant
arr[1] = 'foo';
```

### Compliant Solution (Uygun Kod Örneği) :

```javascript
let obj = {
  name: 'bob',
  arr: ['a', 'foo']
};
```