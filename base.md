**1. Is JavaScript single threaded or multi threaded?**
  - 💡 JavaScript is primarily single-threaded, executing one task at a time.
  - 💡 Asynchronous behavior is possible in JavaScript through concepts like callbacks, promises, and async/await.
  - 💡 The Event Loop manages the execution of asynchronous operations in an event-driven manner.
  - 💡 JavaScript can interact with multi-threaded environments like web browsers through Web APIs such as Web Workers.
  - 💡 Understanding JavaScript's single-threaded nature is essential for writing efficient and responsive code.
    
**2. Explain how nodejs handles async operations?**
    ![image](https://github.com/Malong11-007/JS-interview-questions/assets/40298510/2493a28c-0f6a-49ac-b1da-f484ead37352)
    ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/cf900d82-3e80-4610-8bd7-050ddb597ad2)

**2.1. Event loop behaviour in ESM vs CJS**

  - 💡 In an ESM environment, such as Node.js with ESM support or modern browsers with native ESM support, the script is typically interpreted as an ECMAScript Module. In ESM, the script runs in a global async context, and the event loop operates differently compared to CJS.
  - 💡 In ESM, when you use Promise.resolve() or other microtasks, they are queued in the microtask queue. Microtasks have higher priority than regular tasks, and they are executed immediately after the current task is finished, before the event loop moves to the next phase. This means that microtasks are executed before the next event loop cycle starts. So, if you're running an ESM script and queue a microtask like Promise.resolve(), it will be executed right away because the event loop is still in the microtask phase. This behavior can lead to differences in execution order compared to CJS, where microtasks are not present.
  - 💡 It's important to consider the context and the specific environment in which the code is running to understand the nuances of event loop execution and the differences between ESM and CJS.
  
```javascript
console.log(typeof module) // if it return object then its CJS otherwise ESM.
process.nextTick(() => {
  console.log("nextTick");
});
setTimeout(() => {
  console.log("setTimeout");
}, 0);
Promise.resolve(true).then(() => {
  console.log("promise");
});
console.log("Last");

// Outputs CJS
    // Object
    // Last
    // nextTick
    // promise
    // setTimeout

// Output ESM
    // undefined
    // Last
    // promise
    // nextTick
    // setTimeout

```


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
  ```JS
  // PolyFill for bind.
  Function.prototype.myBind = function (obj, ...args) {
    let func = this;
    // Accepting arguments passed to newFunc
    return function (...newArgs) {
      func.apply(obj, [...args, ...newArgs]);
    };
  };

  // Usage
  let melissa = {
    name: "Malissa",
  };
  
  let patrick = {
    name: "patrick",
  };
  
  function printName(...args) {
    console.log(this.name, ...args);
  }
  
  // Apply => accepts arg as arr
  printName.apply(melissa, [1, 2, 4]);
  
  // Call => Comma-separated args
  printName.call(melissa, 1, 2, 3);
  
  // Bind
  const printNamePatrick = printName.bind(patrick, 1, 2, 3);
  printNamePatrick();

  ```
**8. What are symbols?**

  - 💡 JavaScript Symbols were added in ES6 and serve as a **unique** value for identifying object properties.
  - 💡 Symbols are a primitive datatype and cannot be constructed like objects.
  - 💡 Symbols can have descriptions but primarily serve debugging purposes.
  - 💡 Symbols can be used as keys for objects and have a guaranteed unique value.
  - 💡 Symbols are not included in the for...in loop and are not represented in JSON.stringify.
  - 💡 The Symbol.iterator property is used to check if an object has an iterator.
  ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/4e34a7ec-40c5-4838-ad1a-6ea2193a0107)

**9. Enumberable vs Iterable**
  
  - 💡 Iterable: An iterable is an object that can be iterated over using a loop. It has a built-in method called Symbol.iterator that returns an iterator object. Examples of built-in iterables in JavaScript include arrays, strings, maps, sets, and generators.
  - 💡 Enumerable: Enumerable properties in JavaScript are the properties of an object that can be iterated over using the for...in loop construct. By default, properties added to an object using dot notation or square bracket notation are enumerable. You can control the enumerability of properties using methods like Object.defineProperty() or the enumerable property descriptor.
  - 💡 So, in simpler terms, an iterable is an object that you can loop over, like an array or a string. Enumerable properties are the properties of an object that you can iterate over using a for...in loop.
  - 💡 Only in JS, Iterable -> values, enumerable -> properties / keys
  - 💡 Tip to remember
      - for..in..keys === foreign keys === use for...in for keys;
      - for...of for values.
      - **in** gives you index.
   
