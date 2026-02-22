# JavaScript Quick Cheat Sheet

Quick reference for common JavaScript patterns and syntax.

## Variables

```javascript
// Declaration
let variable = "can change";      // Block-scoped, changeable
const constant = "cannot change";  // Block-scoped, unchangeable
var old = "function-scoped";       // Avoid in modern code

// Constants for config
const MAX_USERS = 100;
const API_URL = "https://api.example.com";
```

## Data Types

```javascript
// Primitives
let num = 42;
let str = "text";
let bool = true;
let nothing = null;
let empty;  // undefined
let sym = Symbol("id");
let big = 100n;

// Objects
let obj = { key: "value" };
let arr = [1, 2, 3];
let fn = () => {};
let date = new Date();

// Type checking
typeof 42           // "number"
typeof "hello"      // "string"
typeof true         // "boolean"
typeof []           // "object"
Array.isArray([])   // true
```

## Operators

```javascript
// Arithmetic
10 + 5 = 15         // Addition
10 - 5 = 5          // Subtraction
10 * 5 = 50         // Multiplication
10 / 5 = 2          // Division
10 % 3 = 1          // Modulo
2 ** 3 = 8          // Exponent

// Comparison (use ===!)
x === y             // Strictly equal
x !== y             // Strictly not equal
x > y               // Greater than
x < y               // Less than
x >= y              // Greater or equal
x <= y              // Less or equal

// Logical
x && y              // AND
x || y              // OR
!x                  // NOT

// Assignment
x = 5               // Assign
x += 5              // Add and assign
x -= 5              // Subtract and assign
x *= 5              // Multiply and assign
x /= 5              // Divide and assign

// Increment/Decrement
++x                 // Pre-increment
x++                 // Post-increment
--x                 // Pre-decrement
x--                 // Post-decrement

// Ternary
condition ? true : false
```

## Strings

```javascript
// Creation
let str = "hello";
let str2 = 'world';
let str3 = `interpolate: ${variable}`;

// Methods
str.length          // Length
str.toUpperCase()   // To uppercase
str.toLowerCase()   // To lowercase
str.charAt(0)       // Character at index
str[0]              // Alternative access
str.slice(0, 5)     // Extract substring
str.substring(0, 5) // Like slice
str.indexOf("l")    // Find index
str.includes("lo")  // Check if includes
str.replace("l", "x") // Replace
str.split(" ")      // Split into array
str.trim()          // Remove whitespace
str.repeat(3)       // Repeat string
str.padStart(10, "0") // Pad start

// Template literals
`String with ${variable} and ${expression}`
```

## Arrays

```javascript
// Creation
let arr = [1, 2, 3];
let arr2 = new Array(3);
let arr3 = Array.from("hello");

// Access
arr[0]              // First element
arr[arr.length - 1] // Last element

// Modification
arr.push(4)         // Add to end
arr.pop()           // Remove last
arr.unshift(0)      // Add to start
arr.shift()         // Remove first
arr.splice(1, 2)    // Remove/add elements
arr.slice(0, 3)     // Extract copy

// Transformation
arr.map(x => x * 2)                     // Transform
arr.filter(x => x > 2)                  // Filter
arr.reduce((sum, x) => sum + x, 0)      // Reduce
arr.find(x => x > 2)                    // Find first
arr.findIndex(x => x > 2)               // Find index
arr.some(x => x > 2)                    // Check any
arr.every(x => x > 0)                   // Check all
arr.includes(2)                         // Contains

// Iteration
arr.forEach(x => console.log(x))        // Loop
arr.entries()                           // Key-value pairs

// Search
arr.indexOf(2)                          // Find index
arr.includes(2)                         // Check existence

// Sorting
arr.sort()                              // Sort
arr.sort((a, b) => a - b)               // Sort numbers
arr.reverse()                           // Reverse

// Info
arr.length                              // Length
arr.join("-")                           // Join to string
```

## Objects

