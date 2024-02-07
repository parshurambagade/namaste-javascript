# Lecture 3: JavaScript Magic - Hoisting and Call Stack

## Introduction:
- In this lecture, we'll explore some fascinating aspects of JavaScript: Hoisting and Call Stack.

## Concept 1: Hoisting
- **Magic in JavaScript**: JavaScript allows accessing variables and functions even before they are initialized.
- Example Program:
  ```javascript
  var x = 7;
  function getName() {
    console.log("Namaste JavaScript");
  }
  getName();
  console.log(x);
  ```
- **Expected Output**: "Namaste JavaScript" followed by **'7'** for **'x'**.
- **Magic**: Move function invocation and console log of **'x'** to the top of the program.
  ```javascript
  getName();
  console.log(x);
  var x = 7;
  function getName() {
    console.log("Namaste JavaScript");
  }
  ```
  - **Question**: What do you expect now?
  - **Result**: Despite accessing **'getName'** and **'x'** before declaration, JavaScript doesn't throw an error.

## Understanding Hoisting:
- **Explanation**:
  - JavaScript allocates memory for variables and functions before executing the code.
  - Variables are assigned **'undefined'** initially.
  - Functions are stored as they are.
- **Demo**: Using browser debugger to inspect memory allocation before code execution.

## Difference Between undefined and not defined:
- **Scenario**: Remove the line where x is initialized.
  ```javascript
  getName();
  console.log(x);

  function getName() {
    console.log("Namaste JavaScript");
  }
  ```
- **Result**: JavaScript throws a **'ReferenceError'** for **'x'**.
- **Explanation**: **'not defined'** means the variable doesn't exist, while **'undefined'** means it exists but has no value.

## Arrow Functions and Hoisting:
- **Scenario**: Change **'getName'** to an arrow function.
  ```javascript
  console.log(getName);
  console.log(x);
  var x = 7;
  const getName = () => {
    console.log("Namaste JavaScript");
  }
  ```
- **Result**: JavaScript throws a **'TypeError'** saying **'getName'** is not a function.
- **Explanation**: Arrow functions behave like variables, not functions, during hosting.
## Additional Ways to Declare Functions:
- **Scenario**: Declare **'getName'** using different syntaxes.
  ```javascript
  console.log(getName);
  console.log(x);
  var x = 7;
  var getName = function () {
    console.log("Namaste JavaScript");
  }
  ```
- **Result**: Similar to arrow functions, these declarations result in **'undefined'** during hosting.
## Conclusion:
- Hoisting in JavaScript allows accessing variables and functions before their declaration.
- Understanding hoisting is crucial for explaining JavaScript behavior during interviews.
## Concept 2: Call Stack
- **Recap**: Execution context is created during JavaScript execution.
- **Demo**: Using browser debugger to inspect call stack during function execution.
## Understanding Call Stack:
- **Explanation**:
  - Each function call creates a new execution context, added to the call stack.
  - After execution, the context is removed from the stack.
## Conclusion:
- Call stack manages the order of execution of execution contexts.
- Understanding call stack helps in visualizing JavaScript program execution.
