# Function Basics: Creating and Using Functions

Learn how to create and use reusable code blocks.

## What is a Function?

A function is a reusable block of code that performs a specific task.

```javascript
// Function declaration
function sayHello() {
    console.log("Hello, World!");
}

// Call the function
sayHello();  // Output: "Hello, World!"
sayHello();  // Output: "Hello, World!"
```

Why use functions?
- **Reusability** - Write once, use many times
- **Organization** - Group related code
- **Maintainability** - Easier to update and fix
- **Readability** - Code is clearer with function names

---

## Function Declaration

The most common way to create a function.

```javascript
// Syntax
function functionName() {
    // Code to execute
}

// Example
function greet() {
    console.log("Welcome to JavaScript!");
}

// Call it
greet();
```

### With Curly Braces

```javascript
function printNumbers() {
    console.log(1);
    console.log(2);
    console.log(3);
}

printNumbers();
// Output:
// 1
// 2
// 3
```

---

## Function Expression

Assign a function to a variable.

```javascript
// Function expression
const add = function() {
    return 5 + 3;
};

console.log(add());  // 8

// Anonymous function (no name)
const multiply = function(a, b) {
    return a * b;
};

console.log(multiply(4, 5));  // 20
```

### Named Function Expression

```javascript
const factorial = function fact(n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
};

console.log(factorial(5));  // 120
```

---

## Arrow Functions (Modern)

Shorter syntax introduced in ES6.

```javascript
// Single expression
const square = (x) => x * x;
console.log(square(5));  // 25

// Multiple lines need braces and return
const add = (a, b) => {
    const sum = a + b;
    return sum;
};
console.log(add(3, 4));  // 7

// Single parameter (parentheses optional)
const double = x => x * 2;
console.log(double(5));  // 10

// No parameters
const getPI = () => 3.14159;
console.log(getPI());  // 3.14159
```

---

## Calling Functions

Different ways to invoke functions.

```javascript
// Basic function call
function sayHi() {
    console.log("Hi!");
}
sayHi();

// Store result in variable
function add(a, b) {
    return a + b;
}
const result = add(5, 3);
console.log(result);  // 8

// Use directly in expression
console.log(add(2, 3) * 2);  // 10

// Multiple times
sayHi();
sayHi();
sayHi();
```

---

## Parameters and Arguments

### Basic Parameters

```javascript
// Define parameters
function greet(name) {
    console.log(`Hello, ${name}!`);
}

// Pass arguments
greet("Alice");   // Output: "Hello, Alice!"
greet("Bob");     // Output: "Hello, Bob!"
```

### Multiple Parameters

```javascript
function add(a, b) {
    return a + b;
}

console.log(add(5, 3));      // 8
console.log(add(100, 50));   // 150
```

### Default Parameters

```javascript
// Set default values
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}

greet();           // "Hello, Guest!"
greet("Alice");    // "Hello, Alice!"
```

### Rest Parameters

```javascript
// Accept any number of arguments
function sum(...numbers) {
    let total = 0;
    for (let num of numbers) {
        total += num;
    }
    return total;
}

console.log(sum(1, 2, 3));        // 6
console.log(sum(1, 2, 3, 4, 5));  // 15
```

---

## Return Statements

Send data back from a function.

```javascript
// Return a value
function multiply(a, b) {
    return a * b;
}

let result = multiply(4, 5);
console.log(result);  // 20

// Function without return gives undefined
function test() {
    console.log("No return");
}

let x = test();
console.log(x);  // undefined
```

### Early Return

```javascript
function isAdult(age) {
    if (age < 0) {
        return "Invalid age";
    }
    if (age < 18) {
        return false;
    }
    return true;
}

console.log(isAdult(25));   // true
console.log(isAdult(15));   // false
console.log(isAdult(-5));   // "Invalid age"
```

### Returning Multiple Values

```javascript
// Return an array
function getCoordinates() {
    return [10, 20];
}

const [x, y] = getCoordinates();
console.log(x, y);  // 10 20

// Return an object
function getUserInfo() {
    return {
        name: "Alice",
        age: 25,
        email: "alice@example.com"
    };
}

const user = getUserInfo();
console.log(user.name);  // "Alice"
```

---

## Hoisting

Functions are hoisted (moved to top of scope).

