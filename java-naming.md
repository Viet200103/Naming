# JAVA CONVENTIONS

---

reference: https://google.github.io/styleguide/javaguide.html#s5.1-identifier-names

---

### Packages
* Use only lowercase letters and numbers (no underscores)
* Write in all lower case to avoid conflicts with class or interface names.
* Consecutive words are simply joined together

Example:

| Package                | status |
|------------------------|--------|
| com.example.deepspace  | Good   |
| com.example.deepSpace  | Bad    |
| com.example.deep_space | Bad    |

### Class

* Use PascalCase
* Use nouns or phrases to name the class
* Interface may include nouns, nouns phrases, adjective or adjective phrases
* A Test class has name ends with Test. Example: **HashIntegrationTest**

### Method

* Use camelCase
* Use verbs or verb phrases. Example **sendMessage** or **stop**

### Constant, Local variable, Parameter

* Constant uses UPPER_SNAKE_CASE : all uppercase letters, separated by underscores
* Non-constant are written in camelCase
* Local variable and parameter use camelCase

Example

```java

// Constants
static final int NUMBER=5;
static final ImmutableList<String> NAMES=ImmutableList.of("Ed","Ann");
static final Map<String, Integer> AGES=ImmutableMap.of("Ed",35,"Ann",32);
static final Joiner COMMA_JOINER=Joiner.on(','); // because Joiner is immutable
static final SomeMutableType[]EMPTY_ARRAY={};

// Not constants
static String nonFinal="non-final";
final String nonStatic="non-static";
static final Set<String> mutableCollection=new HashSet<String>();
static final ImmutableSet<SomeMutableType> mutableElements=ImmutableSet.of(mutable);
static final ImmutableMap<String, SomeMutableType> mutableValues=ImmutableMap.of("Ed",mutableInstance,"Ann",mutableInstance2);
static final Logger logger=Logger.getLogger(MyClass.getName());
static final String[]nonEmptyArray={"these","can","change"};

```

### Caught exceptions: not ignored

```
try{
    int i=Integer.parseInt(response);
    return handleNumericResponse(i);
} catch(NumberFormatException ok) {
    // When it truly is appropriate to take no action whatsoever in a catch block,
    // the reason this is justified is explained in a comment.
}
```

### Basic formatting of Javadoc blocks

```
/**
 * Multiple lines of Javadoc text are written here,
 * wrapped normally...
 */
public int method(String p1) { ... }
```
