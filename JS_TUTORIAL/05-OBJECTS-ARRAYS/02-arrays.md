# Arrays in JavaScript

Arrays are ordered collections of elements. They're one of the most important data structures in JavaScript.

## Table of Contents
- [Creating Arrays](#creating-arrays)
- [Accessing Elements](#accessing-elements)
- [Modifying Arrays](#modifying-arrays)
- [Array Methods](#array-methods)
- [Iterating Arrays](#iterating-arrays)
- [Higher Order Functions](#higher-order-functions)
- [Destructuring Arrays](#destructuring-arrays)
- [Exercises](#exercises)

---

## Creating Arrays

### Array Literal
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];
console.log(fruits); // ['Apple', 'Banana', 'Orange']
```

### Array Constructor
```javascript
const numbers = new Array(1, 2, 3, 4, 5);
console.log(numbers); // [1, 2, 3, 4, 5]
```

### Array with Mixed Types
```javascript
const mixed = [1, 'two', true, null, { name: 'John' }, [1, 2]];
console.log(mixed);
// [1, 'two', true, null, {name: 'John'}, [1, 2]]
```

### Empty Array
```javascript
const empty = [];
console.log(empty); // []
console.log(empty.length); // 0
```

### Array with Length
```javascript
const arr = new Array(3);
console.log(arr.length); // 3
console.log(arr); // [empty × 3]
```

---

## Accessing Elements

### By Index
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

console.log(fruits[0]); // Apple
console.log(fruits[1]); // Banana
console.log(fruits[2]); // Orange
console.log(fruits[3]); // undefined
```

### Last Element
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

// Method 1
console.log(fruits[fruits.length - 1]); // Orange

// Method 2 (ES2022)
console.log(fruits.at(-1)); // Orange
console.log(fruits.at(-2)); // Banana
```

### Length Property
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

console.log(fruits.length); // 3

// You can also set length (be careful!)
fruits.length = 2;
console.log(fruits); // ['Apple', 'Banana']
```

---

## Modifying Arrays

### Adding Elements

**Push (end)**
```javascript
const fruits = ['Apple', 'Banana'];
fruits.push('Orange');
console.log(fruits); // ['Apple', 'Banana', 'Orange']

fruits.push('Mango', 'Pineapple');
console.log(fruits); // ['Apple', 'Banana', 'Orange', 'Mango', 'Pineapple']
```

**Unshift (beginning)**
```javascript
const fruits = ['Apple', 'Banana'];
fruits.unshift('Orange');
console.log(fruits); // ['Orange', 'Apple', 'Banana']
```

### Removing Elements

**Pop (end)**
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];
const last = fruits.pop();
console.log(last);   // Orange
console.log(fruits); // ['Apple', 'Banana']
```

**Shift (beginning)**
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];
const first = fruits.shift();
console.log(first);  // Apple
console.log(fruits); // ['Banana', 'Orange']
```

**Splice (any position)**
```javascript
const fruits = ['Apple', 'Banana', 'Orange', 'Mango'];

// Remove 2 elements starting at index 1
const removed = fruits.splice(1, 2);
console.log(removed); // ['Banana', 'Orange']
console.log(fruits);  // ['Apple', 'Mango']

// Insert without removing
fruits.splice(1, 0, 'Pineapple', 'Grape');
console.log(fruits); // ['Apple', 'Pineapple', 'Grape', 'Mango']
```

### Replacing Elements
```javascript
const colors = ['Red', 'Green', 'Blue'];

// Replace one element
colors[1] = 'Yellow';
console.log(colors); // ['Red', 'Yellow', 'Blue']

// Replace multiple with splice
colors.splice(1, 1, 'Orange', 'Purple');
console.log(colors); // ['Red', 'Orange', 'Purple', 'Blue']
```

---

## Array Methods

### Finding Elements

**indexOf**
```javascript
const fruits = ['Apple', 'Banana', 'Orange', 'Apple'];

console.log(fruits.indexOf('Apple'));  // 0 (first occurrence)
console.log(fruits.indexOf('Orange')); // 2
console.log(fruits.indexOf('Mango'));  // -1 (not found)
```

**includes**
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

console.log(fruits.includes('Apple'));  // true
console.log(fruits.includes('Mango'));  // false
```

**find**
```javascript
const users = [
  { id: 1, name: 'John' },
  { id: 2, name: 'Jane' },
  { id: 3, name: 'Bob' }
];

const user = users.find(u => u.id === 2);
console.log(user); // { id: 2, name: 'Jane' }
```

**findIndex**
```javascript
const numbers = [10, 20, 30, 40, 50];

const index = numbers.findIndex(num => num > 25);
console.log(index); // 2 (index of 30)
```

### Transforming Arrays

**map**
```javascript
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(num => num * 2);
console.log(doubled); // [2, 4, 6, 8, 10]

// With objects
const users = [
  { name: 'John', age: 30 },
  { name: 'Jane', age: 25 }
];
const names = users.map(user => user.name);
console.log(names); // ['John', 'Jane']
```

**filter**
```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
const evens = numbers.filter(num => num % 2 === 0);
console.log(evens); // [2, 4, 6, 8, 10]

// Filter objects
const users = [
  { name: 'John', active: true },
  { name: 'Jane', active: false },
  { name: 'Bob', active: true }
];
const activeUsers = users.filter(user => user.active);
console.log(activeUsers);
// [{ name: 'John', active: true }, { name: 'Bob', active: true }]
```

**reduce**
```javascript
const numbers = [1, 2, 3, 4, 5];

// Sum all numbers
const sum = numbers.reduce((acc, num) => acc + num, 0);
console.log(sum); // 15

// Product of all numbers
const product = numbers.reduce((acc, num) => acc * num, 1);
console.log(product); // 120

// Group by property
const ages = [20, 30, 25, 35, 28];
const ageGroups = ages.reduce((acc, age) => {
  const group = age < 30 ? 'young' : 'old';
  acc[group] = (acc[group] || 0) + 1;
  return acc;
}, {});
console.log(ageGroups); // { young: 3, old: 2 }
```

### Sorting and Reversing

**sort**
```javascript
const numbers = [3, 1, 4, 1, 5, 9, 2, 6];
numbers.sort((a, b) => a - b);
console.log(numbers); // [1, 1, 2, 3, 4, 5, 6, 9]

// Strings
const fruits = ['banana', 'apple', 'cherry'];
fruits.sort();
console.log(fruits); // ['apple', 'banana', 'cherry']

// Objects
const users = [
  { name: 'John', age: 30 },
  { name: 'Jane', age: 25 },
  { name: 'Bob', age: 28 }
];
users.sort((a, b) => a.age - b.age);
console.log(users);
// [{ name: 'Jane', age: 25 }, { name: 'Bob', age: 28 }, { name: 'John', age: 30 }]
```

**reverse**
```javascript
const numbers = [1, 2, 3, 4, 5];
numbers.reverse();
console.log(numbers); // [5, 4, 3, 2, 1]
```

### Other Methods

**join**
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

console.log(fruits.join(', ')); // Apple, Banana, Orange
console.log(fruits.join(' - ')); // Apple - Banana - Orange
console.log(fruits.join(''));  // AppleBananaOrange
```

**slice**
```javascript
const numbers = [1, 2, 3, 4, 5];

console.log(numbers.slice(1, 3)); // [2, 3]
console.log(numbers.slice(2));    // [3, 4, 5]
console.log(numbers.slice(-2));   // [4, 5]
console.log(numbers.slice());     // [1, 2, 3, 4, 5] (copy)
```

**concat**
```javascript
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

const combined = arr1.concat(arr2);
console.log(combined); // [1, 2, 3, 4, 5, 6]

// With spread operator (modern)
const combined2 = [...arr1, ...arr2];
console.log(combined2); // [1, 2, 3, 4, 5, 6]
```

**some and every**
```javascript
const numbers = [1, 2, 3, 4, 5];

// Some - returns true if at least one element passes test
const hasEven = numbers.some(num => num % 2 === 0);
console.log(hasEven); // true

// Every - returns true if all elements pass test
const allPositive = numbers.every(num => num > 0);
console.log(allPositive); // true

const allEven = numbers.every(num => num % 2 === 0);
console.log(allEven); // false
```

---

## Iterating Arrays

### forEach
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

fruits.forEach((fruit, index) => {
  console.log(`${index + 1}: ${fruit}`);
});
// Output:
// 1: Apple
// 2: Banana
// 3: Orange
```

### for...of
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

for (let fruit of fruits) {
  console.log(fruit);
}
// Output: Apple, Banana, Orange
```

### for...in
```javascript
const fruits = ['Apple', 'Banana', 'Orange'];

for (let index in fruits) {
  console.log(`${index}: ${fruits[index]}`);
}
// Output:
// 0: Apple
// 1: Banana
// 2: Orange
```

---

## Higher Order Functions

Chaining array methods:

```javascript
const users = [
  { name: 'John', age: 30, active: true },
  { name: 'Jane', age: 25, active: false },
  { name: 'Bob', age: 28, active: true },
  { name: 'Alice', age: 35, active: true }
];

// Filter active users, map to names, sort alphabetically
const result = users
  .filter(user => user.active)
  .map(user => user.name)
  .sort();

console.log(result); // ['Alice', 'Bob', 'John']
```

**Complex Example:**
```javascript
const products = [
  { name: 'Laptop', price: 1000, category: 'Electronics' },
  { name: 'Mouse', price: 30, category: 'Electronics' },
  { name: 'Book', price: 20, category: 'Books' },
  { name: 'Keyboard', price: 80, category: 'Electronics' },
  { name: 'Monitor', price: 300, category: 'Electronics' }
];

// Get total price of Electronics
const electronicsTotal = products
  .filter(p => p.category === 'Electronics')
  .map(p => p.price)
  .reduce((sum, price) => sum + price, 0);

console.log(electronicsTotal); // 1410
```

---

## Destructuring Arrays

### Basic Destructuring
```javascript
const [a, b, c] = [1, 2, 3];
console.log(a); // 1
console.log(b); // 2
console.log(c); // 3
```

### Skipping Elements
```javascript
const [first, , third] = [1, 2, 3];
console.log(first); // 1
console.log(third); // 3
```

### Rest Element
```javascript
const [first, ...rest] = [1, 2, 3, 4, 5];
console.log(first); // 1
console.log(rest);  // [2, 3, 4, 5]
```

### Default Values
```javascript
const [a, b, c = 'default'] = [1, 2];
console.log(a); // 1
console.log(b); // 2
console.log(c); // 'default'
```

### Swapping Variables
```javascript
let x = 10;
let y = 20;

[x, y] = [y, x];
console.log(x); // 20
console.log(y); // 10
```

---

## Practical Examples

### Student Grades
```javascript
const grades = [85, 92, 78, 88, 95];

const average = grades.reduce((sum, grade) => sum + grade, 0) / grades.length;
const highest = Math.max(...grades);
const lowest = Math.min(...grades);
const passing = grades.filter(grade => grade >= 80);

console.log(`Average: ${average}`);      // Average: 87.6
console.log(`Highest: ${highest}`);      // Highest: 95
console.log(`Lowest: ${lowest}`);        // Lowest: 78
console.log(`Passing: ${passing}`);      // Passing: 85, 92, 88, 95
```

### Data Transformation
```javascript
const data = [
  { id: 1, name: 'Product A', price: 100 },
  { id: 2, name: 'Product B', price: 200 },
  { id: 3, name: 'Product C', price: 150 }
];

const result = data
  .filter(item => item.price > 100)
  .map(item => ({
    ...item,
    discountedPrice: item.price * 0.9
  }));

console.log(result);
// [{id: 2, name: 'Product B', price: 200, discountedPrice: 180},
//  {id: 3, name: 'Product C', price: 150, discountedPrice: 135}]
```

---

## Exercises

### Exercise 1: Sum Array Elements
Create a function that returns the sum of all elements in an array.

**Solution:**
```javascript
function sumArray(arr) {
  return arr.reduce((sum, num) => sum + num, 0);
}

console.log(sumArray([1, 2, 3, 4, 5])); // 15
```

### Exercise 2: Remove Duplicates
Create a function that removes duplicates from an array.

**Solution:**
```javascript
function removeDuplicates(arr) {
  return [...new Set(arr)];
}

console.log(removeDuplicates([1, 2, 2, 3, 3, 4])); // [1, 2, 3, 4]
```

### Exercise 3: Flatten Nested Array
Create a function that flattens a nested array.

**Solution:**
```javascript
function flatten(arr) {
  return arr.reduce((acc, val) => 
    acc.concat(Array.isArray(val) ? flatten(val) : val), []);
}

console.log(flatten([1, [2, [3, 4]], 5])); // [1, 2, 3, 4, 5]
```

---

## Next Steps

→ [Back to Objects & Arrays](./README.md)  
→ [Functions](../04-FUNCTIONS/01-function-basics.md)
