# Closures and Scope in JavaScript

Understanding closures and scope is crucial for writing robust JavaScript code. This covers the most important concepts in JavaScript.

## Table of Contents
- [Scope Basics](#scope-basics)
- [Lexical Scope](#lexical-scope)
- [Function Scope](#function-scope)
- [Block Scope](#block-scope)
- [Closures](#closures)
- [This Keyword](#this-keyword)
- [Hoisting](#hoisting)
- [Exercises](#exercises)

---

## Scope Basics

Scope determines the accessibility of variables and functions.

### Global Scope
```javascript
// Global scope - accessible everywhere
const globalVar = 'I am global';

function myFunction() {
  console.log(globalVar); // Can access global variable
}

myFunction(); // I am global
console.log(globalVar); // I am global
```

### Function Scope
```javascript
function outer() {
  const outerVar = 'I am in outer function';
  
  function inner() {
    console.log(outerVar); // Can access outer's variable
  }
  
  inner();
}

outer(); // I am in outer function
// console.log(outerVar); // Error - not accessible here
```

### Local Scope
```javascript
function myFunction() {
  const localVar = 'I am local';
  console.log(localVar); // Can access
}

myFunction(); // I am local
// console.log(localVar); // Error - localVar is not defined
```

---

## Lexical Scope

Functions are executed using the variable scope that was in effect when they were defined, not when they're called.

```javascript
const globalName = 'Global';

function outer() {
  const name = 'Outer';
  
  function inner() {
    console.log(name); // Looks for 'name' in its scope chain
  }
  
  return inner;
}

const innerFunc = outer();
innerFunc(); // Outer (uses the scope where inner was defined)
```

**Scope Chain:**
```javascript
// The JavaScript engine looks for variables in this order:
// 1. Local scope
// 2. Parent scope (enclosing functions)
// 3. Global scope

const a = 'global';

function first() {
  const a = 'first';
  
  function second() {
    const a = 'second';
    
    function third() {
      console.log(a); // Uses variable from third's parent scope first
    }
    
    third();
  }
  
  second();
}

first(); // second
```

---

## Function Scope

Variables declared in a function are local to that function only.

```javascript
function test() {
  var x = 1;
  let y = 2;
  const z = 3;
  
  console.log(x, y, z); // 1, 2, 3
}

test();
// console.log(x); // Error
// console.log(y); // Error
// console.log(z); // Error
```

### var vs let vs const in Function Scope

```javascript
// var - function scoped (can be reassigned and redeclared)
function varExample() {
  if (true) {
    var x = 1;
  }
  console.log(x); // 1 (accessible outside block!)
}
varExample();

// let - block scoped (can be reassigned but not redeclared)
function letExample() {
  if (true) {
    let y = 2;
  }
  // console.log(y); // Error - y is not defined
}
letExample();

// const - block scoped (cannot be reassigned or redeclared)
function constExample() {
  if (true) {
    const z = 3;
  }
  // console.log(z); // Error - z is not defined
}
constExample();
```

---

## Block Scope

let and const are block scoped, meaning they're only accessible within their block.

```javascript
{
  const x = 1;
  let y = 2;
  console.log(x, y); // 1, 2
}

// console.log(x); // Error
// console.log(y); // Error
```

### For Loop Scope
```javascript
// var - same variable in all iterations
for (var i = 0; i < 3; i++) {
  setTimeout(() => console.log('var:', i), 0);
}
// Output: var: 3, var: 3, var: 3

// let - new variable for each iteration
for (let j = 0; j < 3; j++) {
  setTimeout(() => console.log('let:', j), 0);
}
// Output: let: 0, let: 1, let: 2
```

---

## Closures

A closure is a function that has access to variables from its outer scope even after that function has finished executing.

### Basic Closure
```javascript
function outer() {
  const outerVar = 'I am outer';
  
  function inner() {
    console.log(outerVar);
  }
  
  return inner;
}

const myFunc = outer();
myFunc(); // I am outer
```

### Practical Closure Example
```javascript
function counter() {
  let count = 0; // Private variable
  
  return {
    increment: function() {
      count++;
      return count;
    },
    decrement: function() {
      count--;
      return count;
    },
    getCount: function() {
      return count;
    }
  };
}

const myCounter = counter();
console.log(myCounter.increment()); // 1
console.log(myCounter.increment()); // 2
console.log(myCounter.decrement()); // 1
console.log(myCounter.getCount());  // 1
```

### Creating Private Variables
```javascript
function createBankAccount(initialBalance) {
  let balance = initialBalance; // Private variable
  
  return {
    deposit: function(amount) {
      balance += amount;
      return `Balance: $${balance}`;
    },
    withdraw: function(amount) {
      if (amount > balance) {
        return 'Insufficient funds';
      }
      balance -= amount;
      return `Balance: $${balance}`;
    },
    getBalance: function() {
      return balance;
    }
  };
}

const account = createBankAccount(1000);
console.log(account.deposit(500));   // Balance: $1500
console.log(account.withdraw(200));  // Balance: $1300
console.log(account.getBalance());   // 1300
// console.log(account.balance);      // undefined - balance is private!
```

### Closure in Loops
```javascript
// ❌ Problem - all functions refer to the same i
const functions = [];
for (var i = 0; i < 3; i++) {
  functions.push(function() {
    console.log(i);
  });
}
functions[0](); // 3
functions[1](); // 3
functions[2](); // 3

// ✅ Solution 1 - use let (block scope)
const functions2 = [];
for (let i = 0; i < 3; i++) {
  functions2.push(function() {
    console.log(i);
  });
}
functions2[0](); // 0
functions2[1](); // 1
functions2[2](); // 2

// ✅ Solution 2 - IIFE (Immediately Invoked Function Expression)
const functions3 = [];
for (var i = 0; i < 3; i++) {
  functions3.push((function(j) {
    return function() {
      console.log(j);
    };
  })(i));
}
functions3[0](); // 0
functions3[1](); // 1
functions3[2](); // 2
```

### Module Pattern
```javascript
const userModule = (function() {
  // Private variables
  let users = [];
  let nextId = 1;
  
  // Private function
  function findUserById(id) {
    return users.find(user => user.id === id);
  }
  
  // Public methods (exposed through return)
  return {
    addUser: function(name) {
      const user = { id: nextId++, name };
      users.push(user);
      return user;
    },
    getUser: function(id) {
      return findUserById(id);
    },
    getAllUsers: function() {
      return users;
    },
    deleteUser: function(id) {
      users = users.filter(u => u.id !== id);
    }
  };
})();

userModule.addUser('John');
userModule.addUser('Jane');
console.log(userModule.getAllUsers());
// [{ id: 1, name: 'John' }, { id: 2, name: 'Jane' }]
```

---

## This Keyword

The `this` keyword refers to the object that is executing the current function.

### Global Context
```javascript
console.log(this); // Window (browser) or global (Node.js)

function test() {
  console.log(this); // Window or global
}
test();
```

### Object Method Context
```javascript
const person = {
  name: 'John',
  greet: function() {
    console.log(`Hi, I'm ${this.name}`);
  }
};

person.greet(); // Hi, I'm John
```

### Constructor Function Context
```javascript
function Person(name) {
  this.name = name;
  this.introduce = function() {
    console.log(`I'm ${this.name}`);
  };
}

const john = new Person('John');
john.introduce(); // I'm John
```

### Call, Apply, Bind
```javascript
function greet(greeting, punctuation) {
  return `${greeting}, I'm ${this.name}${punctuation}`;
}

const person = { name: 'Alice' };

// call - invoke immediately with specific this and arguments
console.log(greet.call(person, 'Hello', '!')); // Hello, I'm Alice!

// apply - like call but arguments as array
console.log(greet.apply(person, ['Hi', '.'])); // Hi, I'm Alice.

// bind - returns new function with bound this
const greetAlice = greet.bind(person);
console.log(greetAlice('Hey', '!')); // Hey, I'm Alice!
```

### Arrow Functions and this
```javascript
const person = {
  name: 'John',
  greet: function() {
    console.log(this.name); // John
  },
  greetArrow: () => {
    console.log(this); // global object (arrow functions don't have their own this)
  },
  method: function() {
    const inner = () => {
      console.log(this.name); // John (inherits this from outer function)
    };
    inner();
  }
};

person.greet();      // John
person.greetArrow(); // undefined
person.method();     // John
```

---

## Hoisting

Hoisting is JavaScript's behavior of moving declarations to the top of their scope before code execution.

### var Hoisting
```javascript
console.log(x); // undefined (not error!)
var x = 5;
console.log(x); // 5

// This is what actually happens:
// var x;
// console.log(x); // undefined
// x = 5;
// console.log(x); // 5
```

### let and const Hoisting
```javascript
// console.log(y); // ReferenceError - Temporal Dead Zone
let y = 5;
console.log(y); // 5

// const has same behavior
// console.log(z); // ReferenceError
const z = 10;
console.log(z); // 10
```

### Function Hoisting
```javascript
// Function declarations are fully hoisted
console.log(add(2, 3)); // 5

function add(a, b) {
  return a + b;
}

// Function expressions are NOT hoisted
console.log(multiply(2, 3)); // Error - multiply is not a function

const multiply = function(a, b) {
  return a * b;
};
```

---

## Practical Examples

### Function Factory
```javascript
function createMultiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = createMultiplier(2);
const triple = createMultiplier(3);

console.log(double(5)); // 10
console.log(triple(5)); // 15
```

### Memoization
```javascript
function memoize(fn) {
  const cache = {};
  
  return function(...args) {
    const key = JSON.stringify(args);
    
    if (key in cache) {
      console.log('From cache:', key);
      return cache[key];
    }
    
    console.log('Computing:', key);
    const result = fn(...args);
    cache[key] = result;
    return result;
  };
}

function expensiveCalculation(n) {
  let sum = 0;
  for (let i = 0; i < n; i++) {
    sum += i;
  }
  return sum;
}

const memoizedCalc = memoize(expensiveCalculation);
console.log(memoizedCalc(1000)); // Computing, result
console.log(memoizedCalc(1000)); // From cache
```

---

## Exercises

### Exercise 1: Create a Secret Keeper
Create a function that keeps values secret and only allows getting/setting them.

**Solution:**
```javascript
function createSecretKeeper(secret) {
  let value = secret;
  
  return {
    getSecret: () => value,
    setSecret: (newSecret) => {
      value = newSecret;
    }
  };
}

const keeper = createSecretKeeper('My secret');
console.log(keeper.getSecret()); // My secret
keeper.setSecret('New secret');
console.log(keeper.getSecret()); // New secret
```

### Exercise 2: Create a Throttle Function
Create a function that limits how often another function can be called.

**Solution:**
```javascript
function throttle(fn, delay) {
  let lastCall = 0;
  
  return function(...args) {
    const now = Date.now();
    if (now - lastCall >= delay) {
      lastCall = now;
      return fn(...args);
    }
  };
}

const log = (msg) => console.log(msg);
const throttledLog = throttle(log, 1000);

throttledLog('Call 1'); // logs immediately
throttledLog('Call 2'); // ignored (less than 1000ms)
throttledLog('Call 3'); // ignored
setTimeout(() => throttledLog('Call 4'), 1100); // logs after 1100ms
```

---

## Next Steps

→ [Back to Functions](./README.md)  
→ [Object-Oriented Programming](../06-OOP/README.md)
