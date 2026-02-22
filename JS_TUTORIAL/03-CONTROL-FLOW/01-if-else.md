# If/Else Statements: Making Decisions

Control program flow based on conditions.

## Basic If Statement

Execute code only if condition is true.

```javascript
// Syntax
if (condition) {
    // Code runs if condition is true
}

// Example
let age = 18;
if (age >= 18) {
    console.log("You can vote!");
}
// Output: "You can vote!"
```

### Single Statement (no braces)

```javascript
let score = 95;
if (score > 90)
    console.log("Excellent!");

// ✅ Better: Always use braces for clarity
if (score > 90) {
    console.log("Excellent!");
}
```

---

## If/Else Statement

Execute one block if true, another if false.

```javascript
let age = 15;

if (age >= 18) {
    console.log("You can vote!");
} else {
    console.log("You cannot vote yet.");
}
// Output: "You cannot vote yet."
```

### More Complex Example

```javascript
let score = 75;

if (score >= 90) {
    console.log("Grade A");
} else {
    console.log("Not an A");
}
```

---

## If/Else If/Else Statement

Handle multiple conditions.

```javascript
let score = 75;

if (score >= 90) {
    console.log("Grade: A");
} else if (score >= 80) {
    console.log("Grade: B");
} else if (score >= 70) {
    console.log("Grade: C");
} else if (score >= 60) {
    console.log("Grade: D");
} else {
    console.log("Grade: F");
}
// Output: "Grade: C"
```

### Important: Order Matters

```javascript
let age = 20;

// ✅ Correct order (specific to general)
if (age >= 18) {
    console.log("Adult");
} else if (age >= 13) {
    console.log("Teen");
} else {
    console.log("Child");
}

// ❌ Wrong order (first condition catches everything)
if (age >= 13) {
    console.log("Teen");
} else if (age >= 18) {
    console.log("Adult");  // This never runs!
} else {
    console.log("Child");
}
```

---

## Nested If Statements

If statements inside if statements.

```javascript
let age = 20;
let hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        console.log("Can drive!");
    } else {
        console.log("Get a license first");
    }
} else {
    console.log("Too young to drive");
}
// Output: "Can drive!"

// Better with && operator
if (age >= 18 && hasLicense) {
    console.log("Can drive!");
}
```

---

## Comparison Operators (Review)

Used in conditions:

```javascript
let x = 10;

console.log(x > 5);      // true
console.log(x < 5);      // false
console.log(x >= 10);    // true
console.log(x <= 10);    // true
console.log(x == 10);    // true (loose equality)
console.log(x === "10"); // false (strict equality)
console.log(x !== "10"); // true (strict inequality)
```

---

## Logical Operators (Review)

### AND (&&)

Both conditions must be true.

```javascript
let age = 25;
let hasJob = true;

if (age >= 18 && hasJob) {
    console.log("Loan approved!");
}
// Output: "Loan approved!"
```

### OR (||)

At least one condition must be true.

```javascript
let isWeekend = false;
let isHoliday = true;

if (isWeekend || isHoliday) {
    console.log("Day off!");
}
// Output: "Day off!"
```

### NOT (!)

Inverts the condition.

```javascript
let isRaining = false;

if (!isRaining) {
    console.log("Go outside!");
}
// Output: "Go outside!"
```

---

## Truthy and Falsy in Conditions

Any value can be used in a condition (will convert to boolean).

### Falsy Values

```javascript
if (false) console.log("Won't print");
if (0) console.log("Won't print");
if ("") console.log("Won't print");
if (null) console.log("Won't print");
if (undefined) console.log("Won't print");
if (NaN) console.log("Won't print");
```

### Truthy Values

```javascript
if (true) console.log("Prints");         // true
if (1) console.log("Prints");            // number
if ("hello") console.log("Prints");      // string
if ([]) console.log("Prints");           // array
if ({}) console.log("Prints");           // object
if (function() {}) console.log("Prints"); // function
```

### Practical Truthy/Falsy Usage

```javascript
let user = "Alice";

// Check if user exists
if (user) {
    console.log(`Welcome, ${user}!`);
}

let items = [];
if (items.length) {
    console.log("Has items");
} else {
    console.log("Empty");  // Prints
}

// Default value
let name = userInput || "Guest";
```

---

## Practical Examples

### Age Check Program

