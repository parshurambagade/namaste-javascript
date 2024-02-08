# Function Invocation and Variable Environment

## Introduction:
- This video delves into function invocation and variable environment in JavaScript.

## Function Definition:
- Define function `a` with variable `x` set to 10.
- Log the value of `x` inside function `a`.
- Introduce another function `b` with the same variable name `x`, setting it to 100 and logging its value.

```JavaScript 
var x = 1;
a();
b();

function a() {
var x = 10;
console.log(x);
}

function b() {
var x = 100;
console.log(x);
}
```
## Demonstration:
- Functions `a` and `b` are defined.
- The same variable `x` is initialized in the global space with a value of 1.
- Functions `a` and `b` are invoked, showcasing JavaScript behavior with variables of the same name.
- Output is logged for variable `x` after invoking both functions.

![function invocation](./function%20invocation.png)

## Behind the Scenes:
- JavaScript creates a global execution context upon running the program.
- Memory allocation for variables `x`, functions `a`, and `b`.
- Understanding of the call stack, with the global execution context pushed onto it.
- Execution of code line by line, with variable assignments and function invocations.
- Creation of local execution contexts for functions `a` and `b`, with their own memory space.
- Execution of code within these local contexts, updating the value of `x` as needed.
- Removal of execution contexts from the call stack upon completion of execution.
- Visualization of JavaScript's handling of variable environments and function invocations.
