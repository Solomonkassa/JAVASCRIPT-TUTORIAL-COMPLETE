# Operators: Performing Operations on Data

Learn how to manipulate data using JavaScript operators.

## 1. Arithmetic Operators

Perform mathematical operations.

```javascript
let a = 10;
let b = 3;

console.log(a + b);  // 13 (Addition)
console.log(a - b);  // 7 (Subtraction)
console.log(a * b);  // 30 (Multiplication)
console.log(a / b);  // 3.333... (Division)
console.log(a % b);  // 1 (Modulo - remainder)
console.log(a ** b); // 1000 (Exponentiation)
```

### Increment and Decrement

```javascript
let x = 5;

console.log(x++);  // 5 (post-increment, then increments)
console.log(x);    // 6

console.log(++x);  // 7 (pre-increment, then logs)
console.log(x);    // 7

console.log(x--);  // 7 (post-decrement, then decrements)
console.log(x);    // 6

console.log(--x);  // 5 (pre-decrement, then logs)
```

---

## 2. Assignment Operators

Assign values to variables.

```javascript
let x = 10;

x = 5;           // Assignment
x += 3;          // x = x + 3 → 8
x -= 2;          // x = x - 2 → 6
x *= 2;          // x = x * 2 → 12
x /= 4;          // x = x / 4 → 3
x %= 2;          // x = x % 2 → 1
x **= 3;         // x = x ** 3 → 1

console.log(x);  // 1
```

---

## 3. Comparison Operators

Compare values and return boolean results.

```javascript
let a = 10;
let b = "10";
let c = 5;

console.log(a == b);   // true (value equal, different types)
console.log(a === b);  // false (strict equal, same type required)
console.log(a != c);   // true (not equal)
console.log(a !== b);  // true (strictly not equal)
console.log(a > c);    // true (greater than)
console.log(a >= a);   // true (greater than or equal)
console.log(a < c);    // false (less than)
console.log(a <= c);   // false (less than or equal)
```

### == vs === (Important!)

```javascript
// == (loose equality - allows type conversion)
console.log(5 == "5");    // true (converts string to number)
console.log(1 == true);   // true (converts boolean to number)
console.log(0 == false);  // true

// === (strict equality - no type conversion)
console.log(5 === "5");   // false (different types)
console.log(1 === true);  // false (different types)
console.log(0 === false); // false

// ✅ ALWAYS use === in modern JavaScript!
```

---

## 4. Logical Operators

Combine boolean values.

### AND Operator (&&)

Returns true only if BOTH conditions are true.

```javascript
let age = 25;
let hasLicense = true;

console.log(age >= 18 && hasLicense);  // true
console.log(age >= 18 && false);       // false

// Practical example
if (age >= 18 && hasLicense) {
    console.log("Can drive!");
}
```

### OR Operator (||)

Returns true if AT LEAST ONE condition is true.

```javascript
let isWeekend = false;
let isHoliday = true;

console.log(isWeekend || isHoliday);  // true
console.log(false || false);          // false

// Practical example
if (isWeekend || isHoliday) {
    console.log("No work today!");
}
```

### NOT Operator (!)

Reverses the boolean value.

```javascript
let isRaining = false;

console.log(!isRaining);     // true
console.log(!true);          // false
console.log(!false);         // true

// Practical example
if (!isRaining) {
    console.log("Go outside!");
}
```

### Complex Logic

```javascript
let age = 25;
let hasLicense = true;
let isInsured = true;

// Can drive if: age >= 18 AND (has license AND is insured)
if (age >= 18 && (hasLicense && isInsured)) {
    console.log("Approved to drive!");
}

// Can enter if: has ID OR is recognized
if (hasID || isRecognized) {
    console.log("Welcome!");
}

// Multiple conditions
if (age >= 18 && (hasLicense || isExperienced) && !isDrunk) {
    console.log("Safe to drive");
}
```

---

## 5. String Operators

### Concatenation (+)

```javascript
let firstName = "John";
let lastName = "Doe";

let fullName = firstName + " " + lastName;
console.log(fullName);  // "John Doe"

// With numbers
console.log("Age: " + 25);           // "Age: 25"
console.log(10 + 5);                 // 15 (addition)
console.log("10" + 5);               // "105" (concatenation)
console.log(10 + "5");               // "105" (concatenation)
```

### Concatenation Assignment (+=)

```javascript
let message = "Hello";
message += " ";
message += "World";
console.log(message);  // "Hello World"
```

### Template Literals (Better way - Chapter 5)

```javascript
let name = "Alice";
let age = 25;

// Modern approach
let intro = `My name is ${name} and I am ${age} years old.`;
console.log(intro);  // "My name is Alice and I am 25 years old."
```

---

## 6. Ternary Operator

Shorthand conditional.

```javascript
let age = 20;
let canVote = age >= 18 ? "Yes" : "No";
console.log(canVote);  // "Yes"

// Format: condition ? valueIfTrue : valueIfFalse

let status = score > 80 ? "Passed" : "Failed";
let message = isMorning ? "Good morning!" : "Good evening!";

// Nested ternary (avoid - hard to read)
let grade = score >= 90 ? "A" : score >= 80 ? "B" : "C";
```

