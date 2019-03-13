# "===" and "!==" should be used instead of "==" and "!="

> The `==` and `!=` operators do type coercion before comparing values. This is bad because it can mask type errors. For example, it evaluates ' `\t\r\n' == 0` as `true`.

> It is best to always use the side-effect-less `===` and `!==` operators instead. (Karşılaştırma operatörlerinden kullanımı en uygun olan `===` ve `==!` şeklindedir.)

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```javascript
if (variable == 'ahmet') {...} // Noncompliant
```

### Compliant Solution (Uygun Kod Örneği) :

```javascript
if (variable === 'ahmet') {...}
```

### Exceptions (İstisnalar) :

> Even if testing the equality of a variable against null doesn't do exactly what most JavaScript developers believe, usage of `==` or `!=` is tolerated in such context. In the following case, if variable hasn't been initialized, its default value is not null but undefined. Nevertheless `undefined == null`, so JavaScript developers get the expected behavior.

```javascript
if(variable == null) {...}
```
