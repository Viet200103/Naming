# C# CONVENTIONS

---

references: https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions

---

* Interface start with 'I' prefix
* Attribute types end with the word Attribute
* Enum types use a singular noun for nonflags, and a plural noun for flags.

---

*   Class, interface, struct, delegate, record and their properties using PascalCase
*   Constant names, both fields and local constants using PascalCase.

```
public class DataService {
}

public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode
);
    
public struct ValueCoordinate {
}

public delegate void DelegateType(string message);
```


* Public members of types: fields, properties, event, methods using PascalCase
```
public class ExampleEvents {
    // A public field, these should be used sparingly
    public bool IsValid;

    // An init-only property
    public IWorkerQueue WorkerQueue { get; init; }

    // An event
    public event Action EventProcessing;

    // Method
    public void StartEventProcessing()
    {
        // Local function
        static int CountQueueItems() => WorkerQueue.Count;
        // ...
    }
}
```
* Private instance fields start with an underscore '_' and the remaining text is camelCased.
*   Private or internal fields, local variables, method parameters
    instances of a delegate type using camelCase
```
public class DataService
{
    private IWorkerQueue _workerQueue;
}
```


* Static fields that are private or internal, use the 's_' prefix
* Thread static use 't_' prefix.

```
public class DataService {
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```

*   Do name generic type parameters with descriptive names start with 'T' prefix,
    unless a single letter name is completely self explanatory and a descriptive name wouldn't add value.

```
public interface ISessionChannel<TSession> { /*...*/ }
public delegate TOutput Converter<TInput, TOutput>(TInput from);
public class List<T> { /*...*/ }
```