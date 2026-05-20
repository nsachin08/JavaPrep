# Circuit Breaker in Microservices

# What is Circuit Breaker?

Circuit breaker is a resilience pattern.

It prevents applications from repeatedly calling:

```text
A failing downstream service
```

---

# Real Production Scenario

Suppose:

```text
Order Service -> Payment Service
```

Payment service becomes slow.

Without circuit breaker:

- all threads wait
- request queue increases
- thread pool exhausts
- whole application slows down

This causes:

```text
Cascading failure
```

---

# How Circuit Breaker Works

# CLOSED State

Normal operation.

Requests pass through.

---

# OPEN State

If failures exceed threshold:

```text
Circuit opens
```

Requests fail immediately.

Fallback response returned.

Example:

```text
"Payment service temporarily unavailable"
```

This protects system resources.

---

# HALF-OPEN State

After cooldown period:

- limited requests allowed
- if successful -> CLOSED
- if failure continues -> OPEN again

---

# Why Circuit Breaker is Important

Benefits:

- prevents thread exhaustion
- avoids cascading failures
- improves resilience
- protects downstream systems
- faster recovery

---

# Popular Libraries

## Resilience4j

Most popular modern library.

---

## Hystrix

Netflix library.

Now deprecated.

---

# Example Using Resilience4j

```java
@CircuitBreaker(name = "payment-service",
                fallbackMethod = "fallback")
public String processPayment() {
    return paymentClient.call();
}

# Important Interview Insight

Circuit breaker does NOT fix failing services.

It:

```text
Prevents entire system collapse
```