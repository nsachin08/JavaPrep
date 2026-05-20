# @RestController vs @Controller

# What is @Controller?

Used in:

```text
Traditional MVC applications
```

Returns:

- JSP pages
- Thymeleaf templates
- HTML views

---

# Example

```java
@Controller
public class HomeController {

    @GetMapping("/home")
    public String home() {
        return "home";
    }
}
```

Spring searches for:

```text
home.jsp
or
home.html
```

---

# What is @RestController?

Used for REST APIs.

Returns:

```text
JSON/XML response directly
```

---

# Example

```java
@RestController
public class UserController {

    @GetMapping("/user")
    public User getUser() {
        return new User();
    }
}
```

Spring converts object into JSON.

---

# Internal Difference

```java
@RestController
```

is internally:

```java
@Controller + @ResponseBody
```

---

# What Happens if We Replace @RestController with @Controller?

Suppose:

```java
@Controller
public class UserController {

    @GetMapping("/user")
    public User getUser() {
        return new User();
    }
}
```

Now Spring interprets returned object as:

```text
View Name
```

Instead of JSON.

Application may fail with:

```text
404 View Not Found
```

Because Spring tries to locate:

```text
user.jsp
```

---

# How to Fix?

Either:

```java
@RestController
```

OR:

```java
@Controller
@ResponseBody
```

---

# Interview Insight

Use:

- @Controller -> UI rendering
- @RestController -> REST APIs
```