```javascript
// Creation
let obj = { name: "Alice", age: 25 };
let obj2 = { "key-name": "value" };
let obj3 = new Object();

// Access
obj.name                // Dot notation
obj["name"]             // Bracket notation
obj["key-name"]         // For invalid names

// Modification
obj.city = "NYC"        // Add property
obj.age = 26            // Update property
delete obj.age          // Delete property

// Checking
"name" in obj           // Has property
obj.hasOwnProperty("name") // Has own property

// Keys/Values
Object.keys(obj)        // Get all keys
Object.values(obj)      // Get all values
Object.entries(obj)     // Get [key, value] pairs

// Methods
Object.assign(obj1, obj2)     // Merge objects
Object.freeze(obj)            // Make immutable
Object.seal(obj)              // Can't add/remove

// Spread
{ ...obj }              // Copy object
{ ...obj1, ...obj2 }    // Merge objects
```

## Functions

```javascript
// Declaration
function greet(name) {
    return `Hello, ${name}!`;
}

// Expression
const add = function(a, b) {
    return a + b;
};

// Arrow
const multiply = (a, b) => a * b;
const square = x => x * x;
const getName = () => "John";

// Default parameters
function greet(name = "Guest") {
    return `Hello, ${name}!`;
}

// Rest parameters
function sum(...numbers) {
    return numbers.reduce((a, b) => a + b, 0);
}

// Destructuring parameters
function display({ name, age }) {
    console.log(name, age);
}
```

## Control Flow

```javascript
// If/Else
if (condition) {
    // true
} else if (condition2) {
    // condition2 true
} else {
    // both false
}

// Ternary
condition ? valueIfTrue : valueIfFalse

// Switch
switch (value) {
    case 1:
        // statements
        break;
    case 2:
        // statements
        break;
    default:
        // default statements
}

// For loop
for (let i = 0; i < 10; i++) {
    console.log(i);
}

// While loop
while (condition) {
    // statements
}

// Do-while
do {
    // statements
} while (condition);

// For-of (values)
for (const item of array) {
    console.log(item);
}

// For-in (keys)
for (const key in object) {
    console.log(key, object[key]);
}

// ForEach
array.forEach((item, index) => {
    console.log(item, index);
});
```

## Classes

```javascript
// Class declaration
class Person {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    
    greet() {
        return `Hello, I'm ${this.name}`;
    }
    
    static info() {
        return "Person class";
    }
}

// Create instance
const person = new Person("Alice", 25);

// Inheritance
class Student extends Person {
    constructor(name, age, studentId) {
        super(name, age);
        this.studentId = studentId;
    }
}

// Getters/Setters
class Circle {
    constructor(radius) {
        this._radius = radius;
    }
    
    get radius() {
        return this._radius;
    }
    
    set radius(value) {
        this._radius = value;
    }
}
```

## Destructuring

```javascript
// Array destructuring
const [a, b, c] = [1, 2, 3];
const [first, ...rest] = [1, 2, 3, 4];

// Object destructuring
const { name, age } = person;
const { name: personName } = person;  // Rename
const { name, age = 18 } = person;    // Default

// Nested destructuring
const { address: { city } } = person;

// Function parameters
const greet = ({ name, age }) => {
    console.log(name, age);
};
```

## Async/Await

```javascript
// Promise
const promise = new Promise((resolve, reject) => {
    if (success) resolve(value);
    else reject(error);
});

promise
    .then(result => console.log(result))
    .catch(error => console.log(error))
    .finally(() => console.log("done"));

// Async/Await
async function getData() {
    try {
        const response = await fetch("/api");
        const data = await response.json();
        return data;
    } catch (error) {
        console.log("Error:", error);
    } finally {
        console.log("Done");
    }
}

// Promise.all
Promise.all([promise1, promise2])
    .then(([result1, result2]) => {});

// Promise.race
Promise.race([promise1, promise2])
    .then(result => {});
```

## Fetch API

```javascript
// GET
fetch("/api/users")
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(err => console.log(err));

// POST
fetch("/api/users", {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ name: "John" })
})
    .then(res => res.json())
    .then(data => console.log(data));

// With async/await
async function getUsers() {
    const res = await fetch("/api/users");
    const data = await res.json();
    return data;
}
```

## DOM Manipulation

```javascript
// Select elements
document.getElementById("id")
document.querySelector(".class")
document.querySelectorAll(".class")
document.getElementsByClassName("class")
document.getElementsByTagName("div")

