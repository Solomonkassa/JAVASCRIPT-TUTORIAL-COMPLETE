# Type Conversion: Converting Between Data Types

Understanding how JavaScript converts between different data types.

## Two Types of Conversion

### 1. Implicit Conversion (Type Coercion)

JavaScript automatically converts types when needed.

```javascript
// String concatenation converts numbers to strings
console.log("Price: $" + 99);       // "Price: $99"
console.log(5 + "5");               // "55" (number + string = string)
console.log("5" + 5);               // "55"

// Arithmetic with strings
console.log("10" - 5);              // 5 (string converted to number)
console.log("10" * 2);              // 20
console.log("10" / 2);              // 5

// Boolean conversion in logical operations
console.log(5 && "hello");          // "hello"
console.log(0 || "default");        // "default"
console.log(!0);                    // true
```

---

## 2. Explicit Conversion (Type Casting)

You deliberately convert types using functions.

### Convert to String

```javascript
// Method 1: String() function
console.log(String(123));           // "123"
console.log(String(true));          // "true"
console.log(String(false));         // "false"
console.log(String(null));          // "null"
console.log(String(undefined));     // "undefined"

// Method 2: toString() method
console.log((123).toString());      // "123"
console.log(true.toString());       // "true"
let arr = [1, 2, 3];
console.log(arr.toString());        // "1,2,3"

// Method 3: Template literals
let age = 25;
console.log(`I am ${age} years old`);  // "I am 25 years old"

// Method 4: Concatenation
console.log("" + 42);               // "42"
```

### Convert to Number

```javascript
// Method 1: Number() function
console.log(Number("123"));         // 123
console.log(Number("123.45"));      // 123.45
console.log(Number(""));            // 0
console.log(Number("123abc"));      // NaN
console.log(Number(true));          // 1
console.log(Number(false));         // 0
console.log(Number(null));          // 0
console.log(Number(undefined));     // NaN

// Method 2: parseInt() - convert to integer
console.log(parseInt("123.45"));    // 123
console.log(parseInt("123abc"));    // 123
console.log(parseInt("abc123"));    // NaN
console.log(parseInt("FF", 16));    // 255 (hexadecimal)

// Method 3: parseFloat() - convert to decimal
console.log(parseFloat("123.45"));      // 123.45
console.log(parseFloat("123.45abc"));   // 123.45

// Method 4: Unary plus operator
console.log(+"123");                // 123
console.log(+"123.45");             // 123.45
console.log(+true);                 // 1
console.log(+false);                // 0
```

### Convert to Boolean

```javascript
// Method 1: Boolean() function
console.log(Boolean(1));            // true
console.log(Boolean(0));            // false
console.log(Boolean("hello"));      // true
console.log(Boolean(""));           // false
console.log(Boolean(null));         // false
console.log(Boolean(undefined));    // false
console.log(Boolean([]));           // true (arrays are truthy)
console.log(Boolean({}));           // true (objects are truthy)

// Method 2: Double negation (!!)
console.log(!!1);                   // true
console.log(!!0);                   // false
console.log(!!"hello");             // true
console.log(!!"");                  // false

// Method 3: In conditional statements
if (5) console.log("5 is truthy");   // Executes
if (0) console.log("0 is truthy");   // Doesn't execute
if ("") console.log("Empty string is truthy");  // Doesn't execute
if ("hello") console.log("'hello' is truthy");  // Executes
```

---

## Truthy and Falsy Values

### Falsy Values (become false when converted)

```javascript
// These are the ONLY falsy values:
Boolean(false);              // false
Boolean(0);                  // false
Boolean("");                 // false (empty string)
Boolean(null);               // false
Boolean(undefined);          // false
Boolean(NaN);                // false
```

### Truthy Values (everything else)

```javascript
Boolean(true);               // true
Boolean(1);                  // true
Boolean(-1);                 // true
Boolean("hello");            // true
Boolean("0");                // true (string "0" is truthy!)
Boolean([]);                 // true (array is truthy!)
Boolean({});                 // true (object is truthy!)
Boolean(function() {});      // true (function is truthy!)
```

### Practical Truthy/Falsy Usage

```javascript
let user = "";

// Checking if user exists
if (user) {
    console.log("User exists");
} else {
    console.log("No user");  // This prints
}

// Better way to check
if (user && user.length > 0) {
    console.log("Valid user");
}

// Default values
let name = userInput || "Guest";

// Array length check
let items = [];
if (items.length) {
    console.log("Has items");
} else {
    console.log("Empty");  // This prints
}
```

---

## Common Conversion Pitfalls

### Comparing Different Types

