
Async/Await Notes
=================

1\. Introduction to Async/Await
-------------------------------

Async/Await is a feature introduced in JavaScript to handle asynchronous operations more effectively and with cleaner syntax compared to using promises and callbacks.

*   **Async Function:** A function that returns a promise and allows the use of the await keyword.
*   **Await Keyword:** Used inside an async function to pause the execution until a promise is resolved, allowing for sequential and cleaner code.

2\. Behind the Scenes of Async/Await
------------------------------------

Async/Await works by suspending the execution of an async function until promises are resolved. Behind the scenes, JavaScript manages the execution flow, allowing developers to focus on writing code without worrying about callback hell.

Example:
```javascript 
    async function fetchData() {
      const response = await fetch('https://api.example.com/data');
      const data = await response.json();
      console.log(data);
    }
```
3\. Handling Errors with Async/Await
------------------------------------

Error handling in Async/Await can be done using try-catch blocks, providing a cleaner and more readable way to handle errors compared to using .catch() with promises.

Example:
```javascript
    async function fetchData() {
      try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
```
4\. Best Practices and Comparison
---------------------------------

Async/Await is considered a syntactic sugar over promises, providing cleaner and more readable code. It is recommended to use Async/Await for handling asynchronous operations whenever possible.

Example:
```javascript
    async function fetchData() {
      try {
        const response = await fetch('https://api.example.com/data');
        const data = await response.json();
        console.log(data);
      } catch (error) {
        console.error('Error fetching data:', error);
      }
    }
```
Using Async/Await:

    fetchData();

Using Promises:

    fetchData()
      .then(data => console.log(data))
      .catch(error => console.error('Error fetching data:', error));

## Complex examples

#### Example 1: Both Awaits Resolving in 10 Seconds
 ```javascript   
    async function complexExample1() {
      try {
        console.log('Start');
        await new Promise(resolve => setTimeout(resolve, 10000)); // Wait for 10 seconds
        console.log('After 10 seconds');
        await new Promise(resolve => setTimeout(resolve, 10000)); // Wait for another 10 seconds
        console.log('After another 10 seconds');
      } catch (error) {
        console.error('Error:', error);
      }
    }
    complexExample1();
  ```      


**Explanation:**

*   The function starts execution and logs 'Start'.
*   The first await pauses execution for 10 seconds.
*   After 10 seconds, 'After 10 seconds' is logged.
*   The second await then pauses execution for another 10 seconds.
*   After the second 10 seconds, 'After another 10 seconds' is logged.

#### Example 2: Concurrent Resolution of Promises (10 seconds)
 ```javascript   
    async function complexExample2() {
      const p1 = new Promise(resolve => setTimeout(resolve, 10000));
      const p2 = new Promise(resolve => setTimeout(resolve, 10000));
      try {
        console.log('Start');
        const val1 = await p1// Wait for 10 seconds
        console.log('After 10 seconds');
        const val2 = await p2 // Will not wait for another 10 seconds
        console.log('Instantly after the first promise is resolved');
      } catch (error) {
        console.error('Error:', error);
      }
    }
    complexExample2();
```
**Explanation:**

*   Both promises \`p1\` and \`p2\` are created simultaneously, each with a timeout of 10 seconds.
*   The function starts execution and logs 'Start'.
*   The first \`await p1\` pauses execution for 10 seconds.
*   The second \`await p2\` will not pause execution for another 10 seconds as it is already been resolved.
*   After the first promise is resolved, both \`await\` expressions complete concurrently, resulting in both console log statements ('After 10 seconds' and 'Instantly after the first promise is resolved') being printed almost simultaneously.
        
#### Example 3: First Await Resolving in 10 Seconds, Second Await Resolving in 20 Seconds
```javascript 
    async function complexExample1() {
      try {
        console.log('Start');
        await new Promise(resolve => setTimeout(resolve, 10000)); // Wait for 10 seconds
        console.log('After 10 seconds');
        await new Promise(resolve => setTimeout(resolve, 20000)); // Wait for another 20 seconds
        console.log('After another 20 seconds');
      } catch (error) {
        console.error('Error:', error);
      }
    }
    complexExample1();
```
**Explanation:**

*   The function starts execution and logs 'Start'.
*   The first await pauses execution for 10 seconds.
*   After 10 seconds, 'After 10 seconds' is logged.
*   The second await then pauses execution for another 20 seconds.
*   After the second 20 seconds, 'After another 20 seconds' is logged.

        
#### Example 4: Concurrent Resolution of Promises (10 seconds and 20 seconds)
```javascript 
    async function complexExample2() {
      const p1 = new Promise(resolve => setTimeout(resolve, 10000));
      const p2 = new Promise(resolve => setTimeout(resolve, 20000));
      try {
        console.log('Start');
        const val1 = await p1// Wait for 10 seconds
        console.log('After 10 seconds');
        const val2 = await p2 // Wait for next 10 seconds
        console.log('After next 10 seconds');
      } catch (error) {
        console.error('Error:', error);
      }
    }
    complexExample2();
```
**Explanation:**

*   Both promises \`p1\` and \`p2\` are created simultaneously, but \`p2\` has a longer timeout of 20 seconds.
*   The function starts execution and logs 'Start'.
*   The first \`await p1\` pauses execution for 10 seconds (already 10 seconds are passed, remaining next 10 seconds).
*   The second \`await p2\` then pauses execution for another 10 seconds.
*   After the second 10 seconds, 'After next 10 seconds' is logged.

    
#### Example 5: First Await Resolving in 20 Seconds, Second Await Resolving in 10 Seconds
```javascript 
    async function complexExample1() {
      try {
        console.log('Start');
        await new Promise(resolve => setTimeout(resolve, 20000)); // Wait for 20 seconds
        console.log('After 20 seconds');
        await new Promise(resolve => setTimeout(resolve, 10000)); // Wait for another 10 seconds
        console.log('After another 10 seconds');
      } catch (error) {
        console.error('Error:', error);
      }
    }
    complexExample1();
```
**Explanation:**

*   The function starts execution and logs 'Start'.
*   The first await pauses execution for 20 seconds.
*   After 20 seconds, 'After 20 seconds' is logged.
*   The second await then pauses execution for another 10 seconds.
*   After the second 10 seconds, 'After another 10 seconds' is logged.

        

#### Example 6: First Promise Resolving in 20 Seconds, Second Promise Resolving in 10 Seconds
```javascript 
    async function complexExample2() {
      const p1 = new Promise(resolve => setTimeout(resolve, 20000));
      const p2 = new Promise(resolve => setTimeout(resolve, 10000));
      try {
        console.log('Start');
        const val1 = await p1; // Wait for 20 seconds
        console.log('After 20 seconds');
        const val2 = await p2; // Will not wait for another 10 seconds
        console.log('Resolved before p1');
      } catch (error) {
        console.error('Error:', error);
      }
    }
    complexExample2();
```
**Explanation:**

*   Both promises \`p1\` and \`p2\` are created simultaneously, with \`p1\` resolving in 20 seconds and \`p2\` resolving in 10 seconds.
*   The function starts execution and logs 'Start'.
*   The first \`await p1\` pauses execution for 20 seconds.
*   The second \`await p2\` will not pause execution for another 10 seconds.
*   After the first promise is resolved, 'Resolved before p1' is logged instantly.

    
    