```javascript
let age = prompt("What is your age?");
age = Number(age);

if (age < 0 || isNaN(age)) {
    console.log("Invalid age");
} else if (age < 13) {
    console.log("Child");
} else if (age < 18) {
    console.log("Teen");
} else if (age < 65) {
    console.log("Adult");
} else {
    console.log("Senior");
}
```

### Login System

```javascript
function login(username, password) {
    if (!username || !password) {
        return "Username and password required";
    }
    
    if (username === "admin" && password === "pass123") {
        return "Login successful!";
    } else {
        return "Invalid credentials";
    }
}

console.log(login("admin", "pass123"));  // "Login successful!"
console.log(login("admin", "wrong"));    // "Invalid credentials"
console.log(login("", "pass123"));       // "Username and password required"
```

### Weather Suggestion

```javascript
let temperature = 25;
let condition = "sunny";

if (temperature < 0) {
    console.log("Wear a heavy coat!");
} else if (temperature < 15) {
    console.log("Wear a light jacket");
} else if (temperature < 25) {
    console.log("Wear a sweater");
} else {
    console.log("Short sleeves are fine");
}

if (condition === "rainy") {
    console.log("Bring an umbrella");
}
```

---

## Common Mistakes

### Missing Braces

```javascript
// ❌ Wrong - only first statement is in if block
if (x > 5)
    console.log("x is big");
    console.log("This always runs!");

// ✅ Correct
if (x > 5) {
    console.log("x is big");
    console.log("This is conditional");
}
```

### Using = instead of ==

```javascript
let x = 5;

// ❌ Wrong - this assigns instead of comparing
if (x = 10) {
    console.log("x is now 10");  // This runs!
}

// ✅ Correct
if (x === 10) {
    console.log("x equals 10");
}
```

### Too Many Else Ifs

```javascript
// ❌ Too many conditions - use switch instead
if (day === "Monday") {
    // ...
} else if (day === "Tuesday") {
    // ...
} else if (day === "Wednesday") {
    // ...
} else if (day === "Thursday") {
    // ...
} else if (day === "Friday") {
    // ...
}

// ✅ Use switch for this (see next section)
```

---

## Practice Exercises

### Exercise 1: Simple If/Else
```javascript
// Check if a number is positive, negative, or zero
let num = 10;
// Your code here
```

### Exercise 2: Nested If
```javascript
// Check if someone can drive:
// Must be 18+ AND have a license
let age = 20;
let hasLicense = false;
// Your code here
```

### Exercise 3: Multiple Conditions
```javascript
// Assign letter grade based on score:
// 90+: A, 80-89: B, 70-79: C, 60-69: D, <60: F
let score = 85;
// Your code here
```

### Exercise 4: User Validation
```javascript
// Create function that validates user input:
// - Username must be at least 3 characters
// - Password must be at least 8 characters
// - Email must contain @

function validate(username, password, email) {
    // Your code here
}
```

---

## Solutions

```javascript
// Exercise 1
let num = 10;
if (num > 0) {
    console.log("Positive");
} else if (num < 0) {
    console.log("Negative");
} else {
    console.log("Zero");
}

// Exercise 2
let age = 20;
let hasLicense = false;
if (age >= 18) {
    if (hasLicense) {
        console.log("Can drive");
    } else {
        console.log("Get a license");
    }
} else {
    console.log("Too young");
}

// Exercise 3
let score = 85;
if (score >= 90) {
    console.log("A");
} else if (score >= 80) {
    console.log("B");
} else if (score >= 70) {
    console.log("C");
} else if (score >= 60) {
    console.log("D");
} else {
    console.log("F");
}

// Exercise 4
function validate(username, password, email) {
    if (username.length < 3) {
        return "Username too short";
    }
    if (password.length < 8) {
        return "Password too short";
    }
    if (!email.includes("@")) {
        return "Invalid email";
    }
    return "Valid";
}
```

---

## Key Takeaways

✅ Use === for comparison, not ==  
✅ Always use braces even for single statements  
✅ Order matters in else if chains  
✅ Understand truthy and falsy values  
✅ Use logical operators to combine conditions  

---

## 📚 Resources

### Documentation
- **MDN: If...else**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else
- **JavaScript.info: Conditionals**: https://javascript.info/ifelse

### Video Tutorials
- **If/Else by Traversy Media**: https://www.youtube.com/watch?v=IsG4Xd6LlsM
- **Conditional Statements**: https://www.youtube.com/watch?v=Go7bVeVlsos

---

**Next**: [Switch Statements](./02-switch.md)  
**Back**: [← Control Flow Index](./README.md)
