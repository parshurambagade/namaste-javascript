# Understanding Lexical Environment and Scope in JavaScript

## Introduction:
- Lexical environment and scope are fundamental concepts in JavaScript.
- Understanding these concepts is crucial for comprehending scope chains and closures.

## Lexical Environment:
- Lexical environment is the local memory along with the lexical environment of its parent.
- It consists of local memory and a reference to the lexical environment of the parent function.
- Lexical environment is created whenever an execution context is created.

## Scope:
- Scope determines where a variable or function can be accessed in code.
- There are two aspects of scope: 
  1. Scope of a variable/function
  2. Whether a variable/function is inside the scope of a function

## Scope Chain:
- The scope chain is the chain of lexical environments.
- When JavaScript engine doesn't find a variable/function in the local environment, it moves up the scope chain.
- It continues searching through the parent lexical environments until the variable/function is found or the scope chain is exhausted.

## Example:
```javascript 
function outerFunction() {
  let outerVar = 'Main bahar hoon';

  function innerFunction() {
    let innerVar = 'Main andar hoon';
    console.log(innerVar); // Accessible
    console.log(outerVar); // Accessible
  }

  innerFunction();

  console.log(innerVar); // Error: innerVar is not defined
}

outerFunction();

console.log(outerVar); // Error: outerVar is not defined

```
- Program contains a function `outerFunction` which includes another function `innerFunction`.
- `outerFunction` declares a variable `outerVar`.
- `innerFunction` declares a variable `innerVar`.
- When `innerFunction` tries to access `outerVar`, JavaScript engine checks its local memory first.
- If `outerVar` is not found locally, the engine moves up the scope chain to `outerFunction` where `outerVar` is declared, and access is successful.
-  However, accessing `innerVar` from outside `innerFunction` results in an error as `innerVar` is scoped only within `innerFunction`.
- Variables declared inside `outerFunction` are not accessible outside its lexical environment.
- If not found, it continues up the chain until the global scope is reached.

## Visual Representation:
![Scope chain in js](./lexical%20environment.png)
- The call stack includes global execution context and nested function execution contexts.
- Each execution context has its own local memory and code.
- Lexical environment is established for each execution context, including a reference to its parent's lexical environment.

## Conclusion:
- Lexical environment and scope form the backbone of JavaScript's variable and function access.
- Understanding lexical environment and scope chain is crucial for effective JavaScript programming.
- Visualizing the scope chain aids in understanding how JavaScript resolves variable/function access.
- Mastery of these concepts enhances code clarity and proficiency in JavaScript development.
