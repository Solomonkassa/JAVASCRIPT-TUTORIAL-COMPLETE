# Variables and Data Types

The foundation of JavaScript programming - how to store and work with data.

## What is a Variable?

A variable is a named container that holds a value. Think of it as a labeled box where you store information.

```javascript
// Create a variable and assign a value
let age = 25;
console.log(age);  // Output: 25
```

## Three Ways to Declare Variables

### 1. `let` (Recommended for modern JavaScript)

Used for variables that change. Block-scoped (only exists within `{}`).

```javascript
let name = "Alice";
name = "Bob";  // Can be reassigned
console.log(name);  // Output: Bob

let x;  // Can declare without initial value
console.log(x);  // Output: undefined
```

**Characteristics:**
- Can be reassigned ✅
- Block-scoped ✅
- Cannot be redeclared in same scope ❌
- Recommended for modern code ✅

### 2. `const` (Default choice)

Used for variables that don't change. Block-scoped.

```javascript
const pi = 3.14159;
// pi = 3.14;  // ❌ Error! Cannot reassign

const person = { name: "Alice", age: 25 };
person.age = 26;  // ✅ OK! (Modifying object properties)
```

**Characteristics:**
- Cannot be reassigned ✅
- Block-scoped ✅
- Must be initialized ✅
- Preferred in modern code ✅

### 3. `var` (Old way - avoid)

Used before `let` and `const`. Function-scoped.

```javascript
var count = 0;
count = 1;  // Can be reassigned
var count = 2;  // Can be redeclared (confusing!)

function test() {
    var x = 10;
}
console.log(x);  // ❌ Error! x doesn't exist here
```

**Avoid `var` in modern JavaScript!** Use `let` and `const` instead.

---

## JavaScript Data Types

JavaScript has 8 main data types:

### Primitive Types (7 types)

#### 1. **Number**
Represents numeric values (integers and decimals).

```javascript
let age = 25;
let height = 5.9;
let temperature = -10;
let infinity = Infinity;
let notANumber = NaN;  // "Not a Number"

console.log(typeof age);  // Output: "number"
console.log(typeof notANumber);  // Output: "number" (quirk!)
```

#### 2. **String**
Represents text data.

```javascript
let firstName = "Alice";
let lastName = 'Bob';
let message = `Hello, World!`;  // Template literal (modern)

console.log(typeof firstName);  // Output: "string"
console.log(firstName.length);  // Output: 5
```

#### 3. **Boolean**
Represents true or false.

```javascript
let isActive = true;
let isLoggedIn = false;
let hasAccess = age >= 18;

console.log(typeof isActive);  // Output: "boolean"
```

#### 4. **Undefined**
A variable that has been declared but not assigned a value.

```javascript
let x;
console.log(x);  // Output: undefined
console.log(typeof x);  // Output: "undefined"
```

#### 5. **Null**
Intentional absence of a value (must be assigned).

```javascript
let user = null;  // Explicitly set to null
console.log(typeof user);  // Output: "object" (historical quirk!)
```

#### 6. **Symbol**
Unique and immutable identifier (advanced).

```javascript
const id = Symbol("userId");
console.log(typeof id);  // Output: "symbol"
```

#### 7. **BigInt**
For very large numbers beyond Number limits.

```javascript
let bigNumber = 123456789012345678901234567890n;
console.log(typeof bigNumber);  // Output: "bigint"
```

### Complex Type (1 type)

#### 8. **Object**
A collection of key-value pairs. Arrays are also objects!

```javascript
// Object
let person = {
    name: "Alice",
    age: 25,
    city: "New York"
};
console.log(typeof person);  // Output: "object"

// Array (special object)
let fruits = ["apple", "banana", "orange"];
console.log(typeof fruits);  // Output: "object"
```

---

## Quick Type Reference

```javascript
// Numbers
let integer = 42;
let decimal = 3.14;
let negative = -10;
let veryBig = 1e10;  // 10000000000

// Strings
let text = "Hello";
let empty = "";
let quote = 'It\'s cool';

// Booleans
let yes = true;
let no = false;

// Special values
let nothing = undefined;
let empty_value = null;

// Objects
let obj = { key: "value" };
let arr = [1, 2, 3];
```

---

## Naming Variables (Conventions)

```javascript
// ✅ Good names (camelCase for variables)
let userName = "Alice";
let maxAttempts = 5;
let isReady = true;

// ✅ Good names (UPPER_CASE for constants)
const MAX_USERS = 100;
const API_KEY = "secret";

// ❌ Bad names
let x = 25;  // Not descriptive
let data = "Alice";  // Too vague
let 123abc = "invalid";  // Starts with number
let user-name = "Alice";  // Hyphens not allowed
```

---

## Important Concepts

### Scope
Where a variable is accessible.

```javascript
let global = "I'm global";

function myFunction() {
    let local = "I'm local";
    console.log(global);  // ✅ Works
    console.log(local);   // ✅ Works
}

myFunction();
console.log(global);  // ✅ Works
console.log(local);   // ❌ Error! Not defined outside function
```

### Reassignment vs Redeclaration

```javascript
let name = "Alice";
name = "Bob";  // Reassignment ✅

let name = "Charlie";  // Redeclaration ❌ Error

const age = 25;
age = 26;  // ❌ Error! Cannot reassign const
```

---

## Practice Exercises

### Exercise 1: Create Variables
```javascript
// Create these variables using const/let:
// 1. Your name (string)
// 2. Your age (number)
// 3. A boolean for if you like JavaScript
// 4. Then print all of them

const myName = "Your Name";
const myAge = 25;
const likeJS = true;
console.log(myName, myAge, likeJS);
```

### Exercise 2: Type Detection
```javascript
// Identify the type of each value:
console.log(typeof 42);           // ?
console.log(typeof "hello");      // ?
console.log(typeof true);         // ?
console.log(typeof undefined);    // ?
console.log(typeof [1, 2, 3]);    // ?
console.log(typeof { name: "Alice" });  // ?

// Answers shown at end of this file
```

### Exercise 3: Scope Challenge
```javascript
// What will each console.log print?
let a = 1;
{
    let a = 2;
    console.log(a);  // What prints?
}
console.log(a);  // What prints?
```

---

## Solutions to Exercises

```javascript
// Exercise 2 Answers:
console.log(typeof 42);           // "number"
console.log(typeof "hello");      // "string"
console.log(typeof true);         // "boolean"
console.log(typeof undefined);    // "undefined"
console.log(typeof [1, 2, 3]);    // "object" (arrays are objects)
console.log(typeof { name: "Alice" });  // "object"

// Exercise 3 Answer:
// First console.log prints: 2 (the local 'a')
// Second console.log prints: 1 (the outer 'a')
```

---

## Key Takeaways

✅ Use `const` by default, `let` when you need to reassign  
✅ Avoid `var` in modern JavaScript  
✅ Understand the 8 data types JavaScript provides  
✅ Use descriptive variable names  
✅ Understand scope - where variables are accessible  

---

## 📚 Resources

### Documentation
- **MDN: Variables**: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables
- **MDN: Data Types**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures

### Video Tutorials
- **Variables & Data Types by Traversy Media**: https://www.youtube.com/watch?v=9WIWNJVvPEM
- **JavaScript Data Types explained by Academind**: https://www.youtube.com/watch?v=qw3j0A3DIzQ

### Interactive Practice
- **Codecademy: Variables**: https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-variables
- **Scrimba JavaScript Basics**: https://scrimba.com/learn/javascript

---

**Next**: [Operators](./02-operators.md)  
**Back**: [← Fundamentals Index](./README.md)
