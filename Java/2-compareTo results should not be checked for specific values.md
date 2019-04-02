# "compareTo" results should not be checked for specific values

> While most `compareTo` methods return -1, 0, or 1, some do not, and testing the result of a `compareTo` against a specific value other than 0 could result in false negatives.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```java
if (myClass.compareTo(arg) == -1) {  // Noncompliant
  // ...
}
```

### Compliant Solution (Uygun Kod Örneği) :

```java
if (myClass.compareTo(arg) < 0) {
  // ...
}
```

