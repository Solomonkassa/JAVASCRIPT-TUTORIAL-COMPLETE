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

---

## Learning Path

```
Callbacks → Promises → Async/Await 
→ Fetch API → Error Handling → Promise Methods
```

**Why Async Matters**:
- Network requests
- File operations
- Database queries
- Timers
- User interactions

**Start with**: [Callbacks](./01-callbacks.md)

---

[← Back to Main](../README.md) | [DOM & Events →](../08-DOM-EVENTS/README.md)
