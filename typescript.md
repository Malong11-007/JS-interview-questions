**1. What is Typescript?**

  - 🏷️ TypeScript is a superset of JavaScript developed by Microsoft.
  - 🏷️ It introduces static typing for catching errors at compile-time.
  - 🏷️ TypeScript enhances code maintainability with features like enums, interfaces, types etc.
  - 🏷️ It provides a better development experience with powerful tools and IDE support.
  - 🏷️ It allows for gradual adoption and seamless integration with existing JavaScript codebases.
  - 🏷️ The TypeScript compiler is responsible for converting TypeScript code (.ts or .tsx files) into JavaScript code (.js files) that can be executed by a JavaScript runtime environment.
  - 🏷️ The TypeScript compiler provides various options and configurations that can be specified through command-line arguments or by using a tsconfig.json file. These options allow you to customize the compilation process, enable strict type checking, target specific JavaScript versions, and more.

**2. What are access modifiers?**
  - 🏷️ Access modifiers in TypeScript allow you to control the visibility and accessibility of class members, enforcing encapsulation and providing more robust and maintainable code.
  - 🏷️ Following are the types:
    - **Public** (default): Public members are accessible from anywhere, both within the class and from external code. This is the default access modifier if none is explicitly specified.
    - **Private**: Private members are only accessible within the class in which they are defined. They cannot be accessed or modified from outside the class.
    - **Protected**: Protected members are accessible within the class that defines them and in derived classes (subclasses). They are not accessible from external code.

**3. Type vs interface**

  - 🏷️ Both interfaces and type aliases can create basic shapes and include functions.
  - 🏷️ Interfaces and type aliases can describe function signatures.
  - 🏷️ Type aliases can alias one type to another, providing additional semantic information.
  - 🏷️ Type aliases can be used to create tuples, unions, and intersections.
  - 🏷️ Interfaces can extend other interfaces, while type aliases cannot extend union types.
  - 🏷️ Interfaces allow for the merging of multiple interface declarations.
  - 🏷️ Choosing between interfaces and type aliases depends on personal conventions and requirements.
  - 🏷️ When the compiler encounters multiple interface declarations with the same name, it merges them into a single interface definition that includes all the properties and methods from each declaration. Interface reopening is particularly useful when working with external libraries or modules. It allows you to extend or augment the types provided by those libraries without modifying their original definitions. 

**4. What are generics?**

  - Generics are a programming feature that enables the creation of reusable code for working with different types, enhancing flexibility and code efficiency. They promote type-safe and flexible coding by allowing algorithms and data structures to be written once and used with multiple types.
    ```ts
    // Generics - Keyof Usage
    const pluck = <ItemType, keyType extends keyof ItemType>(
      items: ItemType[],
      key: keyType
    ): ItemType[keyType][] => {
      return items.map((item) => item[key]);
    };
    
    const cars = [
      { name: "Car 1", hp: 200 },
      { name: "Car 2", hp: 250 },
      { name: "Car 3", hp: 180 },
    ];
    
    pluck(cars, "name"); 
    // ^?
    ```
**5. Opaque vs Strutural Typing**
  
  - 🏷️ TypeScript lacks support for opaque types due to its focus on developer convenience over strict type safety.
  - 🏷️ Opaque types are offered by a nominal type system, which TypeScript does not fully adhere to.
  - 🏷️ TypeScript treats types with the same structure as the same type, regardless of their names.
  - 🏷️ Simulating opaque types in TypeScript involves adding distinct properties to differentiate between similar types.
  - 🏷️ By making types distinct, errors can be caught at compile time instead of in production.
  - 🏷️ Utility functions can be created to convert primitive numbers into well-defined types using type assertions.
  - 🏷️ The use of simulated opaque types improves type safety and prevents invalid variable assignments.
  - 🏷️ Simulated opaque types remain compatible with the primitive types they are derived from.
  - 🏷️ Arithmetic operations can still be performed on simulated opaque types.
  - 🏷️ Simulating opaque types in TypeScript involves using type intersections and controlled type assertions.
  - 🏷️ Example: https://github.com/basarat/demo-typescript-opaque-types

