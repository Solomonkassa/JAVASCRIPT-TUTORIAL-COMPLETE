# Loops in JavaScript

Loops allow you to execute a block of code multiple times. This is essential for iterating through data structures and automating repetitive tasks.

## Table of Contents
- [For Loop](#for-loop)
- [While Loop](#while-loop)
- [Do...While Loop](#dowhile-loop)
- [For...In Loop](#forin-loop)
- [For...Of Loop](#forof-loop)
- [Loop Control: Break & Continue](#loop-control-break--continue)
- [Nested Loops](#nested-loops)
- [Performance Tips](#performance-tips)
- [Exercises](#exercises)

---

## For Loop

The `for` loop repeats a block of code a specified number of times.

### Syntax
```javascript
for (initialization; condition; increment) {
  // Code to execute in each iteration
}
```

### Basic Example
```javascript
// Print numbers 1 to 5
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
// Output: 1, 2, 3, 4, 5
```

### Count Backwards
```javascript
// Countdown from 10 to 1
for (let i = 10; i >= 1; i--) {
  console.log(i);
}
// Output: 10, 9, 8, ..., 2, 1
```

### Loop Through Array
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
// Output: Apple, Banana, Orange
```

### Multiple Counters
```javascript
// Using multiple variables in for loop
for (let i = 0, j = 10; i < 5; i++, j--) {
  console.log(`i: ${i}, j: ${j}`);
}
// Output: 
// i: 0, j: 10
// i: 1, j: 9
// i: 2, j: 8
// i: 3, j: 7
// i: 4, j: 6
```

---

## While Loop

The `while` loop repeats a block of code while a condition is true.

### Syntax
```javascript
while (condition) {
  // Code to execute while condition is true
}
```

### Basic Example
```javascript
let count = 1;

while (count <= 5) {
  console.log(count);
  count++;
}
// Output: 1, 2, 3, 4, 5
```

### User Input Example
```javascript
let password = '';

while (password !== 'secret') {
  password = prompt('Enter password:');
  if (password === 'secret') {
    console.log('Access granted!');
  }
}
```

### Infinite Loop (⚠️ Be Careful!)
```javascript
// This will run forever!
// while (true) {
//   console.log('This never stops');
// }
```

---

## Do...While Loop

The `do...while` loop executes the block at least once, then checks the condition.

### Syntax
```javascript
do {
  // Code to execute
} while (condition);
```

### Example
```javascript
let i = 1;

do {
  console.log(i);
  i++;
} while (i <= 5);
// Output: 1, 2, 3, 4, 5
```

### Practical Example: Menu System
```javascript
let choice;

do {
  choice = prompt('Choose: 1=Start, 2=Settings, 3=Exit');
  
  switch(choice) {
    case '1':
      console.log('Starting game...');
      break;
    case '2':
      console.log('Opening settings...');
      break;
    case '3':
      console.log('Goodbye!');
      break;
    default:
      console.log('Invalid choice');
  }
} while (choice !== '3');
```

### Key Difference: do...while vs while
```javascript
// while loop - checks condition first
let x = 10;
while (x < 5) {
  console.log(x); // Never executes
}

// do...while - executes first, then checks
let y = 10;
do {
  console.log(y); // Executes once: 10
} while (y < 5);
```

---

## For...In Loop

The `for...in` loop iterates over all enumerable properties of an object.

### Syntax
```javascript
for (let key in object) {
  // Code to execute for each property
}
```

### Object Example
```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}
// Output:
// name: John
// age: 30
// city: New York
```

### Array Example (Not Recommended for Arrays!)
```javascript
const colors = ['Red', 'Green', 'Blue'];

for (let index in colors) {
  console.log(index + ': ' + colors[index]);
}
// Output:
// 0: Red
// 1: Green
// 2: Blue

// ⚠️ Problem: for...in also iterates inherited properties
// Use for...of for arrays instead (see below)
```

### Nested for...in
```javascript
const users = {
  user1: { name: 'Alice', age: 25 },
  user2: { name: 'Bob', age: 30 }
};

for (let userId in users) {
  console.log(`${userId}:`);
  for (let prop in users[userId]) {
    console.log(`  ${prop}: ${users[userId][prop]}`);
  }
}
// Output:
// user1:
//   name: Alice
//   age: 25
// user2:
//   name: Bob
//   age: 30
```

---

## For...Of Loop

The `for...of` loop iterates over values of iterable objects (arrays, strings, etc.).

### Syntax
```javascript
for (let value of iterable) {
  // Code to execute for each value
}
```

### Array Example
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

for (let fruit of fruits) {
  console.log(fruit);
}
// Output: Apple, Banana, Orange
```

### String Example
```javascript
const word = 'Hello';

for (let char of word) {
  console.log(char);
}
// Output: H, e, l, l, o
```

### Get Index and Value
```javascript
const colors = ['Red', 'Green', 'Blue'];

for (let [index, color] of colors.entries()) {
  console.log(`${index}: ${color}`);
}
// Output:
// 0: Red
// 1: Green
// 2: Blue
```

### for...of vs for...in
```javascript
const arr = ['a', 'b', 'c'];
arr.customProp = 'custom';

console.log('for...in:');
for (let i in arr) {
  console.log(i); // 0, 1, 2, customProp (includes all properties!)
}

console.log('\nfor...of:');
for (let item of arr) {
  console.log(item); // a, b, c (only values)
}
```

---

## Loop Control: Break & Continue

### Break Statement

Terminates the loop immediately.

```javascript
// Stop loop when number is found
for (let i = 1; i <= 10; i++) {
  if (i === 5) {
    console.log('Found 5! Stopping loop.');
    break;
  }
  console.log(i);
}
// Output: 1, 2, 3, 4, Found 5! Stopping loop.
```

### Continue Statement

Skips the current iteration and moves to the next one.

```javascript
// Skip even numbers
for (let i = 1; i <= 10; i++) {
  if (i % 2 === 0) {
    continue; // Skip this iteration
  }
  console.log(i);
}
// Output: 1, 3, 5, 7, 9
```

### Practical Examples

**Finding an item in array:**
```javascript
const items = [10, 20, 30, 40, 50];
let foundValue = null;

for (let item of items) {
  if (item === 30) {
    foundValue = item;
    break;
  }
}
console.log(foundValue); // 30
```

**Filtering with continue:**
```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

console.log('Numbers greater than 5:');
for (let num of numbers) {
  if (num <= 5) continue;
  console.log(num);
}
// Output: 6, 7, 8, 9, 10
```

---

## Nested Loops

Loops within loops - useful for multi-dimensional arrays and complex iterations.

### 2D Array (Times Table)
```javascript
// Create a multiplication table
for (let i = 1; i <= 3; i++) {
  let row = '';
  for (let j = 1; j <= 3; j++) {
    row += (i * j) + ' ';
  }
  console.log(row);
}
// Output:
// 1 2 3 
// 2 4 6 
// 3 6 9
```

### Array of Arrays
```javascript
const matrix = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];

// Print each element
for (let row of matrix) {
  for (let cell of row) {
    console.log(cell);
  }
}
// Output: 1, 2, 3, 4, 5, 6, 7, 8, 9
```

### Practical: Checking Duplicates
```javascript
const arr = [1, 2, 3, 2, 4, 5];

for (let i = 0; i < arr.length; i++) {
  for (let j = i + 1; j < arr.length; j++) {
    if (arr[i] === arr[j]) {
      console.log(`Duplicate found: ${arr[i]}`);
      break;
    }
  }
}
// Output: Duplicate found: 2
```

---

## Performance Tips

### Avoid Unnecessary Operations
```javascript
// ❌ Bad - length is calculated every iteration
for (let i = 0; i < array.length; i++) {
  console.log(array[i]);
}

// ✅ Good - length calculated once
const len = array.length;
for (let i = 0; i < len; i++) {
  console.log(array[i]);
}
```

### Cache Variables
```javascript
const data = {
  items: [1, 2, 3, 4, 5]
};

// ❌ Bad - accessing nested property repeatedly
for (let i = 0; i < data.items.length; i++) {
  console.log(data.items[i]);
}

// ✅ Good - cache the array
const items = data.items;
for (let i = 0; i < items.length; i++) {
  console.log(items[i]);
}
```

### Use Modern Array Methods Instead
```javascript
const numbers = [1, 2, 3, 4, 5];

// Instead of for loop
for (let i = 0; i < numbers.length; i++) {
  console.log(numbers[i] * 2);
}

// Use forEach (more readable)
numbers.forEach(num => console.log(num * 2));

// Use map (returns new array)
const doubled = numbers.map(num => num * 2);
```

---

## Exercises

### Exercise 1: Sum Numbers
Create a loop that sums all numbers from 1 to 100.

**Solution:**
```javascript
let sum = 0;
for (let i = 1; i <= 100; i++) {
  sum += i;
}
console.log(sum); // 5050
```

### Exercise 2: Count Vowels
Count the vowels in a given string.

**Solution:**
```javascript
const text = 'Hello World';
let vowelCount = 0;
const vowels = 'aeiouAEIOU';

for (let char of text) {
  if (vowels.includes(char)) {
    vowelCount++;
  }
}
console.log(vowelCount); // 3
```

### Exercise 3: Print Pattern
Print a pyramid pattern:
```
*
**
***
****
*****
```

**Solution:**
```javascript
for (let i = 1; i <= 5; i++) {
  let row = '';
  for (let j = 1; j <= i; j++) {
    row += '*';
  }
  console.log(row);
}
```

### Exercise 4: Find Prime Numbers
Find all prime numbers from 2 to 20.

**Solution:**
```javascript
for (let num = 2; num <= 20; num++) {
  let isPrime = true;
  
  for (let i = 2; i < num; i++) {
    if (num % i === 0) {
      isPrime = false;
      break;
    }
  }
  
  if (isPrime) {
    console.log(num);
  }
}
// Output: 2, 3, 5, 7, 11, 13, 17, 19
```

---

## Next Steps

→ [Switch Statements](./03-switch-statements.md)  
→ [Functions](../04-FUNCTIONS/01-function-basics.md)  
→ [Back to Control Flow](./README.md)
