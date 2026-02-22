# Error Handling in JavaScript

Proper error handling is crucial for writing robust applications that handle unexpected situations gracefully.

## Table of Contents
- [Try...Catch...Finally](#trycatchfinally)
- [Error Types](#error-types)
- [Throwing Errors](#throwing-errors)
- [Error Objects](#error-objects)
- [Best Practices](#best-practices)
- [Exercises](#exercises)

---

## Try...Catch...Finally

The try...catch...finally statement handles errors that occur during code execution.

### Basic Syntax
```javascript
try {
  // Code that might throw an error
} catch (error) {
  // Code that runs if error occurs
} finally {
  // Code that always runs (optional)
}
```

### Try...Catch Example
```javascript
try {
  const result = JSON.parse('invalid json');
} catch (error) {
  console.log('Error caught:', error.message);
}
console.log('Program continues'); // Still executes

// Output:
// Error caught: Unexpected token i in JSON at position 0
// Program continues
```

### With Finally Block
```javascript
function processFile() {
  const file = openFile();
  
  try {
    readData(file);
    return true;
  } catch (error) {
    console.log('Error:', error.message);
    return false;
  } finally {
    file.close(); // Always closes file
  }
}
```

### Multiple Catch Blocks
```javascript
try {
  // Some code
} catch (error) {
  if (error instanceof TypeError) {
    console.log('Type Error:', error.message);
  } else if (error instanceof ReferenceError) {
    console.log('Reference Error:', error.message);
  } else {
    console.log('Unknown error:', error.message);
  }
}
```

### Catching Different Error Types
```javascript
try {
  // Various operations
} catch (error) {
  switch (error.name) {
    case 'SyntaxError':
      console.log('Invalid syntax');
      break;
    case 'ReferenceError':
      console.log('Variable not defined');
      break;
    case 'TypeError':
      console.log('Wrong type');
      break;
    default:
      console.log('Other error:', error.message);
  }
}
```

---

## Error Types

JavaScript has several built-in error types:

### TypeError
```javascript
// Accessing property of undefined
try {
  const obj = undefined;
  obj.property; // TypeError: Cannot read property 'property' of undefined
} catch (error) {
  console.log(error.name); // TypeError
  console.log(error.message); // Cannot read property 'property' of undefined
}

// Wrong argument type
try {
  const num = 'not a number';
  num.toFixed(2); // ✓ Actually works! But...
  
  const result = (null).toFixed(2); // TypeError
} catch (error) {
  console.log(error);
}
```

### ReferenceError
```javascript
try {
  console.log(undefinedVariable);
} catch (error) {
  console.log(error.name); // ReferenceError
  console.log(error.message); // undefinedVariable is not defined
}
```

### SyntaxError
```javascript
// SyntaxError - thrown during parsing (can't catch with try...catch)
// const x = ;  // SyntaxError
```

### RangeError
```javascript
try {
  const arr = new Array(-5); // RangeError: Invalid array length
} catch (error) {
  console.log(error.name); // RangeError
}
```

### Custom Error Type
```javascript
try {
  throw new Error('Custom error message');
} catch (error) {
  console.log(error.name); // Error
  console.log(error.message); // Custom error message
}
```

---

## Throwing Errors

You can throw your own errors using the `throw` statement.

### Throwing Basic Errors
```javascript
function validateAge(age) {
  if (age < 0) {
    throw new Error('Age cannot be negative');
  }
  if (age > 150) {
    throw new Error('Age seems invalid');
  }
  return true;
}

try {
  validateAge(-5);
} catch (error) {
  console.log(error.message); // Age cannot be negative
}
```

### Throwing Different Error Types
```javascript
function divide(a, b) {
  if (typeof a !== 'number' || typeof b !== 'number') {
    throw new TypeError('Both arguments must be numbers');
  }
  if (b === 0) {
    throw new RangeError('Cannot divide by zero');
  }
  return a / b;
}

try {
  divide(10, 'two');
} catch (error) {
  if (error instanceof TypeError) {
    console.log('Type error:', error.message);
  }
}
```

### Throwing Objects
```javascript
function loginUser(username, password) {
  if (!username) {
    throw {
      code: 'INVALID_USER',
      message: 'Username is required'
    };
  }
  if (!password) {
    throw {
      code: 'INVALID_PASS',
      message: 'Password is required'
    };
  }
}

try {
  loginUser('', 'password123');
} catch (error) {
  console.log(`[${error.code}] ${error.message}`);
}
```

---

## Error Objects

Error objects have useful properties and methods.

### Error Properties
```javascript
try {
  throw new Error('Something went wrong');
} catch (error) {
  console.log(error.name);    // Error
  console.log(error.message); // Something went wrong
  console.log(error.stack);   // Stack trace (browser dependent)
  
  // Stack trace shows where error occurred
  // Error: Something went wrong
  //     at <anonymous>:2:9
  //     at ...
}
```

### Creating Custom Error Classes
```javascript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = 'ValidationError';
  }
}

class DatabaseError extends Error {
  constructor(message) {
    super(message);
    this.name = 'DatabaseError';
  }
}

try {
  if (email === '') {
    throw new ValidationError('Email is required');
  }
} catch (error) {
  if (error instanceof ValidationError) {
    console.log('Validation failed:', error.message);
  }
}
```

---

## Best Practices

### 1. Be Specific with Errors
```javascript
// ❌ Too generic
try {
  // code
} catch (error) {
  console.log('Something went wrong');
}

// ✅ Be specific
try {
  const data = JSON.parse(jsonString);
} catch (error) {
  console.log('Invalid JSON:', error.message);
  // Handle invalid JSON specifically
}
```

### 2. Don't Ignore Errors
```javascript
// ❌ Bad - empty catch block
try {
  riskyOperation();
} catch (error) {
  // Silently fails!
}

// ✅ Good - handle or log error
try {
  riskyOperation();
} catch (error) {
  console.error('Operation failed:', error);
  // Handle error appropriately
}
```

### 3. Clean Up Resources
```javascript
function readFile(filename) {
  const file = openFile(filename);
  
  try {
    return file.read();
  } catch (error) {
    console.error('Failed to read file:', error);
    return null;
  } finally {
    file.close(); // Always close file
  }
}
```

### 4. Use Meaningful Error Messages
```javascript
// ❌ Unclear
throw new Error('Invalid input');

// ✅ Clear
throw new Error('Email must be in format user@domain.com');
```

### 5. Validate Input Early
```javascript
function processUser(user) {
  // Validate early
  if (!user || typeof user !== 'object') {
    throw new TypeError('User must be an object');
  }
  if (!user.email) {
    throw new Error('User must have email property');
  }
  if (!user.name) {
    throw new Error('User must have name property');
  }
  
  // Process user safely
  // ...
}
```

### 6. Error Recovery
```javascript
async function fetchUserData(userId) {
  const maxRetries = 3;
  let lastError;
  
  for (let i = 0; i < maxRetries; i++) {
    try {
      return await fetch(`/api/users/${userId}`);
    } catch (error) {
      lastError = error;
      console.log(`Attempt ${i + 1} failed, retrying...`);
    }
  }
  
  throw lastError; // Throw after all retries exhausted
}
```

---

## Practical Examples

### Validate Function Arguments
```javascript
function updateUser(id, data) {
  if (typeof id !== 'number' || id < 1) {
    throw new Error('ID must be a positive number');
  }
  
  if (!data || typeof data !== 'object') {
    throw new Error('Data must be an object');
  }
  
  if (!data.name || typeof data.name !== 'string') {
    throw new Error('Data must contain name string');
  }
  
  // Safe to proceed
  return { id, ...data, updated: new Date() };
}

try {
  updateUser(1, { name: 'John' });
} catch (error) {
  console.error(error.message);
}
```

### Safe JSON Parsing
```javascript
function safeJsonParse(jsonString, defaultValue = null) {
  try {
    return JSON.parse(jsonString);
  } catch (error) {
    console.warn('Invalid JSON, using default value:', error.message);
    return defaultValue;
  }
}

const data1 = safeJsonParse('{"valid": true}');      // Parsed
const data2 = safeJsonParse('invalid', {});          // Returns {}
const data3 = safeJsonParse('null', []);             // Returns []
```

### Chained Error Handling
```javascript
function processUserRegistration(userData) {
  try {
    // Validate
    if (!userData.email) throw new Error('Email required');
    if (!userData.password) throw new Error('Password required');
    
    // Process
    const user = createUser(userData);
    const verified = verifyEmail(user.email);
    
    if (!verified) throw new Error('Email verification failed');
    
    return user;
  } catch (error) {
    if (error.message === 'Email required') {
      return { success: false, field: 'email', message: error.message };
    }
    if (error.message === 'Password required') {
      return { success: false, field: 'password', message: error.message };
    }
    // Log other errors
    console.error('Registration error:', error);
    return { success: false, message: 'Registration failed' };
  }
}
```

---

## Exercises

### Exercise 1: Safe Divide Function
Create a function that safely divides two numbers with proper error handling.

**Solution:**
```javascript
function safeDivide(a, b) {
  try {
    if (typeof a !== 'number' || typeof b !== 'number') {
      throw new TypeError('Both arguments must be numbers');
    }
    if (b === 0) {
      throw new RangeError('Cannot divide by zero');
    }
    return a / b;
  } catch (error) {
    console.error(`Error: ${error.name} - ${error.message}`);
    return null;
  }
}

console.log(safeDivide(10, 2));    // 5
console.log(safeDivide(10, 0));    // null (error logged)
console.log(safeDivide(10, 'two')); // null (error logged)
```

### Exercise 2: User Validator
Create a function that validates user objects and throws appropriate errors.

**Solution:**
```javascript
function validateUser(user) {
  try {
    if (!user || typeof user !== 'object') {
      throw new TypeError('User must be an object');
    }
    if (!user.name || typeof user.name !== 'string') {
      throw new Error('User name must be a string');
    }
    if (!user.age || typeof user.age !== 'number') {
      throw new Error('User age must be a number');
    }
    if (user.age < 0 || user.age > 150) {
      throw new RangeError('User age must be between 0 and 150');
    }
    return true;
  } catch (error) {
    console.error(`Validation error: ${error.message}`);
    throw error;
  }
}

try {
  validateUser({ name: 'John', age: 30 });
  console.log('User is valid');
} catch (error) {
  console.log('User validation failed');
}
```

---

## Next Steps

→ [Variables and Types](./01-variables-types.md)  
→ [Back to Fundamentals](./README.md)
