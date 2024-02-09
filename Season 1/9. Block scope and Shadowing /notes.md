

Introduction to Blocks in JavaScript
------------------------------------

**Definition of Block:**  
A block is defined by curly braces and can group multiple JavaScript statements into a single unit.

**Usage of Blocks:**  
Blocks are used to combine multiple JavaScript statements into one group. This allows us to use multiple statements where JavaScript expects only one statement.

    // Example:
    if (condition) {
        statement1;
        statement2;
        // Multiple statements grouped together in a block.
    }
        

Block Scope in JavaScript
-------------------------

**Block Scope:**  
Block scope refers to the variables and functions that are accessible within a block.

    // Example:
    {
        // Variables declared with let and const are block-scoped.
        let a = 10;
        const b = 20;
    
        // Block scope example
        // The variables a and b are accessible only within this block.
        console.log(a); // Output: 10
        console.log(b); // Output: 20
    }
        

**Accessing Variables Outside the Block:**  
Variables declared with let and const are not accessible outside the block.

    // Attempting to access a and b outside the block results in an error.
    console.log(a); // Error: a is not defined
    console.log(b); // Error: b is not defined
        

Shadowing in JavaScript
-----------------------

**Shadowing:**  
Shadowing occurs when a variable declared within a block has the same name as a variable in the outer scope.

    // Example:
    let c = 30;
    
    {
        // Variable c inside the block shadows the outer variable c.
        let c = 40;
        console.log(c); // Output: 40
    }
    
    console.log(c); // Output: 30
        

**Illegal Shadowing:**  
Attempting to shadow a variable declared with var using let or const results in an error.

    // Example:
    {
        var d = 50;
        let d = 60; // Error: Identifier 'd' has already been declared
    }
        

Lexical Scope
-------------

**Lexical Scope:**  
Blocks follow lexical scope, meaning inner blocks have access to variables declared in outer blocks.

    // Example:
    {
        let e = 70;
        {
            // Inner block can access variable declared in outer block.
            console.log(e); // Output: 70
        }
    }