# Objects in JavaScript

Objects are containers for named values called properties and methods. They're fundamental to JavaScript and used everywhere.

## Table of Contents
- [Creating Objects](#creating-objects)
- [Accessing Properties](#accessing-properties)
- [Modifying Properties](#modifying-properties)
- [Methods](#methods)
- [Destructuring](#destructuring)
- [This Keyword](#this-keyword)
- [Object Methods](#object-methods)
- [Exercises](#exercises)

---

## Creating Objects

### Object Literal
```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York',
  email: 'john@example.com'
};

console.log(person);
// { name: 'John', age: 30, city: 'New York', email: 'john@example.com' }
```

### Empty Object
```javascript
const emptyObj = {};
console.log(emptyObj); // {}
```

### Constructor Function
```javascript
const person = new Object();
person.name = 'John';
person.age = 30;

console.log(person); // { name: 'John', age: 30 }
```

### Nested Objects
```javascript
const person = {
  name: 'John',
  age: 30,
  address: {
    street: '123 Main St',
    city: 'New York',
    zip: '10001'
  },
  contact: {
    email: 'john@example.com',
    phone: '555-1234'
  }
};

console.log(person.address.city); // New York
```

---

## Accessing Properties

### Dot Notation
```javascript
const person = {
  name: 'Alice',
  age: 25,
  city: 'Boston'
};

console.log(person.name); // Alice
console.log(person.age);  // 25
console.log(person.city); // Boston
```

### Bracket Notation
```javascript
const person = {
  name: 'Alice',
  age: 25,
  'favorite-color': 'blue'
};

console.log(person['name']);           // Alice
console.log(person['age']);            // 25
console.log(person['favorite-color']); // blue (can't use dot for hyphens)
```

### Dynamic Access
```javascript
const person = {
  name: 'Alice',
  age: 25,
  job: 'Developer'
};

const key = 'name';
console.log(person[key]); // Alice

// Useful in loops
for (let key in person) {
  console.log(`${key}: ${person[key]}`);
}
// Output:
// name: Alice
// age: 25
// job: Developer
```

### Checking if Property Exists
```javascript
const person = { name: 'John', age: 30 };

console.log('name' in person);    // true
console.log('email' in person);   // false
console.log(person.hasOwnProperty('name'));  // true
console.log(person.hasOwnProperty('email')); // false
```

---

## Modifying Properties

### Adding Properties
```javascript
const person = {
  name: 'John'
};

person.age = 30;
person['city'] = 'New York';

console.log(person);
// { name: 'John', age: 30, city: 'New York' }
```

### Changing Properties
```javascript
const person = {
  name: 'John',
  age: 30
};

person.name = 'Jane';
person['age'] = 25;

console.log(person);
// { name: 'Jane', age: 25 }
```

### Deleting Properties
```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

delete person.city;

console.log(person);
// { name: 'John', age: 30 }
```

### Merging Objects
```javascript
const obj1 = { a: 1, b: 2 };
const obj2 = { c: 3, d: 4 };

// Using spread operator
const merged = { ...obj1, ...obj2 };
console.log(merged);
// { a: 1, b: 2, c: 3, d: 4 }

// Using Object.assign()
const merged2 = Object.assign({}, obj1, obj2);
console.log(merged2);
// { a: 1, b: 2, c: 3, d: 4 }
```

---

## Methods

Methods are functions stored as object properties.

### Creating Methods
```javascript
const person = {
  name: 'John',
  age: 30,
  greet: function() {
    return `Hello, I'm ${this.name}`;
  },
  celebrateBirthday() {
    this.age++;
    return `Happy birthday! I'm now ${this.age}`;
  }
};

console.log(person.greet()); // Hello, I'm John
console.log(person.celebrateBirthday()); // Happy birthday! I'm now 31
```

### Method Examples
```javascript
const calculator = {
  num1: 10,
  num2: 5,
  add: function() {
    return this.num1 + this.num2;
  },
  subtract: function() {
    return this.num1 - this.num2;
  },
  multiply: function() {
    return this.num1 * this.num2;
  },
  divide: function() {
    return this.num1 / this.num2;
  }
};

console.log(calculator.add());      // 15
console.log(calculator.multiply()); // 50
```

---

## Destructuring

Destructuring extracts values from objects and assigns them to variables.

### Basic Destructuring
```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

// Old way
const name = person.name;
const age = person.age;

// Destructuring way
const { name, age } = person;
console.log(name); // John
console.log(age);  // 30
```

### Renaming Variables
```javascript
const person = {
  name: 'John',
  age: 30
};

const { name: personName, age: personAge } = person;
console.log(personName); // John
console.log(personAge);  // 30
```

### Default Values
```javascript
const person = {
  name: 'John'
};

const { name, age = 25 } = person;
console.log(name); // John
console.log(age);  // 25 (default value)
```

### Nested Destructuring
```javascript
const person = {
  name: 'John',
  address: {
    street: '123 Main St',
    city: 'New York'
  }
};

const { name, address: { city } } = person;
console.log(name); // John
console.log(city); // New York
```

### Function Parameters
```javascript
function displayPerson({ name, age, city }) {
  console.log(`${name} is ${age} years old and lives in ${city}`);
}

displayPerson({
  name: 'Alice',
  age: 25,
  city: 'Boston'
});
// Output: Alice is 25 years old and lives in Boston
```

---

## This Keyword

The `this` keyword refers to the object that owns the method.

### In Methods
```javascript
const person = {
  name: 'John',
  age: 30,
  greet: function() {
    console.log(this.name); // refers to person
  }
};

person.greet(); // John
```

### Common Mistakes
```javascript
const person = {
  name: 'John',
  greet: function() {
    // 'this' refers to person
    console.log(this.name);
  },
  greetArrow: () => {
    // Arrow functions don't have their own 'this'
    // 'this' refers to the global object
    console.log(this);
  }
};

person.greet();      // John
person.greetArrow(); // Window (browser) or undefined (Node.js)
```

### Explicit This Binding
```javascript
function introduce() {
  return `Hi, I'm ${this.name}`;
}

const person = { name: 'Alice' };

// Using call()
console.log(introduce.call(person)); // Hi, I'm Alice

// Using apply()
console.log(introduce.apply(person)); // Hi, I'm Alice

// Using bind()
const boundIntro = introduce.bind(person);
console.log(boundIntro()); // Hi, I'm Alice
```

---

## Object Methods

### Object.keys()
```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

const keys = Object.keys(person);
console.log(keys); // ['name', 'age', 'city']
```

### Object.values()
```javascript
const person = {
  name: 'John',
  age: 30,
  city: 'New York'
};

const values = Object.values(person);
console.log(values); // ['John', 30, 'New York']
```

### Object.entries()
```javascript
const person = {
  name: 'John',
  age: 30
};

const entries = Object.entries(person);
console.log(entries);
// [['name', 'John'], ['age', 30]]

// Useful for converting to Map
const map = new Map(entries);
console.log(map.get('name')); // John
```

### Object.assign()
```javascript
const target = { a: 1, b: 2 };
const source = { b: 3, c: 4 };

const result = Object.assign(target, source);
console.log(result); // { a: 1, b: 3, c: 4 }
console.log(target); // { a: 1, b: 3, c: 4 } (modified!)
```

### Object.freeze()
```javascript
const person = {
  name: 'John',
  age: 30
};

Object.freeze(person);

person.name = 'Jane'; // Silently fails (or error in strict mode)
person.email = 'john@example.com'; // Silently fails

console.log(person); // { name: 'John', age: 30 }
```

### Object.seal()
```javascript
const person = {
  name: 'John',
  age: 30
};

Object.seal(person);

person.name = 'Jane'; // OK - can modify
person.email = 'john@example.com'; // Error - can't add new properties

console.log(person); // { name: 'Jane', age: 30 }
```

---

## Practical Examples

### User Profile
```javascript
const user = {
  id: 1,
  username: 'john_doe',
  email: 'john@example.com',
  profile: {
    firstName: 'John',
    lastName: 'Doe',
    bio: 'Full stack developer',
    avatar: 'https://example.com/avatar.jpg'
  },
  settings: {
    theme: 'dark',
    notifications: true,
    language: 'en'
  },
  updateProfile: function(firstName, lastName) {
    this.profile.firstName = firstName;
    this.profile.lastName = lastName;
  },
  changeTheme: function(theme) {
    this.settings.theme = theme;
  }
};

user.updateProfile('Jane', 'Smith');
console.log(user.profile.firstName); // Jane
```

### Product Object
```javascript
const product = {
  id: 101,
  name: 'Laptop',
  price: 999.99,
  stock: 5,
  category: 'Electronics',
  getDiscountedPrice: function(discountPercent) {
    return this.price * (1 - discountPercent / 100);
  },
  isInStock: function() {
    return this.stock > 0;
  }
};

console.log(product.getDiscountedPrice(10)); // 899.991
console.log(product.isInStock()); // true
```

---

## Exercises

### Exercise 1: Create a Book Object
Create an object with properties: title, author, pages, read. Add a method to check if it's been read.

**Solution:**
```javascript
const book = {
  title: 'JavaScript Basics',
  author: 'John Smith',
  pages: 300,
  read: false,
  markAsRead: function() {
    this.read = true;
    return `${this.title} has been marked as read`;
  }
};

console.log(book.markAsRead()); // JavaScript Basics has been marked as read
console.log(book.read); // true
```

### Exercise 2: Create a Car Object
Create a car object with brand, model, year, and a method to display full info.

**Solution:**
```javascript
const car = {
  brand: 'Toyota',
  model: 'Camry',
  year: 2023,
  displayInfo: function() {
    return `${this.year} ${this.brand} ${this.model}`;
  }
};

console.log(car.displayInfo()); // 2023 Toyota Camry
```

---

## Next Steps

→ [Arrays](./02-arrays.md)  
→ [Back to Objects & Arrays](./README.md)
