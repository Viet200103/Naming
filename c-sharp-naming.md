# C# CONVENTIONS

---

references: https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions

---
**In short**

| Object Name        | Notation   | Char Mask   |
|:-------------------|:-----------|:------------|
| Namespace name     | PascalCase | [A-z][0-9]  |
| Class name         | PascalCase | [A-z][0-9]  |
| Constructor name   | PascalCase | [A-z][0-9]  |
| Method name        | PascalCase | [A-z][0-9]  |
| Method arguments   | camelCase  | [A-z][0-9]  |
| Local variables    | camelCase  | [A-z][0-9]  |
| Constants name     | PascalCase | [A-z][0-9]  |
| Field name Public  | PascalCase | [A-z][0-9]  |
| Field name Private | _camelCase | _[A-z][0-9] |
| Properties name    | PascalCase | [A-z][0-9]  |
| Delegate name      | PascalCase | [A-z]       |
| Enum type name     | PascalCase | [A-z]       |

---
**Classes, Structs, and Interfaces**

* Using PascalCase
* Class and struct should use nouns or noun phrases
* Interface names begin with a capital 'I' prefix, should be adjective phrases, nouns or noun phrases. Example:
  ```IComponent```, ```IPersistable```
* Consider ending the name of derived classes with the name of the base class.
  Example: ```ArgumentOutOfRangeException```, which is a kind of ```Exception```

---
**Enumeration Type**

* Using PascalCase
* Use a singular name for most Enum types, but use a plural name for Enum types that are bit fields.
* Always add the FlagsAttribute to a bit field Enum type.

---
**Generic Type Parameter**

* Type parameter name begin with a capital 'T' prefix
* Do name generic type parameters with descriptive names
* Consider using T as the type parameter name for types with one single-letter type parameter.

Example

```
public interface ISessionChannel<TSession> { /*...*/ }
public delegate TOutput Converter<TInput, TOutput>(TInput from);
public class List<T> { /*...*/ }
```

---
**Type members**

1. **Name of method**
    * Using PascalCase
    * Using verbs or verb phrases to give names

   ```
    public class String {
        public int CompareTo(...);
        public string[] Split(...);
        public string Trim();
    }
   ```

2. **Name of properties**
    * Using PascalCase
    * Using noun, noun phrase, or adjective to give names
    * The boolean properties with an affirmative phrase, should begin with 'is', 'can', 'has'

3. **Name of Fields**
    * Private or internal fields start with an underscore(_)
    * Static fields that are private or internal, use the s_ prefix and for thread static use t_

    ```
    public class DataService {
        private IWorkerQueue _workerQueue;
   
        private static IWorkerQueue s_workerQueue;
    
        [ThreadStatic]
        private static TimeSpan t_timeSpan;
    }
    ```