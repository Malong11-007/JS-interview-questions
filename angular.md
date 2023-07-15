# Angular

 **What are the pros and cons of angular?**
  | Pros                                         | Cons                                                    |
  | -------------------------------------------- | ------------------------------------------------------- |
  | **Powerful framework:** Angular is a full-featured framework with a robust set of tools and features, making it suitable for building complex applications. | **Learning curve:** Angular has a steep learning curve compared to other JavaScript frameworks, primarily due to its extensive feature set and complex concepts. |
  | **TypeScript support:** Angular is built with TypeScript, which brings static typing and enhanced tooling, improving code quality and developer productivity. | **Complexity:** Angular's extensive feature set and conventions can make it complex and overwhelming for small or simple projects. |
  | **Enhanced performance:** Angular provides a performance-optimized architecture that minimizes page reloads and enables efficient rendering, resulting in faster and smoother user experiences. | **Bundle size:** Angular applications tend to have larger bundle sizes compared to some other frameworks, which can impact initial load times. |
  | **Code organization:** Angular enforces a modular architecture with components, services, and modules, promoting code reusability, maintainability, and scalability. | **Version updates:** Angular has a regular release cycle with major updates, which can require significant code refactoring and updates in larger projects. |
  | **Strong community and support:** Angular has a large and active community, providing ample resources, tutorials, and support, making it easier to find answers to questions or seek help when needed. | **Development speed:** Angular's emphasis on structure and conventions can slow down development, especially for small or straightforward projects. |
  | **Cross-platform development:** Angular allows building applications for web, mobile web, native mobile (using frameworks like NativeScript or Ionic), and even desktop (with Electron). | **Flexibility:** Angular's opinionated structure and conventions may limit flexibility compared to more lightweight or flexible frameworks. |
  | **Built-in testing tools:** Angular has a built-in testing framework (Jasmine) and offers excellent support for unit testing, making it easier to write and execute tests for your application. | **Tooling limitations:** Angular's extensive tooling can be overwhelming, and some developers may find the CLI (Command Line Interface) restrictive or limiting in certain scenarios. |

---

**Explain difference between SPA and MPA**
  |                      | SPA (Single-Page Application) | MPA (Multi-Page Application) |
  |----------------------|-------------------------------|------------------------------|
  | **Architecture**     | Operates within a single HTML page | Each page is a separate HTML document |
  | **User Experience**  | Fluid and interactive with faster page transitions | Slower transitions due to full page reloads |
  | **Performance**      | Dynamic content updates without full page reloads | Separate request/response cycle for each page |
  | **SEO**              | Challenges for SEO due to dynamically rendered content | Better support for SEO as each page can be indexed individually |
  | **Complexity**       | More complex with managing application state and memory leaks | Simpler development treating each page as a standalone entity |
  | **Framework** | Angular, React, Vue.js | JS Frameworks can be used to enhance interactivity but not mandatory. MPA Usually are build with Django, Ruby on Rails, or ASP.NET. |

  ---

