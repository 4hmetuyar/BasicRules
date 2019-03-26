# "ConfigureAwait(false)" should be used


- After an awaited Task has executed, you can continue execution in the original, calling thread or any arbitrary thread. Unless the rest of the code needs the context from which the Task was spawned, Task.ConfigureAwait(false) should be used to keep execution in the Task thread to avoid the need for context switching and the possibility of deadlocks.

- This rule raises an issue when code in a class library awaits a Task and continues execution in the original calling thread.

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
