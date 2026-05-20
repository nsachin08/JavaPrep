```md
# Java Versions and Features After Java 8

# 1. Latest Java Version Used

Most modern enterprise projects currently use:

- Java 17 (LTS)
- Java 21 (Latest LTS)

Java 17 is extremely common in production banking and enterprise systems.
Java 21 adoption is rapidly increasing.

---

# 2. Features Introduced After Java 8

Java 8 was revolutionary because it introduced:

- Lambda Expressions
- Streams API
- Functional Interfaces
- Optional
- CompletableFuture
- Default methods

After Java 8, Java evolved rapidly.

---

# Java 9 Features

## Modular System (Project Jigsaw)

Introduced modules.

Earlier:

```java
Everything was inside one huge classpath.
```

Now:

```java
module my.app {
    requires java.sql;
}
```

Benefits:

- Better encapsulation
- Faster startup
- Smaller runtime images
- Better dependency management

---

## JShell

Interactive Java REPL.

```java
jshell> int a = 10
```

Useful for:

- quick testing
- debugging snippets
- learning

---

## Factory Methods for Collections

Before:

```java
List<String> list = new ArrayList<>();
list.add("A");
```

After Java 9:

```java
List<String> list = List.of("A", "B");
```

Immutable collections.

---

# Java 10 Features

## var Keyword

Local variable type inference.

```java
var name = "Sachin";
```

Compiler infers type.

Improves readability.

---

# Java 11 Features

## New HTTP Client API

Modern replacement for HttpURLConnection.

```java
HttpClient client = HttpClient.newHttpClient();
```

Supports:

- HTTP/2
- async calls
- websockets

---

## String Methods

Added:

```java
isBlank()
lines()
repeat()
strip()
```

---

## Lambda Parameter var

```java
(var x, var y) -> x + y
```

---

# Java 14 Features

## Switch Expressions

Before:

```java
switch(day) {
    case MONDAY:
        return 1;
}
```

Now:

```java
int value = switch(day) {
    case MONDAY -> 1;
    default -> 0;
};
```

Cleaner syntax.

---

# Java 15 Features

## Text Blocks

```java
String json = """
{
  "name":"Sachin"
}
""";
```

Useful for:

- SQL
- JSON
- XML

---

# Java 16 Features

## Records

Used for immutable DTOs.

```java
record Employee(String name, int salary) {}
```

Automatically generates:

- constructor
- getters
- equals
- hashCode
- toString

Massively reduces boilerplate.

---

# Java 17 Features

## Sealed Classes

Restrict inheritance.

```java
public sealed class Vehicle
    permits Car, Bike {}
```

Useful in domain modeling.

---

## Pattern Matching for instanceof

Before:

```java
if(obj instanceof String) {
    String s = (String)obj;
}
```

Now:

```java
if(obj instanceof String s) {
    System.out.println(s);
}
```

Cleaner code.

---

# Java 21 Features

## Virtual Threads (Project Loom)

One of the biggest Java improvements.

Traditional threads are expensive.

Virtual threads are lightweight.

```java
Thread.startVirtualThread(() -> {
    System.out.println("Hello");
});
```

Benefits:

- Massive concurrency
- Better scalability
- Simpler async programming

Useful for:

- APIs
- microservices
- high-scale backend systems

---

## Sequenced Collections

Provides predictable iteration order.

---

# Important Interview Insight

Interviewers usually expect:

- Java 17 knowledge minimum
- awareness of Java 21 virtual threads
- understanding of records and sealed classes
```