// Modify content
element.textContent = "text"
element.innerHTML = "<p>HTML</p>"
element.value = "new value"

// Modify attributes
element.setAttribute("data-id", "123")
element.getAttribute("data-id")
element.removeAttribute("data-id")

// Modify classes
element.classList.add("class")
element.classList.remove("class")
element.classList.toggle("class")
element.classList.contains("class")

// Modify styles
element.style.color = "red"
element.style.backgroundColor = "blue"

// Navigation
element.parentElement
element.children
element.firstChild
element.lastChild
element.nextSibling
element.previousSibling

// Create/Remove
document.createElement("div")
element.appendChild(child)
element.removeChild(child)
element.remove()
```

## Events

```javascript
// Add listener
element.addEventListener("click", (event) => {
    console.log(event.target);
});

// Remove listener
element.removeEventListener("click", handler);

// Event properties
event.target          // Element that triggered event
event.currentTarget   // Element listener attached to
event.type            // Event type
event.preventDefault() // Prevent default action
event.stopPropagation() // Stop bubbling

// Common events
"click"               // Mouse click
"dblclick"            // Double click
"mouseover"           // Mouse over
"mouseout"            // Mouse out
"change"              // Input changed
"submit"              // Form submitted
"focus"               // Element focused
"blur"                // Element unfocused
"keydown"             // Key pressed
"keyup"               // Key released
```

## Useful Methods

```javascript
// Math
Math.round(4.5)       // Round
Math.ceil(4.1)        // Round up
Math.floor(4.9)       // Round down
Math.max(1, 2, 3)     // Maximum
Math.min(1, 2, 3)     // Minimum
Math.random()         // 0-1 random
Math.pow(2, 3)        // Power
Math.sqrt(16)         // Square root
Math.abs(-5)          // Absolute

// String conversion
String(123)           // To string
Number("123")         // To number
Boolean(1)            // To boolean
JSON.stringify({})    // To JSON string
JSON.parse("{}")      // Parse JSON

// Array helpers
arr.toString()        // Convert to string
arr.concat([])        // Combine arrays

// Checking values
isNaN(value)          // Is Not a Number
isFinite(value)       // Is finite number
Number.isInteger(5)   // Is integer

// Time
setTimeout(() => {}, 1000)     // After 1 second
setInterval(() => {}, 1000)    // Every 1 second
clearTimeout(id)
clearInterval(id)
```

## Common Patterns

```javascript
// Conditional assignment
const value = condition ? valueIfTrue : valueIfFalse;

// Default value
const name = userInput || "default";
const count = quantity ?? 0;  // Nullish coalescing

// Array from string
const letters = "hello".split("");

// Remove duplicates
const unique = [...new Set(arr)];

// Sort array of objects
arr.sort((a, b) => a.age - b.age);

// Filter and map
arr.filter(x => x > 5).map(x => x * 2);

// Group by property
arr.reduce((groups, item) => {
    const group = item.category;
    groups[group] = groups[group] || [];
    groups[group].push(item);
    return groups;
}, {});

// Check if array includes value
arr.includes(value);

// Find maximum in array
Math.max(...arr);

// Flatten nested arrays
arr.flat();

// Create object from entries
Object.fromEntries([["a", 1], ["b", 2]]);
```

## Debugging

```javascript
console.log("message")         // Log
console.error("error")         // Error
console.warn("warning")        // Warning
console.table(data)            // Table format
console.time("label")          // Start timer
console.timeEnd("label")       // End timer
console.trace()                // Stack trace
console.assert(condition, "message") // Assert

// Error handling
try {
    // code
} catch (error) {
    console.log(error.message);
} finally {
    // cleanup
}

// Check types
typeof value
instanceof Constructor
Array.isArray(value)
```

## Tips & Tricks

```javascript
// Swap variables
[a, b] = [b, a];

// Default parameters for objects
function process(options = {}) {
    const { name = "default", ...rest } = options;
}

// Short-circuit evaluation
condition && doSomething();
condition || doFallback();

// Convert to number quickly
+"123"           // 123
-"-123"          // 123

// Convert to boolean quickly
!!value          // true/false
```

---

**Remember**: This is a quick reference. For detailed explanations, refer to the full tutorial chapters!

---

[← Back to Main](./README.md)
