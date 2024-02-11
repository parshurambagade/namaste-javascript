# JavaScript Functions Overview

Once during an interview for a reputed Indian startup, the Akshay faced questions about functions, first-class functions, function expressions, and function statements in JavaScript.

The interview included discussions on anonymous functions, first-class functions, and the difference between function statements and function expressions.

Let's break down the key concepts related to functions in JavaScript:

## Function Statement (Declaration)

Function statements create named functions and can be called before their declaration. Example:

        function functionName() {                 
            console.log("Function statement");             
        }             
        functionName(); // Function statement
        

## Function Expression

Function expressions create anonymous functions assigned to variables. They should be called after their declaration. Example:

        const funcExpression = function () {                 
            console.log("Function expression");             
        };             
        funcExpression(); // Function expression

## Anonymous Functions

Functions without names, commonly used as values. Be cautious when using them, as they lack their own identity. Example:

        const anonymousFunc = function () {                 
            console.log("Anonymous function");             
        };             
        anonymousFunc(); // Anonymous function

## Parameters and Arguments

Parameters are the function's local variables defined in the function declaration. Arguments are the values passed to a function when called.

        function sum(a, b) {                 
            return a + b;             
        }            
        console.log(sum(3, 5)); // 8

## First-Class Functions

JavaScript treats functions as first-class citizens, allowing them to be used as values, passed as arguments, and returned from other functions. Example:

        function greet() {                 
            return "Hello!";             
        }              
        function sayHello(func) {                 
            console.log(func());             
        }              
        sayHello(greet); // Hello!

Stay tuned for the next topic covering callbacks and higher-order functions, crucial for learning functional programming in JavaScript.

Remember, JavaScript functions are powerful and form the heart of the language!

Disclaimer: These notes are for learning purposes and may not cover all nuances. Explore further for a deeper understanding.
