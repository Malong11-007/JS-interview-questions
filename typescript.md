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
