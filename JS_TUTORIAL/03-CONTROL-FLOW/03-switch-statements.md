# Switch Statements

Switch statements are used to execute different code blocks for different conditions. They're cleaner than multiple if...else statements.

## Table of Contents
- [Basic Syntax](#basic-syntax)
- [How Switch Works](#how-switch-works)
- [Examples](#examples)
- [Break Statement](#break-statement)
- [Default Case](#default-case)
- [Switch vs If...Else](#switch-vs-ifelse)
- [Exercises](#exercises)

---

## Basic Syntax

```javascript
switch (expression) {
  case value1:
    // Code if expression === value1
    break;
  case value2:
    // Code if expression === value2
    break;
  default:
    // Code if no cases match
}
```

---

## How Switch Works

1. The expression is evaluated once
2. Its value is compared with each case
3. If a match is found, associated code executes
4. `break` stops execution
5. If no match, `default` case executes (optional)

### Example
```javascript
let day = 3;
let dayName;

switch (day) {
  case 1:
    dayName = 'Monday';
    break;
  case 2:
    dayName = 'Tuesday';
    break;
  case 3:
    dayName = 'Wednesday';
    break;
  case 4:
    dayName = 'Thursday';
    break;
  case 5:
    dayName = 'Friday';
    break;
  default:
    dayName = 'Weekend';
}

console.log(dayName); // Wednesday
```

---

## Examples

### 1. Grade Calculator
```javascript
let score = 85;
let grade;

switch (true) {
  case score >= 90:
    grade = 'A';
    break;
  case score >= 80:
    grade = 'B';
    break;
  case score >= 70:
    grade = 'C';
    break;
  case score >= 60:
    grade = 'D';
    break;
  default:
    grade = 'F';
}

console.log(grade); // B
```

### 2. User Role Permissions
```javascript
let userRole = 'admin';

switch (userRole) {
  case 'admin':
    console.log('Full access');
    console.log('Can create, edit, delete');
    break;
  case 'editor':
    console.log('Limited access');
    console.log('Can edit and create');
    break;
  case 'viewer':
    console.log('View only access');
    break;
  default:
    console.log('Unknown role');
}
// Output: Full access, Can create, edit, delete
```

### 3. Weather Checker
```javascript
let weather = 'rainy';

switch (weather) {
  case 'sunny':
    console.log('Wear sunscreen');
    console.log('Go to the beach');
    break;
  case 'rainy':
    console.log('Take an umbrella');
    console.log('Stay indoors');
    break;
  case 'snowy':
    console.log('Wear warm clothes');
    console.log('Drive carefully');
    break;
  default:
    console.log('Unknown weather');
}
// Output: Take an umbrella, Stay indoors
```

### 4. Calculator
```javascript
let num1 = 10;
let num2 = 5;
let operator = '+';

let result;

switch (operator) {
  case '+':
    result = num1 + num2;
    break;
  case '-':
    result = num1 - num2;
    break;
  case '*':
    result = num1 * num2;
    break;
  case '/':
    result = num1 / num2;
    break;
  default:
    result = 'Invalid operator';
}

console.log(result); // 15
```

---

## Break Statement

The `break` statement is crucial! Without it, execution continues to the next case (fall-through).

### With Break (Correct)
```javascript
let fruit = 'apple';

switch (fruit) {
  case 'apple':
    console.log('Red fruit');
    break;
  case 'banana':
    console.log('Yellow fruit');
    break;
  case 'grape':
    console.log('Purple fruit');
    break;
}

// Output: Red fruit
```

### Without Break (Fall-Through)
```javascript
let fruit = 'apple';

switch (fruit) {
  case 'apple':
    console.log('Red fruit');
    // No break!
  case 'banana':
    console.log('Yellow fruit');
  case 'grape':
    console.log('Purple fruit');
}

// Output:
// Red fruit
// Yellow fruit
// Purple fruit
```

### Intentional Fall-Through
Sometimes fall-through is useful:

```javascript
let day = 6;
let activity;

switch (day) {
  case 1:
  case 2:
  case 3:
  case 4:
  case 5:
    activity = 'Work';
    break;
  case 6:
  case 7:
    activity = 'Play';
    break;
  default:
    activity = 'Rest';
}

console.log(activity); // Play (Saturday)
```

---

## Default Case

The `default` case executes when no cases match.

```javascript
let color = 'purple';

switch (color) {
  case 'red':
    console.log('Stop');
    break;
  case 'yellow':
    console.log('Caution');
    break;
  case 'green':
    console.log('Go');
    break;
  default:
    console.log('Unknown color');
}

// Output: Unknown color
```

### Default Position
The default doesn't have to be last, but it's a good practice:

```javascript
// ✅ Good practice
switch (value) {
  case 1:
    // ...
    break;
  case 2:
    // ...
    break;
  default:
    // ...
}

// ⚠️ Works but confusing
switch (value) {
  default:
    // ...
    break;
  case 1:
    // ...
    break;
}
```

---

## Switch vs If...Else

### Switch
```javascript
let day = 3;
let result;

switch (day) {
  case 1:
    result = 'Monday';
    break;
  case 2:
    result = 'Tuesday';
    break;
  case 3:
    result = 'Wednesday';
    break;
}
```

### If...Else (Equivalent)
```javascript
let day = 3;
let result;

if (day === 1) {
  result = 'Monday';
} else if (day === 2) {
  result = 'Tuesday';
} else if (day === 3) {
  result = 'Wednesday';
}
```

### When to Use Each

**Use Switch when:**
- Comparing one value against many options
- Code is cleaner and more readable
- Performance matters (switch is faster)

**Use If...Else when:**
- Complex conditions (ranges, boolean logic)
- Different variables are involved
- Conditions are interdependent

```javascript
// Switch is better
switch (status) {
  case 'pending':
  case 'processing':
  case 'completed':
  case 'failed':
    // handle
}

// If...else is better
if (age >= 18 && hasLicense) {
  canDrive = true;
} else if (age >= 16 && hasPermit) {
  canDrive = false;
} else {
  canDrive = false;
}
```

---

## Advanced Patterns

### Switch with Objects
```javascript
const commands = {
  'start': () => console.log('Game started'),
  'pause': () => console.log('Game paused'),
  'resume': () => console.log('Game resumed'),
  'stop': () => console.log('Game stopped')
};

let command = 'start';

switch (command) {
  case 'start':
  case 'pause':
  case 'resume':
  case 'stop':
    commands[command]();
    break;
  default:
    console.log('Unknown command');
}
// Output: Game started
```

### Switch with Function Returns
```javascript
function getDiscount(customerType) {
  switch (customerType) {
    case 'vip':
      return 0.20; // 20% discount
    case 'regular':
      return 0.10; // 10% discount
    case 'new':
      return 0.05; // 5% discount
    default:
      return 0; // No discount
  }
}

console.log(getDiscount('vip')); // 0.20
```

---

## Exercises

### Exercise 1: Traffic Light
Create a switch statement for traffic light colors:
- Red: Stop
- Yellow: Caution
- Green: Go

**Solution:**
```javascript
function trafficLight(color) {
  switch (color) {
    case 'red':
      return 'Stop';
    case 'yellow':
      return 'Caution';
    case 'green':
      return 'Go';
    default:
      return 'Invalid color';
  }
}

console.log(trafficLight('yellow')); // Caution
```

### Exercise 2: Month Days
Create a switch for days in a month:

**Solution:**
```javascript
function daysInMonth(month) {
  switch (month) {
    case 'January':
    case 'March':
    case 'May':
    case 'July':
    case 'August':
    case 'October':
    case 'December':
      return 31;
    case 'April':
    case 'June':
    case 'September':
    case 'November':
      return 30;
    case 'February':
      return 28;
    default:
      return 'Invalid month';
  }
}

console.log(daysInMonth('February')); // 28
```

### Exercise 3: Size Converter
Convert sizes (S, M, L, XL) to numbers:

**Solution:**
```javascript
function sizeToNumber(size) {
  switch (size) {
    case 'S':
      return 1;
    case 'M':
      return 2;
    case 'L':
      return 3;
    case 'XL':
      return 4;
    default:
      return null;
  }
}

console.log(sizeToNumber('L')); // 3
```

---

## Next Steps

→ [Functions](../04-FUNCTIONS/01-function-basics.md)  
→ [Back to Control Flow](./README.md)
