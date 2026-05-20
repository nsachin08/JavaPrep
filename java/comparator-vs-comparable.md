# Comparator vs Comparable

# Comparable

Comparable defines:

```text
Natural ordering
```

Class itself defines sorting logic.

---

# Syntax

```java
class Employee implements Comparable<Employee> {

    int salary;

    @Override
    public int compareTo(Employee e) {
        return this.salary - e.salary;
    }
}
```

---

# Comparator

Comparator defines:

```text
Custom external sorting logic
```

---

# Syntax

```java
Comparator<Employee> bySalary =
    (a, b) -> a.salary - b.salary;
```

---

# Key Differences

| Feature | Comparable | Comparator |
|---|---|---|
| Package | java.lang | java.util |
| Sorting Logic | Inside class | Outside class |
| Method | compareTo() | compare() |
| Multiple Sorts | Difficult | Easy |
| Modification Needed | Yes | No |

---

# Can Comparable Have Multiple Sorting Logics?

NO.

A class can only have one compareTo() implementation.

Example:

```java
compareTo()
```

can sort only by:

- salary
OR
- name
OR
- id

Not all simultaneously.

---

# How Comparator Solves This

We can create multiple comparators.

---

# Sort by Salary

```java
Comparator<Employee> bySalary =
    (a, b) -> a.salary - b.salary;
```

---

# Sort by Name

```java
Comparator<Employee> byName =
    (a, b) -> a.name.compareTo(b.name);
```

---

# Sort by Designation

```java
Comparator<Employee> byDesignation =
    (a, b) -> a.designation.compareTo(b.designation);
```

---

# Real Interview Insight

Use:

- Comparable for natural/default sorting
- Comparator for flexible business sorting

Most real applications use Comparator more frequently.