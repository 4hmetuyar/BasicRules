# "continue" should not be used

- `continue` is an unstructured control flow statement. It makes code less testable, less readable and less maintainable. Structured control flow statements such as if should be used instead.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```c#
 for (i = 0; i < 10; i++) {
    if (i == 5) {
      continue;  /* Noncompliant */
    }
    alert("i = " + i);
  }
```

### Compliant Solution (Uygun Kod Örneği) :

```c#
  for (i = 0; i < 10; i++) {
    if (i != 5) {  /* Compliant */
      alert("i = " + i);
    }
  }
```