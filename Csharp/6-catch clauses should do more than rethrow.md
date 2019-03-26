# "catch" clauses should do more than rethrow


- A catch clause that only rethrows the caught exception has the same effect as omitting the catch altogether and letting it bubble up automatically, but with more code and the additional detriment of leaving maintainers scratching their heads.

- Such clauses should either be eliminated or populated with the appropriate logic.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```c#
string s = "";
try
{
  s = File.ReadAllText(fileName);
}
catch (Exception e)  // Noncompliant
{
  throw;
}
```

### Compliant Solution (Uygun Kod Örneği) :

```c#
string s = "";
try
{
  s = File.ReadAllText(fileName);
}
catch (Exception e) // Compliant
{
  logger.LogError(e);
  throw;
}
```
or 

```c#
string s = File.ReadAllText(fileName);
````