**Compare Angular against famous frameworks.**
  | **Comparison Criteria**     | **Angular**                                                  | **React**                                                           | **Vue.js**                                                     |
  | -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------- | -------------------------------------------------------------- |
  | **Learning Curve**         | Steeper learning curve due to its extensive feature set.      | Relatively easier to learn and get started.                         | Easier to learn, especially for beginners.                      |
  | **Popularity and Community** | Widely adopted with a large and active community.            | Highly popular with a vast community and extensive ecosystem.       | Growing in popularity with an active and supportive community.  |
  | **Component-based Architecture** | Supports component-based architecture out of the box.      | Primarily focused on the component-based architecture.               | Built on the concept of components.                            |
  | **Virtual DOM**            | Angular uses a real DOM for rendering and updates.             | React uses a virtual DOM, allowing efficient rendering updates.     | Vue.js also uses a virtual DOM for efficient rendering.        |
  | **Size and Performance**    | Angular applications tend to have larger bundle sizes.        | React has a smaller bundle size compared to Angular.                  | Vue.js also has a smaller bundle size compared to Angular.    |
  | **Data Binding**            | Angular offers two-way data binding by default.                | React primarily uses one-way data binding for better performance.     | Supports both one-way and two-way data binding.                |
  | **Rendering Speed**         | Angular may be slightly slower due to its use of real DOM.    | React's virtual DOM allows for efficient rendering and better performance. | Vue.js provides fast rendering with its virtual DOM.           |
  | **Flexibility**             | Angular's opinionated structure may limit flexibility.         | React is highly flexible and allows integrating with existing projects.   | Vue.js offers flexibility and can be incrementally adopted.   |
  | **Tooling and Ecosystem**   | Angular provides a comprehensive CLI and a wide range of tools. | React has a robust ecosystem with various third-party tools and libraries. | Vue.js offers a versatile CLI and a growing ecosystem.         |
  | **Mobile App Development**  | Angular supports cross-platform mobile app development with frameworks like Ionic and NativeScript. | React Native enables building native mobile apps using React.      | Vue Native allows building native mobile apps using Vue.js.   |
  | **Famous Companies/Projects** | Google, Microsoft, IBM, General Electric                        | Facebook, Instagram, Netflix, Airbnb                                 | Alibaba                                                        |

---

**Different Ways to share data between Components** https://github.com/Malong11-007/angular-data-sharing
  1. Input/Output Binding:
     - Use `@Input` and `@Output` decorators to establish a parent-child relationship between components.
     - Example: Passing data from a parent component to a child component and vice versa, such as passing user information from a parent component to a child component to display user details.
  
  2. Component Communication with ViewChild:
     - Use `@ViewChild` decorator to get a reference to a child component in the parent component.
     - Example: Accessing properties or methods of a child component directly from the parent component.
  
  3. Services:
     - Create a service to share data between components.
     - Use RxJS subjects (Behavior / Replay) to create a centralized data store for sharing data.
     - Example: Sharing data between unrelated components or components at different levels of the component hierarchy.
  
  4. Event Emitters:
     - Use event emitters to emit custom events and notify other components.
     - Example: Notifying parent components about specific events or actions performed in child components.
  
  5. Route Parameters:
     - Use route parameters to pass data through the URL.
     - Example: Passing an ID in the URL to retrieve specific data from a backend server.
  
  6. Query Parameters:
     - Use query parameters to pass data as key-value pairs in the URL.
     - Example: Filtering or sorting data based on query parameters in a listing page.
  
  7. Local Storage/Session Storage:
     - Store data in the browser's local storage or session storage and access it from different components.
     - Example: Storing user preferences or temporary data that needs to persist across component instances.

---

**Explain data bindings in angular**
  - Bindings that allow you to establish communication between your component's data and the template
    1. Interpolation (`{{ }}`): Interpolation is a one-way binding technique that allows you to display component data in the template.
       ```html
       <p>Welcome, {{ name }}!</p>
       ```
    
    2. Property binding (`[ ]`): Property binding is a one-way binding technique that allows you to set a property value of an HTML element based on a component property.
       ```html
       <img [src]="imageUrl"> <!-- the `src` property of the `<img>` element will be bound to the value of the `imageUrl` property in the component. -->
       ```
    
    3. Event binding (`( )`): Event binding is a one-way binding technique that allows you to listen to events emitted by HTML elements and respond to them in the component.
       ```html
       <button (click)="handleClick()">Click me!</button>
       ```
    
    4. Two-way binding (`[( )]`): Two-way binding allows you to establish a two-way synchronization between a property in the component and an input control in the template. It combines property binding and event binding into a single syntax.
        ```html
        <input [(ngModel)]="name">
        ```

---

**How angular works?**
![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/10b6cee2-6383-4b5d-9b34-74b113a535c9)
![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/15dff29f-f888-4ae0-8059-4ea7ad28b2ef)


