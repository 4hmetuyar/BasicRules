# "async" and "await" should not be used as identifiers

> Since C# 5.0, `async` and `await` are contextual keywords. Contextual keywords do have a particular meaning in some contexts, but can still be used as variable names. Keywords, on the other hand, are always reserved, and therefore are not valid variable names. To avoid any confusion though, it is best to not use `async` and `await` as identifiers.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```c#
int await = 42; // Noncompliant
```

### Compliant Solution (Uygun Kod Örneği) :

```c#
int someOtherName = 42;
```