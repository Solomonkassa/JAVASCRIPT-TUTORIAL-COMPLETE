# Strings: Working with Text

Master JavaScript string operations and methods.

## Creating Strings

```javascript
// Single quotes
let str1 = 'Hello';

// Double quotes
let str2 = "World";

// Backticks (template literals - modern)
let str3 = `Hello World`;

console.log(str1, str2, str3);  // All work the same
```

---

## String Properties

### Length Property

```javascript
let text = "JavaScript";
console.log(text.length);           // 10

let empty = "";
console.log(empty.length);          // 0

// Useful for validation
if (password.length < 8) {
    console.log("Password too short");
}
```

### Accessing Characters

```javascript
let str = "JavaScript";

// Using index (0-based)
console.log(str[0]);                // "J"
console.log(str[4]);                // "S"
console.log(str[str.length - 1]);   // "t" (last character)
console.log(str[100]);              // undefined

// Using charAt()
console.log(str.charAt(0));         // "J"
console.log(str.charAt(4));         // "S"
```

---

## Common String Methods

### Case Conversion

```javascript
let text = "Hello World";

console.log(text.toUpperCase());    // "HELLO WORLD"
console.log(text.toLowerCase());    // "hello world"
console.log(text.toLocaleLowerCase()); // "hello world"
```

### Finding Strings

```javascript
let text = "The quick brown fox";

// indexOf() - returns position (0-based), -1 if not found
console.log(text.indexOf("quick"));     // 4
console.log(text.indexOf("fox"));       // 16
console.log(text.indexOf("dog"));       // -1
console.log(text.indexOf("o"));         // 12 (first occurrence)

// lastIndexOf() - finds last occurrence
console.log(text.lastIndexOf("o"));     // 17

// includes() - returns boolean (modern)
console.log(text.includes("quick"));    // true
console.log(text.includes("dog"));      // false
console.log(text.includes("The"));      // true

// startsWith() and endsWith()
console.log(text.startsWith("The"));    // true
console.log(text.endsWith("fox"));      // true
```

### Extracting Parts

```javascript
let str = "JavaScript";

// slice() - extracts part of string (doesn't modify original)
console.log(str.slice(0, 4));       // "Java"
console.log(str.slice(4));          // "Script"
console.log(str.slice(-6));         // "Script" (from end)
console.log(str.slice(-6, -2));     // "Scri"

// substring() - similar to slice (but different negative handling)
console.log(str.substring(0, 4));   // "Java"
console.log(str.substring(4));      // "Script"

// substr() - DEPRECATED, don't use
// console.log(str.substr(0, 4));   // ❌ Avoid

// trim() - removes whitespace
let messy = "  hello world  ";
console.log(messy.trim());          // "hello world"
console.log(messy.trimStart());     // "hello world  "
console.log(messy.trimEnd());       // "  hello world"
```

### Replacing Content

```javascript
let text = "Hello World, Hello Universe";

// replace() - replaces first match
console.log(text.replace("Hello", "Hi"));
// "Hi World, Hello Universe"

// replaceAll() - replaces all matches (modern)
console.log(text.replaceAll("Hello", "Hi"));
// "Hi World, Hi Universe"

// With regex (advanced)
console.log(text.replace(/Hello/g, "Hi"));  // "Hi World, Hi Universe"
```

### Splitting and Joining

```javascript
// split() - converts string to array
let text = "apple,banana,orange";
let fruits = text.split(",");
console.log(fruits);                // ["apple", "banana", "orange"]

let words = "Hello World JavaScript".split(" ");
console.log(words);                 // ["Hello", "World", "JavaScript"]

let chars = "Hello".split("");
console.log(chars);                 // ["H", "e", "l", "l", "o"]

// join() - converts array to string
let joined = fruits.join(" & ");
console.log(joined);                // "apple & banana & orange"

// Practical example
let csv = "John,Doe,30,NYC";
let [first, last, age, city] = csv.split(",");
console.log(first, last, age, city);
```

### Repeating Strings

```javascript
let star = "*";
console.log(star.repeat(5));        // "*****"

let dash = "-".repeat(10);
console.log(dash);                  // "----------"

// Creating separators
let separator = "=".repeat(30);
console.log(separator);             // "=============================="
```

### Padding Strings

```javascript
let num = "5";

// padStart() - pad beginning
console.log(num.padStart(3, "0"));  // "005"
console.log("42".padStart(4, "0")); // "0042"

// padEnd() - pad end
console.log(num.padEnd(3, "0"));    // "500"
console.log("hi".padEnd(5, "."));   // "hi..."

// Practical: formatting numbers
let price = "9.99";
console.log(price.padStart(8, "$")); // "$$$9.99"
```

### String Comparison

```javascript
let str1 = "apple";
let str2 = "banana";

console.log(str1.localeCompare(str2));  // -1 (str1 comes first)
console.log(str2.localeCompare(str1));  // 1  (str2 comes first)
console.log(str1.localeCompare("apple")); // 0 (same)
```

---

## String Concatenation

### Using + Operator

```javascript
let firstName = "John";
let lastName = "Doe";

let fullName = firstName + " " + lastName;
console.log(fullName);              // "John Doe"

// Adding different types
console.log("Age: " + 25);          // "Age: 25"
console.log("Items: " + 5 + 3);     // "Items: 53" (concatenation)
console.log("Items: " + (5 + 3));   // "Items: 8" (addition first)
```

### Using concat() Method

```javascript
let greeting = "Hello".concat(" ", "World", "!");
console.log(greeting);              // "Hello World!"

// Works with any type
let msg = "Count: ".concat(1, 2, 3);
console.log(msg);                   // "Count: 123"
```

### Using += Operator

