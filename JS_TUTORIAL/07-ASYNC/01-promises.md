# Promises and Async/Await

Promises and async/await are essential for handling asynchronous operations in JavaScript like API calls, file operations, and timers.

## Table of Contents
- [Understanding Asynchronous Code](#understanding-asynchronous-code)
- [Promises](#promises)
- [Promise Chaining](#promise-chaining)
- [Async/Await](#asyncawait)
- [Error Handling in Async](#error-handling-in-async)
- [Promise Methods](#promise-methods)
- [Practical Examples](#practical-examples)
- [Exercises](#exercises)

---

## Understanding Asynchronous Code

JavaScript is single-threaded but supports asynchronous operations through callbacks, promises, and async/await.

### Synchronous Code (Blocking)
```javascript
console.log('Start');

function slowOperation() {
  for (let i = 0; i < 1000000000; i++) {}
  return 'Done';
}

console.log(slowOperation());
console.log('End');
```

### Asynchronous Code (Non-Blocking)
```javascript
console.log('Start');

setTimeout(() => {
  console.log('After delay');
}, 1000);

console.log('End');
```

---

## Promises

A Promise represents an eventual result (or failure) of an asynchronous operation.

### Creating a Promise
```javascript
const myPromise = new Promise((resolve, reject) => {
  if (Math.random() > 0.5) {
    resolve('Success!');
  } else {
    reject('Error!');
  }
});
```

### Using .then() and .catch()
```javascript
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve('Success!');
  }, 1000);
});

promise
  .then(result => console.log(result))
  .catch(error => console.log('Error:', error))
  .finally(() => console.log('Done'));
```

### Real World: Fetch
```javascript
fetch('https://api.example.com/user/1')
  .then(response => response.json())
  .then(data => console.log('User:', data))
  .catch(error => console.error('Error:', error));
```

---

## Promise Chaining

```javascript
function step1() {
  return new Promise(resolve => {
    setTimeout(() => resolve('Step 1'), 1000);
  });
}

step1()
  .then(result => {
    console.log(result);
    return 'Step 2';
  })
  .then(result => {
    console.log(result);
    return 'Step 3';
  })
  .then(result => console.log(result));
```

---

## Async/Await

Async/await makes asynchronous code look synchronous.

### Basic Async Function
```javascript
async function greet() {
  return 'Hello!';
}

greet().then(result => console.log(result));
```

### Using Await
```javascript
async function example() {
  console.log('Start');
  await new Promise(resolve => setTimeout(resolve, 1000));
  console.log('After 1 second');
}

example();
```

### Fetching with Async/Await
```javascript
async function getUser(userId) {
  try {
    const response = await fetch(`/api/users/${userId}`);
    const user = await response.json();
    return user;
  } catch (error) {
    console.error('Error:', error);
  }
}
```

---

## Error Handling in Async

### Try...Catch
```javascript
async function fetchData() {
  try {
    const response = await fetch('/api/data');
    const data = await response.json();
    return data;
  } catch (error) {
    console.error('Error:', error);
    return null;
  }
}
```

### Try...Catch...Finally
```javascript
async function operation() {
  try {
    const data = await fetch('/api/data').then(r => r.json());
    console.log(data);
  } catch (error) {
    console.error('Error:', error);
  } finally {
    console.log('Done');
  }
}
```

---

## Promise Methods

### Promise.all()
```javascript
const promise1 = fetch('/api/users').then(r => r.json());
const promise2 = fetch('/api/posts').then(r => r.json());

Promise.all([promise1, promise2])
  .then(([users, posts]) => {
    console.log('Data loaded');
  })
  .catch(error => console.error(error));
```

### Promise.race()
```javascript
Promise.race([
  new Promise(resolve => setTimeout(() => resolve('First'), 500)),
  new Promise(resolve => setTimeout(() => resolve('Second'), 100))
])
  .then(result => console.log(result)); // Second
```

### Promise.allSettled()
```javascript
Promise.allSettled([
  Promise.resolve('Success'),
  Promise.reject('Error'),
  Promise.resolve('OK')
])
  .then(results => console.log(results));
```

---

## Practical Examples

### Sequential Calls
```javascript
async function getUserWithPosts(userId) {
  const user = await fetch(`/api/users/${userId}`).then(r => r.json());
  const posts = await fetch(`/api/users/${userId}/posts`).then(r => r.json());
  return { user, posts };
}
```

### Parallel Calls
```javascript
async function getUserDataFull(userId) {
  const [userRes, postsRes] = await Promise.all([
    fetch(`/api/users/${userId}`),
    fetch(`/api/users/${userId}/posts`)
  ]);
  
  const [user, posts] = await Promise.all([
    userRes.json(),
    postsRes.json()
  ]);
  
  return { user, posts };
}
```

### Retry Logic
```javascript
async function fetchWithRetry(url, maxRetries = 3) {
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fetch(url).then(r => r.json());
    } catch (error) {
      if (i === maxRetries - 1) throw error;
      await new Promise(resolve => setTimeout(resolve, 1000));
    }
  }
}
```

---

## Exercises

### Exercise 1: Create a Timer Promise
Create a promise that resolves after specified seconds.

**Solution:**
```javascript
function timer(seconds) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(`Timer completed: ${seconds}s`);
    }, seconds * 1000);
  });
}

timer(2).then(result => console.log(result));
```

### Exercise 2: Async Factorial
Create an async function to calculate factorial with delays.

**Solution:**
```javascript
async function asyncFactorial(n) {
  if (n <= 1) return 1;
  await new Promise(resolve => setTimeout(resolve, 100));
  return n * await asyncFactorial(n - 1);
}

asyncFactorial(5).then(result => console.log(result));
```

---

## Next Steps

→ [Back to Async](./README.md)
