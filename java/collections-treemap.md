```md
# TreeMap Internals

# 1. What is TreeMap?

TreeMap is a NavigableMap implementation based on:

```text
Red-Black Tree
```

It stores entries in sorted order.

---

# Important Characteristics

| Feature | TreeMap |
|---|---|
| Ordering | Sorted |
| Duplicate Keys | Not Allowed |
| Duplicate Values | Allowed |
| Null Keys | Not Allowed |
| Time Complexity | O(log n) |

---

# Internal Working

TreeMap internally uses:

```text
Self-balancing Red-Black Tree
```

Operations:

- put() -> O(log n)
- get() -> O(log n)
- remove() -> O(log n)

Because the tree always remains balanced.

---

# Can We Store Duplicate Values?

YES.

```java
TreeMap<Integer, String> map = new TreeMap<>();

map.put(1, "Java");
map.put(2, "Java");
```

Values can repeat.

---

# Can We Store Duplicate Keys?

NO.

If same key inserted:

```java
map.put(1, "A");
map.put(1, "B");
```

Old value gets replaced.

---

# Can We Store Custom Objects as Keys?

YES.

But sorting logic must exist.

Either:

- implement Comparable
OR
- provide Comparator

---

# Example Using Comparable

```java
class Employee implements Comparable<Employee> {

    int id;

    Employee(int id) {
        this.id = id;
    }

    @Override
    public int compareTo(Employee e) {
        return this.id - e.id;
    }
}
```

---

# Example Using Comparator

```java
TreeMap<Employee, String> map =
    new TreeMap<>((a, b) -> a.id - b.id);
```

---

# Why TreeMap Cannot Work Without Sorting Logic?

Because Red-Black Tree requires ordering.

TreeMap must know:

```text
Which node goes left?
Which node goes right?
```

Hence comparison is mandatory.