```javascript
let text = "Hello";
text += " ";
text += "World";
console.log(text);                  // "Hello World"

// More efficient for multiple concatenations
let result = "";
for (let i = 1; i <= 3; i++) {
    result += i + " ";
}
console.log(result);                // "1 2 3 "
```

---

## Template Literals (Modern Way)

Use backticks (`) and ${} for variable insertion.

```javascript
let name = "Alice";
let age = 25;

// Old way (concatenation)
let intro1 = "My name is " + name + " and I am " + age + " years old";

// Modern way (template literal)
let intro2 = `My name is ${name} and I am ${age} years old`;

console.log(intro2);  // "My name is Alice and I am 25 years old"
```

### Template Literal Features

```javascript
let x = 10;
let y = 20;

// Expressions inside ${}
console.log(`${x} + ${y} = ${x + y}`);  // "10 + 20 = 30"

// Multi-line strings
let poem = `Roses are red
Violets are blue
JavaScript is awesome
And so are you`;
console.log(poem);

// Calling functions
function getName() {
    return "Bob";
}
console.log(`Hello, ${getName()}!`);  // "Hello, Bob!"

// Conditional expressions
let age = 20;
console.log(`You are ${age >= 18 ? "an adult" : "a minor"}`);
// "You are an adult"
```

---

## Regular Expressions (Intro)

Pattern matching in strings (covered in depth later).

```javascript
// Finding patterns
let text = "I have 2 apples and 3 oranges";
let matches = text.match(/\d+/g);  // Find all numbers
console.log(matches);              // ["2", "3"]

// Checking if pattern exists
let hasNumbers = /\d/.test(text);
console.log(hasNumbers);           // true

// Replacing patterns
let cleaned = text.replace(/\d+/g, "X");
console.log(cleaned);              // "I have X apples and X oranges"
```

---

## Practical Examples

### Validate Email Format

```javascript
function isValidEmail(email) {
    return email.includes("@") && email.includes(".");
}

console.log(isValidEmail("alice@example.com"));  // true
console.log(isValidEmail("alice.example.com"));  // false
```

### Extract Domain from Email

```javascript
let email = "john@example.com";
let domain = email.slice(email.indexOf("@") + 1);
console.log(domain);                // "example.com"
```

### Format Phone Number

```javascript
function formatPhone(phone) {
    // Remove non-digits
    phone = phone.replace(/\D/g, "");
    // Format as (XXX) XXX-XXXX
    return `(${phone.slice(0, 3)}) ${phone.slice(3, 6)}-${phone.slice(6)}`;
}

console.log(formatPhone("5551234567"));  // "(555) 123-4567"
```

### Reverse a String

```javascript
function reverseString(str) {
    return str.split("").reverse().join("");
}

console.log(reverseString("Hello"));  // "olleH"
```

### Count Character Occurrences

```javascript
function countChar(str, char) {
    return str.split(char).length - 1;
}

console.log(countChar("hello", "l"));  // 2
console.log(countChar("mississippi", "s"));  // 4
```

---

## Practice Exercises

### Exercise 1: String Basics
```javascript
let text = "JavaScript is awesome";

// Get the length
// Get the first character
// Get the last character
// Convert to uppercase
// Convert to lowercase

// Your code here
```

### Exercise 2: Finding and Replacing
```javascript
let sentence = "The quick brown fox jumps over the lazy dog";

// Find if it includes "quick"
// Find the index of "fox"
// Replace "lazy" with "clever"

// Your code here
```

### Exercise 3: String Manipulation
```javascript
// Create a function that:
// 1. Takes a name as input
// 2. Converts first letter to uppercase, rest to lowercase
// 3. Returns the formatted name

function formatName(name) {
    // Your code here
}

console.log(formatName("jOHN"));   // Should print "John"
console.log(formatName("ALICE"));  // Should print "Alice"
```

### Exercise 4: Template Literals
```javascript
let user = "Alice";
let score = 95;
let level = "Expert";

// Using template literals, print:
// "Alice has achieved a score of 95 and reached Expert level!"

// Your code here
```

---

## Solutions

```javascript
// Exercise 1
let text = "JavaScript is awesome";
console.log(text.length);           // 21
console.log(text[0]);               // "J"
console.log(text[text.length - 1]); // "e"
console.log(text.toUpperCase());    // "JAVASCRIPT IS AWESOME"
console.log(text.toLowerCase());    // "javascript is awesome"

// Exercise 2
let sentence = "The quick brown fox jumps over the lazy dog";
console.log(sentence.includes("quick"));  // true
console.log(sentence.indexOf("fox"));     // 16
console.log(sentence.replace("lazy", "clever"));
// "The quick brown fox jumps over the clever dog"

// Exercise 3
function formatName(name) {
    return name.charAt(0).toUpperCase() + name.slice(1).toLowerCase();
}

// Exercise 4
let user = "Alice";
let score = 95;
let level = "Expert";
console.log(`${user} has achieved a score of ${score} and reached ${level} level!`);
```

---

## Key Takeaways

✅ Strings are immutable in JavaScript  
✅ Use template literals for modern string handling  
✅ Learn the common methods: slice, indexOf, replace, split, join  
✅ Remember length property is 0-based indexing  
✅ Template literals support multi-line strings and expressions  

---

## 📚 Resources

### Documentation
- **MDN: String Methods**: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String
- **JavaScript.info Strings**: https://javascript.info/string

### Video Tutorials
- **String Methods by Traversy Media**: https://www.youtube.com/watch?v=08M7lRw3O9s
- **Template Literals Explained**: https://www.youtube.com/watch?v=DRR0iveiMSs

---

**Next**: [Template Literals](./05-template-literals.md)  
**Back**: [← Type Conversion](./03-type-conversion.md)
