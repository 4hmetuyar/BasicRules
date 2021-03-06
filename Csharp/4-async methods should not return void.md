# "async" methods should not return "void"

> An async method with a void return type is a "fire and forget" method best reserved for event handlers because there's no way to wait for the method's execution to complete and respond accordingly. There's also no way to catch exceptions thrown from the method.

- Having an async void method that is not an event handler could mean your program works some times and not others because of timing issues. Instead, async methods should return Task.

- This rule raises an issue when non-event handler methods are both async and void.

### Noncompliant Code Example (Uygunsuz Kod Örneği) :

```c#
class HttpPrinter
{
  private string content;

  public async void CallNetwork(string url) //Noncompliant
  {
    var client = new HttpClient();
    var response = await client.GetAsync(url);
    content = await response.Content.ReadAsStringAsync();
  }

  public async Task PrintContent(string url)  // works correctly if web request finishes in under 1 second, otherwise content will be null
  {
    CallNetwork(url);
    await Task.Delay(1000);
    Console.Write(content);
  }
}
```

### Compliant Solution (Uygun Kod Örneği) :

```c#
class HttpPrinter
{
  private string content;

  public async Task CallNetwork(string url)
  {
    var client = new HttpClient();
    var response = await client.GetAsync(url);
    content = await response.Content.ReadAsStringAsync();
  }

  public async Task PrintContent(string url)
  {
    await CallNetwork(url); // <----- call changed here. If await is not added warning CS4014 will be triggered
    await Task.Delay(1000);
    Console.Write(content);
  }
}
```

### Exceptions
- Event handlers, i.e. methods with two arguments, first one matching object sender and the second being or inheriting from EventArgs, are ignored.
