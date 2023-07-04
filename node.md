**1. Is JavaScript single threaded or multi threaded?**
  - 💡 JavaScript is primarily single-threaded, executing one task at a time.
  - 💡 Asynchronous behavior is possible in JavaScript through concepts like callbacks, promises, and async/await.
  - 💡 The Event Loop manages the execution of asynchronous operations in an event-driven manner.
  - 💡 JavaScript can interact with multi-threaded environments like web browsers through Web APIs such as Web Workers.
  - 💡 Understanding JavaScript's single-threaded nature is essential for writing efficient and responsive code.
    
**2. Explain how nodejs handles async operations?**
    ![image](https://github.com/Malong11-007/JS-interview-questions/assets/40298510/2493a28c-0f6a-49ac-b1da-f484ead37352)
    ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/cf900d82-3e80-4610-8bd7-050ddb597ad2)


**3. What are generators?**

  - 💡 Generators are often misunderstood but can be incredibly useful in JavaScript.
  - 💡 The `function*` syntax denotes a generator function.
  - 💡 The `yield` keyword is used to return values sequentially from a generator.
  - 💡 The `next` function executes the code inside the generator and returns the yielded values.
  - 💡 Multiple generator instances can run concurrently.
  - 💡 Generators are useful for creating infinite loops and generating unique identifiers.
  - 💡 Generators can be used as iterators with the `next` function.
  - 💡 Values can be passed to `next` to affect the iteration.
  - 💡 The `return` function allows for premature exit from a generator.
  - 💡 The `throw` function can be used to throw errors within a generator.
  - 💡 Under the hood async/await uses generators.
  - Use cases: These are some of the main use cases for generators in JavaScript. Generators provide a powerful way to control the flow of execution and create iterable sequences of values or actions.
      1. Infinite Loops: Generators can be used to create infinite loops that don't freeze the program. Unlike regular loops, generators execute one step at a time, allowing you to generate values or perform actions repeatedly without blocking the program.
      2. Unique Identifiers: Generators are useful for generating unique IDs. By using a generator function, you can continuously yield new ID values without the need for manual tracking or potential clashes.
      3. Iterators: Generators can be used as iterators, which are objects or functions that provide a sequence of values. You can iterate over these values using the `next()` method to access each value and determine if the iteration is complete.
      4. Converting Arrays to Iterators: Generators simplify the process of converting arrays into iterators. By defining a generator function that yields each element of an array, you can easily iterate over the array's values one at a time.

**4. Promises vs Observables**

  - 💡 Observables are a core component of Angular and offer advantages over promises.
  - 💡 Observables deliver data over time, while promises deliver data only once.
  - 💡 Observables can be cancelled, while promises cannot.
  - 💡 Observables have a wide range of operators for data transformation, while promises lack additional methods.
  - 💡 Observables are lazy, meaning they are not executed unless subscribed to, while promises are always executed.
  - 💡 Errors in observables are handled within the subscribe method, while errors in promises are handled within the "then" method.
  - 💡 Observables can be used for more than just HTTP calls in Angular.
  - 💡 It is recommended to use observables instead of promises in Angular applications.
  ![image](https://github.com/Malong11-007/JS-interview-questions/assets/40298510/f75a4b60-8256-412b-983a-0d7b95d277d7)

**5. Promise.all vs Promise.allSettled vs Promise.race vs Promise.any**

  - 💡 **Promise.all** waits for all promises to settle and returns a single promise that resolves with an array of fulfillment values or rejects with the reason of the first rejected promise.
  - 💡 **Promise.allSettled** waits for all promises to settle and returns a single promise that always fulfills with an array of objects representing the outcome of each promise.
  - 💡 **Promise.race** returns a promise that resolves or rejects based on the first promise in the iterable that settles.
  - 💡 **Promise.any** returns a promise that resolves with the value of the first fulfilled promise or rejects with an AggregateError if all promises are rejected.
  ![image](https://github.com/Malong11-007/JS-interview-questions/assets/40298510/f98964d5-211f-4e88-8a49-15fccc7c6bb3)

**6. What are event emitters?**

  - 💡 Event emitters are mechanisms that facilitate communication between objects by emitting and handling events.
  - 💡 They are commonly used in event-driven programming and can be implemented using the observer pattern.
  - 💡 Event emitters decouple the emitter from specific listeners, allowing for modular and flexible system design.
  - 💡 They are used for handling user interactions, managing asynchronous operations, and enabling pub/sub messaging systems.
  - 💡 Example: Logger
    
**7. Bind vs Apply vs Call**
  - 💡 In JavaScript, bind, apply, and call are methods that allow you to control the execution context of a function and specify the value of this within the function
  - 💡 **bind**: Creates a new function with a specified this value, returning a bound function.
  - 💡 **apply**: Invokes a function with a specified this value and an array of arguments.
  - 💡 **call**: Invokes a function with a specified this value and individual arguments.
  ```
  PolyFill for bind.
  Function.prototype.myBind = function (obj, ...args) {
    let func = this;
    // Accepting arguments passed to newFunc
    return function (...newArgs) {
      func.apply(obj, [...args, ...newArgs]);
    };
  };
  ```
**8. What are symbols?**

  - 💡 JavaScript Symbols were added in ES6 and serve as a **unique** value for identifying object properties.
  - 💡 Symbols are a primitive datatype and cannot be constructed like objects.
  - 💡 Symbols can have descriptions but primarily serve debugging purposes.
  - 💡 Symbols can be used as keys for objects and have a guaranteed unique value.
  - 💡 Symbols are not included in the for...in loop and are not represented in JSON.stringify.
  ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/4e34a7ec-40c5-4838-ad1a-6ea2193a0107)