```javascript
// ❌ Avoid loose equality (==)
console.log("5" == 5);      // true (converts!)
console.log(0 == false);    // true (converts!)
console.log(null == undefined);  // true

// ✅ Use strict equality (===)
console.log("5" === 5);     // false (different types)
console.log(0 === false);   // false
console.log(null === undefined);  // false
```

### NaN Behavior

```javascript
let result = Number("hello");
console.log(result);            // NaN
console.log(result === NaN);    // false! (NaN !== NaN)

// Correct way to check for NaN
console.log(isNaN(result));     // true
console.log(Number.isNaN(result));  // true (more reliable)
```

### String to Number Edge Cases

```javascript
console.log(Number("   "));     // 0 (whitespace)
console.log(Number("\n123\n")); // 123 (trims whitespace)
console.log(Number("0x10"));    // 16 (hexadecimal)
console.log(parseInt("0x10"));  // 16
console.log(parseInt("123", 10));  // 123 (specify base 10)
```

---

## Practical Examples

### Form Input Conversion

```javascript
// HTML: <input id="ageInput" type="text">

let input = document.getElementById("ageInput").value;
let age = Number(input);  // Convert to number

if (age >= 18) {
    console.log("Can vote");
} else {
    console.log("Cannot vote");
}
```

### Calculating with String Numbers

```javascript
let price1 = "19.99";
let price2 = "29.99";

// Wrong way (concatenation)
console.log(price1 + price2);       // "19.9929.99"

// Right way (convert first)
let total = Number(price1) + Number(price2);
console.log(total);                 // 49.98
console.log(total.toFixed(2));      // "49.98"
```

### Validating User Input

```javascript
function getAge() {
    let input = prompt("What is your age?");
    let age = Number(input);
    
    if (isNaN(age) || age < 0) {
        console.log("Invalid age entered");
        return null;
    }
    
    return age;
}

let age = getAge();
```

---

## Practice Exercises

### Exercise 1: Implicit Conversion
```javascript
// Predict the output:
console.log("20" + 5);              // ?
console.log(20 + "5");              // ?
console.log("20" - 5);              // ?
console.log("20" * 5);              // ?
console.log("20" / "5");            // ?
```

### Exercise 2: Explicit Conversion
```javascript
// Convert these to the specified type:
let str = "42";
let num = Number(str);              // Convert to number
let bool = Boolean(str);            // Convert to boolean
let strAgain = String(bool);        // Convert back to string

console.log(num, bool, strAgain);
```

### Exercise 3: Truthy/Falsy
```javascript
// Which are truthy and which are falsy?
console.log(Boolean(0));            // ?
console.log(Boolean("0"));          // ?
console.log(Boolean(""));           // ?
console.log(Boolean([]));           // ?
console.log(Boolean(null));         // ?
```

### Exercise 4: Type Conversion Program
```javascript
// Create a program that:
// 1. Takes a string number as input
// 2. Converts it to actual number
// 3. Adds 10 to it
// 4. Converts back to string
// 5. Prints the result

let stringNum = "25";
// Your code here
```

---

## Solutions

```javascript
// Exercise 1
console.log("20" + 5);              // "205" (concatenation)
console.log(20 + "5");              // "205" (concatenation)
console.log("20" - 5);              // 15 (conversion)
console.log("20" * 5);              // 100 (conversion)
console.log("20" / "5");            // 4 (conversion)

// Exercise 2
let str = "42";
let num = Number(str);              // 42
let bool = Boolean(str);            // true
let strAgain = String(bool);        // "true"
console.log(num, bool, strAgain);   // 42 true "true"

// Exercise 3
console.log(Boolean(0));            // false (falsy)
console.log(Boolean("0"));          // true (truthy - string!)
console.log(Boolean(""));           // false (falsy)
console.log(Boolean([]));           // true (truthy)
console.log(Boolean(null));         // false (falsy)

// Exercise 4
let stringNum = "25";
let num = Number(stringNum);
let result = num + 10;
let finalStr = String(result);
console.log(finalStr);              // "35"
```

---

## Key Takeaways

✅ Understand implicit type coercion  
✅ Use explicit conversion functions when needed  
✅ Remember the 6 falsy values  
✅ Always use `===` instead of `==`  
✅ Validate user input before using it  

---

## 📚 Resources

### Documentation
- **MDN: Type Conversion**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Type_Conversion
- **JavaScript.info Type Coercion**: https://javascript.info/type-conversions

### Video Tutorials
- **Type Conversion by Traversy Media**: https://www.youtube.com/watch?v=QbVc0hc5A40
- **Truthy and Falsy Values**: https://www.youtube.com/watch?v=fJL0K1oDfCU

---

**Next**: [Strings](./04-strings.md)  
**Back**: [← Operators](./02-operators.md)
