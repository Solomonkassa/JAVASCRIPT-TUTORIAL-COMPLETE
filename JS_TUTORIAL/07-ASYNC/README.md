# Asynchronous JavaScript: Non-Blocking Code

Master handling operations that take time to complete.

## Topics Covered

1. **[Callbacks](./01-callbacks.md)** - Functions as callbacks
2. **[Promises](./02-promises.md)** - Better than callbacks
3. **[Async/Await](./03-async-await.md)** - Modern async syntax
4. **[Fetch API](./04-fetch-api.md)** - Making HTTP requests
5. **[Error Handling](./05-error-handling.md)** - try/catch in async code
6. **[Promise Methods](./06-promise-methods.md)** - Promise.all, Promise.race

## Quick Reference

### Callbacks
```javascript
function getData(callback) {
    setTimeout(() => {
        callback("Data loaded");
    }, 1000);
}

getData((data) => console.log(data));
```

### Promises
```javascript
const promise = new Promise((resolve, reject) => {
    setTimeout(() => resolve("Done"), 1000);
});

promise.then(result => console.log(result));
```

### Async/Await
```javascript
async function fetchData() {
    const response = await fetch("/api/data");
    const data = await response.json();
    return data;
}
```

## Why Asynchronous Programming?

JavaScript is **single-threaded**, meaning:
- Only one thing executes at a time
- Without async, program waits for everything (blocking)
- Async allows other code to run while waiting for results

**Real-world example:** 
Imagine ordering coffee and waiting at counter (synchronous) vs. ordering and getting a buzzer (asynchronous)

## Promise States

```
Pending → Resolved (with value)  ← Fulfilled
       → Rejected (with reason)  ← Error
```

## Common Async Patterns

**Sequential execution (one after another):**
```javascript
async function sequential() {
  const user = await fetchUser();
  const posts = await fetchPosts(user.id);
  const comments = await fetchComments(posts[0].id);
  return comments;
}
```

**Parallel execution (all at once):**
```javascript
async function parallel() {
  const [users, posts, comments] = await Promise.all([
    fetchUsers(),
    fetchPosts(),
    fetchComments()
  ]);
  return { users, posts, comments };
}
```

**Error handling:**
```javascript
async function safefetch() {
  try {
    const data = await fetch("/api/data").then(r => r.json());
    return data;
  } catch (error) {
    console.log("Error:", error);
    return null;
  }
}
```

## Learning Path

```
Callbacks → Promises → Async/Await 
→ Fetch API → Error Handling → Promise Methods
```

## Key Concepts

- **Blocking**: Code waits for operation to complete
- **Non-blocking**: Code continues, result handled later
- **Callback**: Function called when operation completes
- **Promise**: Object representing future value
- **Async/Await**: Cleaner promise syntax
- **Event Loop**: How JavaScript handles async operations

## Real-World Use Cases

- Fetching data from APIs
- Reading files
- Database operations
- Timer operations
- Animation frames
- User input handling

## Timing Comparison

| Method | When | Use Case |
|--------|------|----------|
| Callback | Operation completes | Simple operations |
| Promise | Future value needed | Better readability |
| Async/Await | Multiple operations | Cleanest syntax |

## Common Mistakes to Avoid

- Forgetting to `await` in async functions
- Using `.then()` in async functions unnecessarily
- Not handling promise rejections (unhandled rejections)
- Creating callback hell (deeply nested callbacks)
- Not understanding the event loop
- Using sync code when async is needed

## Performance Tips

- Use `Promise.all()` for parallel operations
- Avoid sequential awaits when you can parallelize
- Cache API responses to avoid repeated requests
- Use debouncing for frequently-called async functions
- Consider race conditions in concurrent operations

## Practice Exercises

1. Create a function that fetches user data with error handling
2. Build a function that waits for multiple API calls to complete
3. Create a retry mechanism for failed API calls
4. Implement request timeout functionality
5. Build a simple data loading animation with promises
6. Create functions for sequential and parallel execution

## Advanced Topics

- Promise cancellation (AbortController)
- Request timeouts
- Retry logic with exponential backoff
- Request caching strategies
- WebSocket for real-time communication
- Service Workers and offline handling

---

**Why Async Matters**:
- Network requests
- File operations
- Database queries
- Timers
- User interactions
- Modern web development depends on async

**Start with**: [Promises & Async/Await](./01-promises.md)

---

**Course Section**: Asynchronous JavaScript - Non-Blocking Code  
**Author**: Solomon Kassa  
**Last Updated**: February 2026  
**Difficulty**: Intermediate-Advanced  
**Prerequisites**: Fundamentals, Functions, Objects & Arrays, OOP basics  
**Next**: DOM & Events section

---

[← Back to Main](../README.md) | [DOM & Events →](../08-DOM-EVENTS/README.md)
