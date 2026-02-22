# Classes and Prototypes in JavaScript

Object-Oriented Programming in JavaScript using classes and prototypes is essential for building larger applications.

## Table of Contents
- [ES6 Classes](#es6-classes)
- [Constructors](#constructors)
- [Properties and Methods](#properties-and-methods)
- [Inheritance](#inheritance)
- [Static Members](#static-members)
- [Prototypes](#prototypes)
- [Practical Examples](#practical-examples)
- [Exercises](#exercises)

---

## ES6 Classes

ES6 introduced a cleaner class syntax (though JavaScript is still prototype-based).

### Basic Class
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
  
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }
}

const person = new Person('John', 30);
person.greet(); // Hello, I'm John
```

### Class Expression
```javascript
const Car = class {
  constructor(brand) {
    this.brand = brand;
  }
  
  describe() {
    return `This is a ${this.brand}`;
  }
};

const myCar = new Car('Toyota');
console.log(myCar.describe()); // This is a Toyota
```

---

## Constructors

The constructor method runs when you create a new instance.

### Constructor Basics
```javascript
class User {
  constructor(username, email) {
    this.username = username;
    this.email = email;
    this.createdAt = new Date();
  }
}

const user = new User('john_doe', 'john@example.com');
console.log(user.username); // john_doe
console.log(user.createdAt); // Current date
```

### Constructor with Default Values
```javascript
class Account {
  constructor(name, balance = 0) {
    this.name = name;
    this.balance = balance;
  }
}

const account1 = new Account('Savings');
const account2 = new Account('Checking', 5000);

console.log(account1.balance); // 0
console.log(account2.balance); // 5000
```

---

## Properties and Methods

### Instance Properties
```javascript
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
    this.inStock = true;
  }
}

const product = new Product('Laptop', 999);
product.inStock = false;
console.log(product); // { name: 'Laptop', price: 999, inStock: false }
```

### Instance Methods
```javascript
class Calculator {
  add(a, b) {
    return a + b;
  }
  
  subtract(a, b) {
    return a - b;
  }
  
  multiply(a, b) {
    return a * b;
  }
}

const calc = new Calculator();
console.log(calc.add(5, 3));       // 8
console.log(calc.multiply(5, 3));  // 15
```

### Getter and Setter
```javascript
class Person {
  constructor(firstName, lastName) {
    this._firstName = firstName;
    this._lastName = lastName;
  }
  
  get fullName() {
    return `${this._firstName} ${this._lastName}`;
  }
  
  set fullName(name) {
    const [first, last] = name.split(' ');
    this._firstName = first;
    this._lastName = last;
  }
}

const person = new Person('John', 'Doe');
console.log(person.fullName); // John Doe

person.fullName = 'Jane Smith';
console.log(person._firstName); // Jane
```

---

## Inheritance

Create specialized classes from base classes.

### Extending Classes
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
  
  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks`);
  }
}

const dog = new Dog('Rex');
dog.speak(); // Rex barks
```

### Using Super
```javascript
class Vehicle {
  constructor(brand) {
    this.brand = brand;
  }
  
  start() {
    console.log(`${this.brand} is starting`);
  }
}

class Car extends Vehicle {
  constructor(brand, model) {
    super(brand);      // Call parent constructor
    this.model = model;
  }
  
  start() {
    super.start();     // Call parent method
    console.log(`${this.model} engine is running`);
  }
}

const car = new Car('Toyota', 'Camry');
car.start();
// Toyota is starting
// Camry engine is running
```

### Multi-level Inheritance
```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Mammal extends Animal {
  constructor(name, furColor) {
    super(name);
    this.furColor = furColor;
  }
}

class Dog extends Mammal {
  constructor(name, furColor, breed) {
    super(name, furColor);
    this.breed = breed;
  }
  
  describe() {
    return `${this.name} is a ${this.breed} with ${this.furColor} fur`;
  }
}

const dog = new Dog('Buddy', 'brown', 'Labrador');
console.log(dog.describe());
// Buddy is a Labrador with brown fur
```

---

## Static Members

Static methods and properties belong to the class, not instances.

### Static Methods
```javascript
class MathHelper {
  static add(a, b) {
    return a + b;
  }
  
  static multiply(a, b) {
    return a * b;
  }
}

console.log(MathHelper.add(5, 3));      // 8
console.log(MathHelper.multiply(5, 3)); // 15

const helper = new MathHelper();
// helper.add(5, 3); // Error - static methods not on instances
```

### Static Properties
```javascript
class Counter {
  static count = 0;
  
  constructor(name) {
    this.name = name;
    Counter.count++;
  }
  
  static getCount() {
    return Counter.count;
  }
}

new Counter('Item 1');
new Counter('Item 2');
new Counter('Item 3');

console.log(Counter.getCount()); // 3
```

### Practical: Configuration Class
```javascript
class Config {
  static API_URL = 'https://api.example.com';
  static API_KEY = 'secret-key';
  static DEBUG = false;
  
  static getEndpoint(path) {
    return `${this.API_URL}/${path}`;
  }
}

console.log(Config.getEndpoint('users')); 
// https://api.example.com/users
```

---

## Prototypes

JavaScript uses prototypal inheritance at its core.

### Prototype Chain
```javascript
function Person(name) {
  this.name = name;
}

Person.prototype.greet = function() {
  console.log(`Hello, I'm ${this.name}`);
};

const john = new Person('John');
john.greet(); // Hello, I'm John

// john doesn't have greet(), but it inherits from Person.prototype
console.log(john.hasOwnProperty('greet'));        // false
console.log('greet' in john);                     // true
```

### Prototype Inheritance
```javascript
function Animal(name) {
  this.name = name;
}

Animal.prototype.speak = function() {
  console.log(`${this.name} makes a sound`);
};

function Dog(name, breed) {
  Animal.call(this, name);
  this.breed = breed;
}

Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog;

Dog.prototype.speak = function() {
  console.log(`${this.name} barks`);
};

const dog = new Dog('Rex', 'Labrador');
dog.speak(); // Rex barks
```

### Checking Prototype
```javascript
class Vehicle {}
class Car extends Vehicle {}

const car = new Car();

console.log(car instanceof Car);     // true
console.log(car instanceof Vehicle); // true
console.log(car instanceof Object);  // true

console.log(Object.getPrototypeOf(car)); // Car.prototype
```

---

## Practical Examples

### Bank Account Class
```javascript
class BankAccount {
  constructor(accountHolder, balance = 0) {
    this.accountHolder = accountHolder;
    this._balance = balance;
    this.transactions = [];
  }
  
  deposit(amount) {
    if (amount > 0) {
      this._balance += amount;
      this.transactions.push({ type: 'deposit', amount });
      return `Deposited $${amount}. New balance: $${this._balance}`;
    }
    return 'Deposit amount must be positive';
  }
  
  withdraw(amount) {
    if (amount > this._balance) {
      return 'Insufficient funds';
    }
    this._balance -= amount;
    this.transactions.push({ type: 'withdrawal', amount });
    return `Withdrew $${amount}. New balance: $${this._balance}`;
  }
  
  get balance() {
    return this._balance;
  }
  
  getStatement() {
    return this.transactions;
  }
}

const account = new BankAccount('Alice', 1000);
console.log(account.deposit(500));      // Deposited $500. New balance: $1500
console.log(account.withdraw(200));     // Withdrew $200. New balance: $1300
console.log(account.balance);           // 1300
console.log(account.getStatement());    // All transactions
```

### Shape Hierarchy
```javascript
class Shape {
  constructor(color) {
    this.color = color;
  }
  
  describe() {
    return `A ${this.color} shape`;
  }
}

class Circle extends Shape {
  constructor(color, radius) {
    super(color);
    this.radius = radius;
  }
  
  getArea() {
    return Math.PI * this.radius ** 2;
  }
  
  describe() {
    return `${super.describe()} - Circle with radius ${this.radius}`;
  }
}

class Rectangle extends Shape {
  constructor(color, width, height) {
    super(color);
    this.width = width;
    this.height = height;
  }
  
  getArea() {
    return this.width * this.height;
  }
}

const circle = new Circle('blue', 5);
const rect = new Rectangle('red', 4, 6);

console.log(circle.describe());  // A blue shape - Circle with radius 5
console.log(circle.getArea());   // 78.53981633974483
console.log(rect.getArea());     // 24
```

---

## Exercises

### Exercise 1: Create a Student Class
Create a Student class with name, grade, and a method to display info.

**Solution:**
```javascript
class Student {
  constructor(name, grade) {
    this.name = name;
    this.grade = grade;
  }
  
  displayInfo() {
    return `${this.name} is in grade ${this.grade}`;
  }
}

const student = new Student('John', 'A');
console.log(student.displayInfo()); // John is in grade A
```

### Exercise 2: Create an Employee and Manager Hierarchy
Create Employee class and Manager extends Employee.

**Solution:**
```javascript
class Employee {
  constructor(name, salary) {
    this.name = name;
    this.salary = salary;
  }
  
  getInfo() {
    return `${this.name} earns $${this.salary}`;
  }
}

class Manager extends Employee {
  constructor(name, salary, department) {
    super(name, salary);
    this.department = department;
  }
  
  getInfo() {
    return `${super.getInfo()} in ${this.department}`;
  }
}

const manager = new Manager('Alice', 80000, 'Engineering');
console.log(manager.getInfo());
// Alice earns $80000 in Engineering
```

---

## Next Steps

→ [Back to OOP](./README.md)  
→ [Asynchronous JavaScript](../07-ASYNC/README.md)
