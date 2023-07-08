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

**7. Explain the use of declare**

  - The declare keyword in TypeScript is used for the Ambient declaration of variables or for methods. Ambient Declarations is like an import keyword. Which tells the compiler that the source exists in another file

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
  - Basic react useState implementation
    ```ts
    // simple react useState hook example
    // Concepts: Closures, Generic, Type annotation, optional params etc
    const useState = <T>(
      initial?: T
    ): [() => T | undefined, (newValue: T) => void] => {
      const _initialVal = initial;
      let state = initial;
      return [() => state, (newValue: T) => (state = newValue)];
    };
    
    const [count, setCount] = useState<number>(10);
    console.log(count()); // 10
    setCount(50);
    console.log(count()); // 50
    ```