**6. Unknown vs any vs never**
  
  - 📌 **Any** (I don't care) type disables type checking and should be used sparingly, mostly when porting JavaScript code to TypeScript.
  - 📌 **Unknown** (I don't know yet) type provides type checking for all possible values, allowing narrowing down to specific types through conditional checks.
  - 📌 "Never" type represents an empty set and is often encountered in complex type building or exhaustive switch statements.
  - https://ivov.dev/notes/typescript-and-set-theory

**7. Declaration files (*.d.ts) / module vs namespace**

  - 📝 Declaration files (`.d.ts`) in TypeScript provide type information for JavaScript libraries or code without native TypeScript support. They enable TypeScript to understand and provide type checking, autocompletion, and type inference for external JavaScript code. 
  - 📝 Declaration files are typically created by library authors or the TypeScript community.
  - 📝 If you're already using TypeScript for your modules, you may not need to create separate declaration files for your own code. TypeScript can infer types from TypeScript source files (.ts) automatically.
  - 📝 Declaration files are primarily used when working with external JavaScript libraries or sharing TypeScript types/interfaces.
  - 📝 Namespaces are used to group related entities under a common namespace, preventing naming collisions. They are defined with the `namespace` keyword.
  - 📝 Modules provide a more modern and recommended approach for organizing and sharing code. They use the `module` or `namespace` keywords (deprecated) and follow a file-based structure.
  - 📝 Declaration files can be referenced using the Triple-Slash Directive syntax (`/// <reference path="path/to/declaration.d.ts" />`) in older projects. In modern projects, module imports (`import`) are preferred.
  - 📝 Declaration files allow you to define types, interfaces, classes, enums, and functions that are accessible globally or within specific modules.
  - 📝 When using `declare module`, the types and functions defined within the module become part of the global namespace and can be used without an import statement.
  - 📝 When using a declaration file written as a module declaration (`declare module "module-name" { ... }`), you can import types and functions using ES module syntax (`import { ... } from "module-name"`).
  Here's a code snippet to illustrate the usage:
    ```typescript
    // Declaration file (`myTypes.d.ts`):
    declare module "myTypes" {
      interface Person {
        name: string;
        age: number;
      }
    
      function greet(person: Person): void;
    }
    ```
    
    
    ```typescript
    // Using the declaration file:
    import { Person, greet } from "myTypes";
    
    const person: Person = {
      name: "John",
      age: 30,
    };
    
    greet(person);
    ```

**8. Static vs Dyanamic Typed language**
    
  - 📝 Static languages have fixed typing and do not allow changing the type of a variable.
  - 📝 Dynamic languages allow variable types to be changed and offer flexibility.
  - 📝 Static languages provide compile-time checks, making the code more robust.
  - 📝 Dynamic languages lack compile-time checks and may be slower.
  - 📝 Dynamic languages like JavaScript are recommended for beginners and smaller-scale applications.
  - 📝 Static languages are more suitable for large-scale applications and scenarios requiring specific interfaces and APIs.
  - 💨 Dynamic languages like JavaScript perform compilation on the runtime, leading to potential slowdowns due to runtime checks.
  - 💪 Static languages like C++ restrict data types upfront, resulting in simpler and more efficient code.

**Tips**

  - Normal TS utility types like Omit and Pick will not work with Unions. So you need to write your own version of these utils that look like this.
    ```ts
    export type UnionOmit<T, K extends string | number | symbol> = T extends unknown
      ? Omit<T, K>
      : never;
    ```
  - The type string | number | symbol is equal to the global type PropertyKey
      ```ts
      type Foo = PropertyKey;
      //     ^? string | number | symbol`
      ```
      
**Mistakes**

  - 💡 Mistake 1 Not understanding the difference between the **unknown** and **any** types. The unknown type allows developers to indicate that they don't know the current type of a variable but will know it later when they use it. In contrast, the any type completely removes type checks and should be avoided.
  - 💡 Mistake 2 Not utilizing type guards and the **is** operator for type inference. Type guards help determine the specific type of an object, allowing better code organization and improved developer experience.
  - 💡 Mistake 3 Using number-based enums without specifying values. This can lead to less reliable code. Instead, it's recommended to use string-based enums or declare a type with string literals.
  - 💡 Mistake 4 Neglecting to use built-in predefined utility types. TypeScript provides utility types like partial, omit, and record, which can greatly simplify code and improve type safety. Partial makes all properties of an interface optional, omit removes specified properties, and record defines a specific set of keys and their corresponding value types.

    
