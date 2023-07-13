**1. What is RxJS?**
    
  - RxJS is a library for reactive programming using Observables to handle asynchronous and event-based operations in JavaScript.

**2. What is a Stream?**
    
  - A stream is a sequence of ongoing events over time, where data is continuously flowing and can be processed asynchronously.

**3. What is Reactive Programming?**

  - Reactive programming is a programming paradigm that focuses on propagating and responding to changes or events in a reactive and declarative manner.
  - The advantages of reactive programming include better handling of asynchronous operations, easier composition of complex event-driven systems, and efficient handling of data streams.
  - Non-blocking in RxJS means that the code execution is not blocked while waiting for an asynchronous operation to complete, allowing the program to continue processing other tasks.
  - Examples: click events, HTTP requests, ingested messages, availability notifications, literally anything that may change or happen.
![image](https://github.com/Malong11-007/javascript-iq/assets/40298510/d5974cd4-c380-4990-9185-57991da92a07)

**6. What is Back-Pressure in Reactive Programming?**
    
  - Back-pressure in reactive programming refers to the mechanism of controlling the flow of data when the producer emits data faster than the consumer can process it, preventing overwhelming the system.
  - These mechanisms can come in either the form of lossy or loss-less operations, each of which depends on the requirements.
  - For example, if you miss a few mouse movements, it may not be a problem, however, if you miss a few bank transactions, that could definitely be a problem.
  - Lossy Backpressure
      - **Debounce**: Emits the most recent value from the source Observable after a specified duration of silence.
      - **Throttle**: Emits the first value from the source Observable and then ignores subsequent values for a specified duration.
      - **AuditTime**: Emits the most recent value from the source Observable at regular intervals defined by the duration.
  - Loss-less Backpressure
      - **Buffer / bufferWithTimeOrCount**: This allows the consumer to set either the number of items they wish to wait for at a time, or a particular timespan, or both, whichever comes first
  - https://codeburst.io/a-look-at-back-pressure-and-its-handling-in-rxjs-5bc8f04a2e8f

**7. What is an Observable?**
    
  - An Observable is a core component in RxJS that represents a stream of values or events over time, which can be observed and processed by subscribing to it.

**8. What is the difference between an Observable and a Promise?**
    
  - The main difference between an Observable and a Promise is that an Observable can emit multiple values over time, while a Promise represents a single value or the eventual completion of an asynchronous operation.

**9. What is the difference between Cold and Hot Observables?**
    
  - Cold observables start emitting data only when subscribed to, while hot observables continue emitting data regardless of whether there are subscribers or not.
  - When the data is produced by the Observable itself, we call it a cold Observable. When the data is produced outside the Observable, we call it a hot Observable.
  - A cold observable starts producing data when some code invokes a subscribe() function on it. For example, your app may declare an observable providing a URL on the server to get certain products. The request will be made only when you subscribe to it. If another script makes the same request to the server, it’ll get the same set of data.
  - A hot observable produces data even if no subscribers are interested in the data. For example, an accelerometer in your smartphone produces data about the position of your device, even if no app subscribes to this data. A server can produce the latest stock prices even if no user is interested in this stock.

**10. What are RxJS Operators?**
    
  - RxJS operators are functions that can be used to transform, filter, combine, or manipulate Observables to perform various operations on data streams.

**11. What are Observers and Subscriptions?**
    
  - Observers are objects that define how to handle values or events emitted by an Observable, while subscriptions represent the connection between an Observer and an Observable, enabling the observation and cancellation of the stream.

**12. What is a Subject?**
    
  - A Subject is a special type of Observable that can act as both an Observable and an Observer, Allowing values to be multicast to multiple subscribers.
  - Types of subject 
      - Subject: It allows multicasting and acts as both an observable and an observer.
        ```typescript
        // Subject example
        const subject = new Subject<number>();
        
        subject.subscribe((value) => {
          console.log(`Subscriber A: ${value}`);
        });
        
        subject.subscribe((value) => {
          console.log(`Subscriber B: ${value}`);
        });
        
        subject.next(1);
        subject.next(2);
        
        /*
        Output:
        Subscriber A: 1
        Subscriber B: 1
        Subscriber A: 2
        Subscriber B: 2
        */
        ```
      - BehaviorSubject: It is a variant of Subject that stores the latest value and emits it immediately to new subscribers. It requires an initial value and always emits the most recent value to subscribers.
        ```typescript
        // BehaviorSubject example
        const behaviorSubject = new BehaviorSubject<number>(0);
        
        behaviorSubject.subscribe((value) => {
          console.log(`Subscriber A: ${value}`);
        });
        
        behaviorSubject.next(1);
        
        behaviorSubject.subscribe((value) => {
          console.log(`Subscriber B: ${value}`);
        });
        
        behaviorSubject.next(2);
        
        /*
        Output:
        Subscriber A: 0
        Subscriber A: 1
        Subscriber B: 1
        Subscriber A: 2
        Subscriber B: 2
        */
        ```
      - ReplaySubject: It is a variant of Subject that buffers a specific number of values and replays them to new subscribers. It maintains a buffer of values, and new subscribers receive values from that buffer.
         ```typescript
        // ReplaySubject example
        const replaySubject = new ReplaySubject<number>(2);
        
        replaySubject.subscribe((value) => {
          console.log(`Subscriber A: ${value}`);
        });
        
        replaySubject.next(1);
        replaySubject.next(2);
        replaySubject.next(3);
        
        replaySubject.subscribe((value) => {
          console.log(`Subscriber B: ${value}`);
        });
        
        /*
        Output:
        Subscriber A: 1
        Subscriber A: 2
        Subscriber A: 3
        Subscriber B: 2
        Subscriber B: 3
        */
        ```
      - AsyncSubject: It is a variant of Subject that only emits the last value it receives and only when the complete() method is called. It emits the value to subscribers only when the source observable completes.
        ```typescript
        // AsyncSubject example
        const asyncSubject = new AsyncSubject<number>();
        
        asyncSubject.subscribe((value) => {
          console.log(`Subscriber A: ${value}`);
        });
        
        asyncSubject.next(1);
        asyncSubject.next(2);
        asyncSubject.next(3);
        asyncSubject.complete();
        
        asyncSubject.subscribe((value) => {
          console.log(`Subscriber B: ${value}`);
        });
        
        /*
        Output:
        Subscriber A: 3
        Subscriber B: 3
        */
        ```    

**13. What are different types of Subjects?**
    
  - The different types of Subjects in RxJS include BehaviorSubject, ReplaySubject, and AsyncSubject, each with specific characteristics for handling values and subscriptions.

**14. What are Schedulers?**
    
  - Schedulers in RxJS provide control over the execution and concurrency of Observables, allowing tasks to be scheduled and executed on different threads or time intervals.

**15. What is RxJS Map and Higher-Order Observable Mapping?**
    
  - RxJS Map is an operator used to transform each emitted value of an Observable into another value. Higher-Order Observable Mapping refers to mapping an Observable to another Observable, allowing for complex transformations.

**16. When do we use switchMap, mergeMap, exhaustMap, and concatMap?**
    
  - switchMap is used when you want to cancel the previous inner Observable and switch to a new one, mergeMap is used when you want to merge inner Observables and emit values as they arrive, exhaustMap ignores new inner Observables until the current one completes, and concatMap maintains the order of emitted values by concatenating the inner Observables.

**17. When do we use zip, combineLatest, and withLatestFrom?**
    
  - zip combines the latest values from multiple Observables into an array, combineLatest combines the latest values from multiple Observables into a new value, and withLatestFrom combines the latest value from one Observable with the latest values from other Observables.

**18. Why is RxJS important for Angular?**
    
  - RxJS is important for Angular because it provides a powerful toolset for handling asynchronous operations, managing data streams, and building reactive and event-driven applications in the Angular framework.