---

## 7. typeof Operator

Check the type of a value.

```javascript
console.log(typeof 42);              // "number"
console.log(typeof "hello");         // "string"
console.log(typeof true);            // "boolean"
console.log(typeof undefined);       // "undefined"
console.log(typeof { name: "John" }); // "object"
console.log(typeof [1, 2, 3]);       // "object"
console.log(typeof null);            // "object" (quirk!)
```

---

## 8. Optional Chaining (?.)

Safely access nested properties (modern JavaScript).

```javascript
let user = {
    name: "Alice",
    address: {
        city: "New York"
    }
};

console.log(user.address?.city);      // "New York"
console.log(user.phone?.number);      // undefined (safe)

// Without optional chaining (would error)
// console.log(user.phone.number);   // ❌ Error!
```

---

## 9. Nullish Coalescing (??)

Use default value if value is null or undefined.

```javascript
let name = null;
let displayName = name ?? "Guest";
console.log(displayName);  // "Guest"

let age = 0;
let displayAge = age ?? 18;
console.log(displayAge);  // 0 (0 is not null/undefined)

// Different from || (logical OR)
let amount = 0;
console.log(amount || 10);  // 10 (treats 0 as falsy)
console.log(amount ?? 10);  // 0 (0 is not null/undefined)
```

---

## 10. Spread Operator (...)

Spread elements (modern JavaScript).

```javascript
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];

let combined = [...arr1, ...arr2];
console.log(combined);  // [1, 2, 3, 4, 5, 6]

let obj1 = { name: "Alice", age: 25 };
let obj2 = { city: "NYC" };

let merged = { ...obj1, ...obj2 };
console.log(merged);  // { name: "Alice", age: 25, city: "NYC" }
```

---

## Operator Precedence

Operations are evaluated in a specific order.

```javascript
console.log(2 + 3 * 4);        // 14 (multiplication first)
console.log((2 + 3) * 4);      // 20 (parentheses first)
console.log(true && false || true);  // true (AND before OR)
```

### Precedence Order (high to low):
1. Parentheses `()`
2. Exponentiation `**`
3. Multiplication/Division/Modulo `* / %`
4. Addition/Subtraction `+ -`
5. Comparison `< > <= >=`
6. Equality `== === != !==`
7. Logical AND `&&`
8. Logical OR `||`
9. Assignment `= += -=` etc.

---

## Practice Exercises

### Exercise 1: Basic Arithmetic
```javascript
// Calculate:
let result1 = 10 + 5 * 2;      // What is this?
let result2 = (10 + 5) * 2;    // What about this?
let result3 = 20 % 3;          // And this?
let result4 = 2 ** 8;          // And this?

console.log(result1, result2, result3, result4);
```

### Exercise 2: Logical Operations
```javascript
// What will these print?
console.log(true && true);     // ?
console.log(true && false);    // ?
console.log(false || true);    // ?
console.log(!true);            // ?
console.log(5 > 3 && 2 < 4);   // ?
```

### Exercise 3: Ternary Operator
```javascript
// Rewrite this using ternary operator:
let age = 20;
let status;
if (age >= 18) {
    status = "Adult";
} else {
    status = "Minor";
}
// Rewritten as one line?
```

### Exercise 4: Type Checking
```javascript
// Create a program that:
// 1. Declares 5 variables with different types
// 2. Checks the type of each using typeof
// 3. Prints the results

// Your code here
```

---

## Solutions

```javascript
// Exercise 1
console.log(20);    // 10 + 5 * 2 = 10 + 10 = 20
console.log(30);    // (10 + 5) * 2 = 15 * 2 = 30
console.log(2);     // 20 % 3 = 2
console.log(256);   // 2 ** 8 = 256

// Exercise 2
console.log(true);      // true && true = true
console.log(false);     // true && false = false
console.log(true);      // false || true = true
console.log(false);     // !true = false
console.log(true);      // 5 > 3 = true, 2 < 4 = true, true && true = true

// Exercise 3
let status = age >= 18 ? "Adult" : "Minor";

// Exercise 4 (Example solution)
let num = 42;
let text = "hello";
let flag = true;
let nothing = undefined;
let obj = { };

console.log(typeof num);       // "number"
console.log(typeof text);      // "string"
console.log(typeof flag);      // "boolean"
console.log(typeof nothing);   // "undefined"
console.log(typeof obj);       // "object"
```

---

## Key Takeaways

✅ Use `===` for comparison, not `==`  
✅ Understand operator precedence (order matters)  
✅ Use template literals for string concatenation  
✅ Logical operators combine conditions  
✅ Ternary operator is useful for simple conditionals  

---

## 📚 Resources

### Documentation
- **MDN: Operators**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators
- **JavaScript.info Operators**: https://javascript.info/operators

### Video Tutorials
- **Operators by The Net Ninja**: https://www.youtube.com/watch?v=nU1FvDWlS6s
- **Logical Operators Explained**: https://www.youtube.com/watch?v=Oj2c0D_6bR4

---

**Next**: [Type Conversion](./03-type-conversion.md)  
**Back**: [← Variables & Types](./01-variables-types.md)  
**Index**: [← Fundamentals](./README.md)