**10. Seal vs Freeze vs preventExtensions**

  - 💡 Calling seal, freeze, or prevent extensions prevents the addition of new properties to an object.
  - 💡 Seal and prevent extensions allow changing the value of existing properties, but freeze does not.
  - 💡 Seal and freeze prevent deleting properties, but prevent extensions allows it.
  - 💡 Property descriptors cannot be changed using seal or freeze, but it's possible with prevent extensions.
  - 💡 Reassigning the prototype of an object is not allowed after calling any of the three methods seal, freeze, or prevent extensions.
  ![Screenshot from 2023-07-05 13-20-06](https://github.com/Malong11-007/javascript-iq/assets/40298510/1400e21a-f3a4-4243-862a-d10fe31b5da2)

**11. What Object.create does?**
  
  - 🔄 Object.create is used to create a new object and set its prototype.
  - 🔑 Objects created with Object.create inherit properties from their prototypes.
  - 📝 Property descriptors can be used to define properties for the created objects.
  ![Screenshot from 2023-07-05 13-46-35](https://github.com/Malong11-007/javascript-iq/assets/40298510/7c7c460d-effb-4c52-a1dd-890f76ab9e46)

**12. Object.assign vs Object.defineProperties**
  - 💡 Object.assign is used to copy the values of properties from source objects to a target object.
  - 💡 Object.defineProperties is used to define or modify multiple properties on an object with explicit property descriptors.

**13. What is strong referencing and reachability?**
  
  - 💡 Strong references and reachability are concepts related to memory management in programming languages. They determine whether an object or value is still accessible and eligible for garbage collection.
  - 💡 In JavaScript, when an object is assigned to a variable or added to a data structure like an array or a map, a strong reference is created. A strong reference means that the object is strongly reachable, and as long as there is at least one strong reference to the object, it will remain in memory and won't be garbage collected.
```javascript
// Credit: https://gist.github.com/prof3ssorSt3v3/602b498ad96d14cad9e9495359019c30
const log = console.log;

// Strong Ref and Reachability - the default state
let person = { id: 123, name: 'Shaggy' };
let list = [person];
person = null; // destroys one reference

// person and list[0] were referring to the same object initially
// After setting person to null, only the reference in list remains
// The object { id: 123, name: 'Shaggy' } is still reachable through list[0]
```

**14. WeakMap / WeakSet**
  - 💡 A `WeakSet` is a built-in JavaScript data structure that allows storing a collection of weak references to objects.
  - 💡 The objects stored in a `WeakSet` must be objects, and they are held as weak references, which means they don't prevent the object from being garbage collected.
  - 💡 Here's an example of using a `WeakSet`:
```javascript
let kids = new WeakSet();
let son = { name: 'Alex' };
let daughter = { name: 'Bree' };

kids.add(son);
kids.add(daughter);

// Check if the WeakSet contains certain objects
log('has son', kids.has(son));           // true
log('has daughter', kids.has(daughter)); // true

son = null;

// After setting `son` to `null`, the object is no longer strongly reachable
// The weak reference in the `kids` WeakSet won't prevent garbage collection

log('has son', kids.has(son));           // false
log('has daughter', kids.has(daughter)); // true
```
  - 💡 A `WeakMap` is a built-in JavaScript data structure that allows storing a collection of key-value pairs, where the keys must be objects.
  - 💡 The objects stored as keys in a `WeakMap` are held as weak references.
  - 💡 Here's an example of using a `WeakMap`:
```javascript
let theGang = new WeakMap();
let fred = { id: 123, gender: 'male' };
let daphne = { id: 456, gender: 'female' };
let velma = { id: 789, gender: 'female' };

theGang.set(fred, 'blue');
```
**15. null vs Undefined**

  - 💡 Null in JavaScript means an empty value and is also a primitive type in JavaScript. The variable which has been assigned as null contains no value.
  - 💡 Undefined, on the other hand, means the variable has been declared, but its value has not been assigned.

**16. What is Hoisting?**
  - 💡 Hoisting is assigning the memory to variables and functions even before initialising them.
  - 💡 Also explain it as, Hoisting is a JavaScript mechanism where variables and function declarations are moved to the top of their scope before code execution.
  - 💡 `const` and `let` have the memory and placeholder Undefined. which means they are also hoisted. But if you try to access them before initialization it will throw regerence error.
      - `Uncaught ReferenceError: Cannot access ‘__variable__’ before initialization`
  - 💡 The `Temporal Dead Zone` (TDZ) is a behavior in JavaScript that occurs with variables declared using let and const. It is the period between the start of a block scope and the actual declaration of a variable within that scope.
```javascript
  // Var
  console.log(x); // Output: undefined
  var x = 10;
  console.log(x); // Output: 10
  
  // function
  foo(); // Output: "Hello, World!"
  function foo() {
    console.log("Hello, World!");
  }
  
  // function expression
  foo(); // Output: TypeError: foo is not a function
  var foo = function () {
    console.log("Hello, World!");
  };
  // let / const
  console.log(x); // Output: ReferenceError: x is not defined
  let x = 10;
```
**16. What is prototype?**

  - 💡 Prototypes are the mechanism by which JavaScript objects inherit features from one another
  - 💡 It allows sharing properties and methods among multiple instances.
  - 💡 The prototype object is shared among instances created with the same constructor function.
  - 💡 Properties and methods defined on the prototype are accessible to instances.
  - 💡 Modifying the prototype affects all instances and future instances.
  - 💡 Prototypal inheritance allows objects to inherit from their prototype chain.
  ![Screenshot from 2023-07-05 17-37-11](https://github.com/Malong11-007/javascript-iq/assets/40298510/225151b7-b5b1-4445-bfda-96900ac76a27)

**17. Arrow function vs Normal function**

  - 💡 Arrow Functions:
    - Have a concise syntax using the arrow (=>) operator.
    - Inherit the "this" value from the surrounding scope.
    - Do not have their own "this" context.
    - Do not have the "arguments" object (the "arguments" keyword refers to the arguments of the surrounding scope).
    - Cannot be used as constructors with the "new" keyword.
  - 💡 Normal Functions:
    - Use the "function" keyword for declaration.
    - Have their own "this" context, which can be influenced by how they are invoked.
    - Have their own "arguments" object that contains all passed arguments, even those not defined in the parameter list.
    - Can be used as constructors with the "new" keyword to create new instances of objects.
   
**18. Explain closures**
  - 💡 A closure is an inner function that remembers and has access to variables in the local scope in which it was created even after the outer function has finished executing
  - 💡 Use cases: Callback functions, Data privacy, React hook utilize closures, Caching / Memoization, Curring / partial application.

**19. What is Currying?**
  - 💡 Currying in JavaScript transforms a function with multiple arguments into a nested series of functions, each taking a single argument. Currying helps you avoid passing the same variable multiple times, and it helps you create a higher order function
  - 💡 JavaScript provides native support for currying through closures and function binding.
  - 💡 Currying and function composition are both techniques used in functional programming, but they serve different purposes.
    - Currying transforms a function with multiple arguments into a sequence of functions, each taking only one argument. It helps create reusable function transformations.
    - On the other hand, function composition is a way of combining multiple functions into a single function, where the output of one function becomes the input of the next function.
```javascript
function curry(fn) {
    return function curried(...args) {
        console.log(fn.length, args.length);
        if (fn.length !== args.length && args.length < fn.length) {
            return curried.bind(null, ...args);
        } 
        return fn(...args);
    }
}

function add(a, b, c) {
    return a + b + c;
}

const curriedAdd = curry(add);
console.log(curriedAdd(1)(3)(5));
console.log(curriedAdd(1)(3, 5));
  
```
  
**20. Programming Paradigms**

  - 💡 Imperative Programming: Programs are written as a series of instructions that explicitly state how to perform computations.
    - Focuses on changing program state through statements and control flow.
    - Uses mutable variables to store and modify data.
    - Relies on loops and conditional statements for control flow.
    - Example: C++, Java
  
  - 💡 Declarative Programming: Programs focus on describing what should be computed rather than how.
    - Expresses relationships and dependencies using declarations and expressions.
    - Does not emphasize explicit control flow.
    - Types of declarative paradigms include:
      - Functional Programming (FP): Programs are composed of pure functions. Function are first-class citizens. Avoid side effects, such as modifying external state or relying on global variables.
        - Example: Haskell, Lisp, Clojure
      - Logic Programming: Programs use rules and facts to express relationships.
        - Example: SQL, Prolog, Datalog
          
    ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/a5c3f4e1-1cbe-403c-b201-00d091862c4b)

**21. SSR vs SSG vs ISR vs CSR**

  - 💡 Static Site Generation (SSG) Pages are pre-rendered and served as static HTML. The content is the same for every request.
  - Server-side generation (SSG) combines server-side rendering with storing the generated HTML file on a CDN for faster response times and reduced server load.
  - 💡 Client-Side Rendering (CSR) Data is loaded and rendered on the client side using React code. The initial render may not include dynamic data, which is loaded later.
  - 💡 Server-Side Rendering (SSR) Data is loaded on the server and passed as props to the component. The server renders the complete HTML, but there may be additional API requests for each page request.
  - 💡 Incremental Static Regeneration (ISR) Similar to SSR, but with caching. The server renders the HTML and caches it for a specific duration. Within that duration, subsequent requests return the cached HTML without making API requests.
  ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/1c36688b-ff05-4dc1-938f-902db5c929d5)

**22. Javascript module system - commonjs vs esm**

  - 💡 CommonJS (CJS):
    - Originally designed for server-side JavaScript environments.
    - Synchronous module system where dependencies are loaded using the `require` function.
    - Commonly used in older Node.js versions and server-side JavaScript frameworks.
    - Not natively supported in web browsers without bundlers or module loaders.
      ```js
      // greet.js
      const greet = (name) => {
      console.log(`Hello, ${name}!`);
      };
      module.exports = greet;
      ------------------------------------------
  
      // index.js
      const greet = require('./greet');
      greet('John'); // Output: Hello, John!
      ```
  
  - 💡 ECMAScript Modules (ESM):
    - JavaScript's official module system introduced with ECMAScript 6 (ES6).
    - Asynchronous module system where dependencies are handled with `import` and `export` statements.
    - Commonly used in modern JavaScript environments, bundlers (like Webpack), module loaders (like SystemJS), and browsers that support ESM.
    - Preferred choice for web-based projects and newer Node.js versions.
      ```js
      // greet.js
      const greet = (name) => {
      console.log(`Hello, ${name}!`);
      };
      export default greet;
      ------------------------------------------
      // index.js
      import greet from './greet.js';
      greet('John'); // Output: Hello, John!
      ```
  
**23. Modern JS development **

  - 💡 JavaScript changes rapidly with new features and syntax, making it challenging to keep up with browser implementations.
  - 💡 Different JavaScript engines (e.g., V8, SpiderMonkey, JavascriptCore - bun.js) may not fully support the ECMAScript standard, causing compatibility issues across browsers.
  - 💡 Polyfills and feature detection help address compatibility issues by providing missing features or alternative code implementations.
  - 💡 Transpiling code to a specific JavaScript version, such as ECMAScript 2015, ensures compatibility across targeted browsers.
  - 💡 Babel is a popular JavaScript compiler that handles transpilation and polyfilling.
  - 💡 Webpack bundles JavaScript code into a single file, simplifying its integration into HTML.
  - 💡 SWC (Speedy Web Compiler) is a faster alternative to Babel, written in Rust, that can perform code compilation and bundling.
  - 💡 https://www.youtube.com/watch?v=QliwSwWHJoQ
  ![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/89876c99-fb1e-4c98-8904-c6671dd3f2f4)

