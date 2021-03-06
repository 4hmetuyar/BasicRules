# "abstract" classes should not have "public" constructors

> Since abstract classes can't be instantiated, there's no point in their having `public` or `internal` constructors. If there is basic initialization logic that should run when an extending class instance is created, you can by all means put it in a constructor, but make that constructor private or protected.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```c#
abstract class Base
{
    public Base() // Noncompliant, should be private or protected
    {
      //...
    }
}
```

### Compliant Solution (Uygun Kod Örneği) :

```c#
abstract class Base
{
    protected Base()
    {
      //...
    }
}
```