```javascript
// This works even though it's called before declaration
sayHi();  // "Hello!"

function sayHi() {
    console.log("Hello!");
}

// BUT: Function expressions are NOT hoisted
greet();  // ❌ Error: Cannot access 'greet' before initialization

const greet = function() {
    console.log("Hi!");
};
```

---

## Scope

Functions have their own scope.

```javascript
let globalVar = "I'm global";

function myFunction() {
    let localVar = "I'm local";
    console.log(globalVar);   // ✅ Can access global
    console.log(localVar);    // ✅ Can access local
}

myFunction();
console.log(globalVar);   // ✅ Works
console.log(localVar);    // ❌ Error!
```

---

## Practical Examples

### Temperature Converter

```javascript
function celsiusToFahrenheit(celsius) {
    return (celsius * 9/5) + 32;
}

console.log(celsiusToFahrenheit(0));    // 32
console.log(celsiusToFahrenheit(100));  // 212
```

### Check if Number is Prime

```javascript
function isPrime(num) {
    if (num <= 1) return false;
    if (num <= 3) return true;
    if (num % 2 === 0 || num % 3 === 0) return false;
    
    for (let i = 5; i * i <= num; i += 6) {
        if (num % i === 0 || num % (i + 2) === 0) {
            return false;
        }
    }
    return true;
}

console.log(isPrime(7));   // true
console.log(isPrime(10));  // false
console.log(isPrime(17));  // true
```

### Calculate Bill with Tip

```javascript
function calculateTotal(bill, tipPercent = 15) {
    const tip = bill * (tipPercent / 100);
    return bill + tip;
}

console.log(calculateTotal(50));      // 57.5 (15% tip)
console.log(calculateTotal(50, 20));  // 60 (20% tip)
```

### Validate Email

```javascript
function isValidEmail(email) {
    return email.includes("@") && 
           email.includes(".") && 
           email.length > 5;
}

console.log(isValidEmail("alice@example.com"));  // true
console.log(isValidEmail("alice@com"));          // false
console.log(isValidEmail("alice.com"));          // false
```

---

## Practice Exercises

### Exercise 1: Basic Function
```javascript
// Create a function that:
// - Takes a name as parameter
// - Returns "Hello, [name]!"

function greet(name) {
    // Your code here
}

console.log(greet("Alice"));  // "Hello, Alice!"
```

### Exercise 2: Function with Multiple Parameters
```javascript
// Create a function that calculates area of rectangle
// - Takes width and height
// - Returns the area

function calculateArea(width, height) {
    // Your code here
}

console.log(calculateArea(5, 10));  // 50
```

### Exercise 3: Function with Default Parameter
```javascript
// Create a function that makes a sentence
// - Takes name and age parameters
// - Age has default value of 18
// - Returns "My name is [name] and I am [age] years old"

function introduce(name, age = 18) {
    // Your code here
}

console.log(introduce("Bob"));           // "My name is Bob and I am 18 years old"
console.log(introduce("Alice", 25));     // "My name is Alice and I am 25 years old"
```

### Exercise 4: Function Returning Boolean
```javascript
// Create a function that:
// - Takes a number as parameter
// - Returns true if the number is even, false if odd

function isEven(num) {
    // Your code here
}

console.log(isEven(4));  // true
console.log(isEven(7));  // false
```

---

## Solutions

```javascript
// Exercise 1
function greet(name) {
    return `Hello, ${name}!`;
}

// Exercise 2
function calculateArea(width, height) {
    return width * height;
}

// Exercise 3
function introduce(name, age = 18) {
    return `My name is ${name} and I am ${age} years old`;
}

// Exercise 4
function isEven(num) {
    return num % 2 === 0;
}
```

---

## Key Takeaways

✅ Functions are reusable blocks of code  
✅ Use descriptive function names  
✅ Return values when you need to use results  
✅ Use default parameters for optional values  
✅ Arrow functions are shorter syntax  

---

## 📚 Resources

### Documentation
- **MDN: Functions**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions
- **JavaScript.info Functions**: https://javascript.info/function-basics

### Video Tutorials
- **Functions by Traversy Media**: https://www.youtube.com/watch?v=FOD408a0EzQ
- **Arrow Functions Explained**: https://www.youtube.com/watch?v=h33Srr5J9nY

---

**Next**: [Parameters & Arguments](./02-parameters-arguments.md)  
**Back**: [← Functions Index](./README.md)
