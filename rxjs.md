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

**4. What is Back-Pressure in Reactive Programming?**
    
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

**5. What is an Observable?**
    
  - An Observable is a core component in RxJS that represents a stream of values or events over time, which can be observed and processed by subscribing to it.

**6. What is the difference between an Observable and a Promise?**
    
  - The main difference between an Observable and a Promise is that an Observable can emit multiple values over time, while a Promise represents a single value or the eventual completion of an asynchronous operation.

**7. What is the difference between Cold and Hot Observables?**
    
  - Cold observables start emitting data only when subscribed to, while hot observables continue emitting data regardless of whether there are subscribers or not.
  - When the data is produced by the Observable itself, we call it a cold Observable. When the data is produced outside the Observable, we call it a hot Observable.
  - A cold observable starts producing data when some code invokes a subscribe() function on it. For example, your app may declare an observable providing a URL on the server to get certain products. The request will be made only when you subscribe to it. If another script makes the same request to the server, it’ll get the same set of data.
  - A hot observable produces data even if no subscribers are interested in the data. For example, an accelerometer in your smartphone produces data about the position of your device, even if no app subscribes to this data. A server can produce the latest stock prices even if no user is interested in this stock.

**8. What are RxJS Operators?**
    
  - RxJS operators are functions that can be used to transform, filter, combine, or manipulate Observables to perform various operations on data streams.

**9. What are Observers and Subscriptions?**
    
  - Observers are objects that define how to handle values or events emitted by an Observable, while subscriptions represent the connection between an Observer and an Observable, enabling the observation and cancellation of the stream.

**10. What is a Subject?**
    
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

**11. Explain popular RxJS operators**
- `map`: Transforms each emitted value by applying a function to it.
  ```javascript
  import { from } from 'rxjs';
  import { map } from 'rxjs/operators';

  const source = from([1, 2, 3, 4, 5]);
  const mapped = source.pipe(map(value => value * 2));

  mapped.subscribe(value => console.log(value));
  // Output: 2, 4, 6, 8, 10
  ```

- `filter`: Filters emitted values based on a condition.
  ```javascript
  import { from } from 'rxjs';
  import { filter } from 'rxjs/operators';

  const source = from([1, 2, 3, 4, 5]);
  const filtered = source.pipe(filter(value => value % 2 === 0));

  filtered.subscribe(value => console.log(value));
  // Output: 2, 4
  ```

- `take`: Emits only a specified number of values and completes.
  ```javascript
  import { interval } from 'rxjs';
  import { take } from 'rxjs/operators';

  const source = interval(1000);
  const limited = source.pipe(take(3));

  limited.subscribe(value => console.log(value));
  // Output: 0, 1, 2
  ```

- `mergeMap` (also known as `flatMap`): Projects each emitted value to an Observable, then merges the resulting Observables into one.
  ```javascript
  import { of } from 'rxjs';
  import { mergeMap } from 'rxjs/operators';

  const source = of(1, 2, 3);
  const merged = source.pipe(mergeMap(value => of(value * 2)));

  merged.subscribe(value => console.log(value));
  // Output: 2, 4, 6
  ```

- `debounceTime`: Emits a value from the source Observable only after a specified duration has passed without any new values.
  ```javascript
  import { fromEvent } from 'rxjs';
  import { debounceTime } from 'rxjs/operators';

  const input = document.querySelector('input');
  const source = fromEvent(input, 'input');
  const debounced = source.pipe(debounceTime(500));

  debounced.subscribe(event => console.log(event.target.value));
  // Output: (after 500ms of inactivity) Emits the latest input value
  ```


- `concatMap`: Projects each source value to an Observable which is merged in the output Observable in a serialized manner, waiting for each inner Observable to complete before moving on to the next.
  ```javascript
  import { of } from 'rxjs';
  import { concatMap, delay } from 'rxjs/operators';

  const source = of(1, 2, 3);
  const concatenated = source.pipe(
    concatMap(value => of(value).pipe(delay(1000)))
  );

  concatenated.subscribe(value => console.log(value));
  // Output: 1 (after 1 second), 2 (after 2 seconds), 3 (after 3 seconds)
  ```

- `retry`: Resubscribes to the source Observable if it errors, for a maximum number of retry attempts.
  ```javascript
  import { of } from 'rxjs';
  import { ajax } from 'rxjs/ajax';
  import { retry } from 'rxjs/operators';

  const url = 'https://api.example.com/data';
  const request = ajax.getJSON(url).pipe(retry(3));

  request.subscribe(
    response => console.log(response),
    error => console.error('Error:', error)
  );
  ```

- `distinctUntilChanged`: Only emits values from the source Observable if they are different from the previous value.
  ```javascript
  import { from } from 'rxjs';
  import { distinctUntilChanged } from 'rxjs/operators';

  const source = from([1, 1, 2, 2, 3, 3, 3, 4, 4, 4]);
  const distinct = source.pipe(distinctUntilChanged());

  distinct.subscribe(value => console.log(value));
  // Output: 1, 2, 3, 4
  ```

- `scan`: Applies an accumulator function over the source Observable and emits each intermediate result.
  ```javascript
  import { from } from 'rxjs';
  import { scan } from 'rxjs/operators';

  const source = from([1, 2, 3, 4, 5]);
  const accumulated = source.pipe(scan((acc, value) => acc + value, 0));

  accumulated.subscribe(value => console.log(value));
  // Output: 1, 3, 6, 10, 15
  ```

- `switchMap`: Projects each source value to an Observable which is merged in the output Observable, cancelling any previous inner Observables.
  ```javascript
  import { fromEvent, interval } from 'rxjs';
  import { switchMap } from 'rxjs/operators';

  const button = document.querySelector('button');
  const clicks = fromEvent(button, 'click');
  const timer = interval(1000);
  const result = clicks.pipe(switchMap(() => timer));

  result.subscribe(value => console.log(value));
  // Output: 0, 1, 2, 3, ...
  ```

- `tap`: Allows you to perform side effects for each value emitted by the source Observable without modifying the emitted values. It is often used for debugging, logging, or triggering actions.
  ```javascript
  import { from } from 'rxjs';
  import { tap } from 'rxjs/operators';

  const source = from([1, 2, 3, 4, 5]);
  const tapped = source.pipe(
    tap(value => console.log('Received value:', value))
  );

  tapped.subscribe(value => console.log('Processed value:', value));
  // Output: Received value: 1, Processed value: 1, ...
  ```

- `pipe`: Used to combine multiple operators into a chain, allowing you to apply them sequentially to an Observable. It provides a concise and readable way to compose complex data transformations.
  ```javascript
  import { of } from 'rxjs';
  import { map, filter } from 'rxjs/operators';

  const source = of(1, 2, 3, 4, 5);
  const transformed = source.pipe(
    filter(value => value % 2 === 0),
    map(value => value * 2)
  );

  transformed.subscribe(value => console.log(value));
  // Output: 4, 8
  ```

- `share`: Converts a cold Observable into a hot Observable, causing multiple subscribers to share the same execution and receive the same sequence of values. It helps avoid duplicating expensive operations or network requests.
  ```javascript
  import { interval } from 'rxjs';
  import { take, share } from 'rxjs/operators';

  const source = interval(1000).pipe(take(5), share());

  source.subscribe(value => console.log('Subscriber 1:', value));
  // Output: Subscriber 1: 0, Subscriber 1: 1, ...

  setTimeout(() => {
    source.subscribe(value => console.log('Subscriber 2:', value));
    // Output: Subscriber 2: 2, Subscriber 2: 3, ...
  }, 2500);
  ```

- `retryWhen`: Retries the source Observable when a notifier Observable emits a value or completes, allowing you to implement custom retry logic. It is often used when retrying failed HTTP requests.
  ```javascript
  import { ajax } from 'rxjs/ajax';
  import { retryWhen, delay } from 'rxjs/operators';

  const url = 'https://api.example.com/data';
  const request = ajax.getJSON(url).pipe(
    retryWhen(errors => errors.pipe(delay(1000)))
  );

  request.subscribe(
    response => console.log(response),
    error => console.error('Error:', error)
  );
  ```
- `zip`: Combines multiple Observables by emitting an array of values, where the nth value contains the nth value from each source Observable. It waits for all source Observables to emit before emitting a new array.
  ```javascript
  import { zip, interval } from 'rxjs';

  const source1 = interval(1000);
  const source2 = interval(500).pipe(take(4));
  const zipped = zip(source1, source2);

  zipped.subscribe(value => console.log(value));
  // Output: [0, 0], [1, 1], [2, 2], [3, 3]
  ```

- `combineLatest`: Combines multiple Observables by emitting an array of the latest values, where the nth value contains the latest value from each source Observable. It emits whenever any source Observable emits a new value.
  ```javascript
  import { combineLatest, interval } from 'rxjs';

  const source1 = interval(1000);
  const source2 = interval(2000);
  const combined = combineLatest(source1, source2);

  combined.subscribe(value => console.log(value));
  // Output: [0, 0], [1, 0], [2, 0], [2, 1], [3, 1], [4, 1], ...
  ```

- `withLatestFrom`: Combines the latest values from the source Observable with the latest values from other Observables, emitting a new value whenever the source Observable emits. It is similar to `combineLatest`, but only emits when the source Observable emits.
  ```javascript
  import { fromEvent, interval } from 'rxjs';
  import { withLatestFrom } from 'rxjs/operators';

  const button = document.querySelector('button');
  const source = interval(1000);
  const clickStream = fromEvent(button, 'click');
  const combined = source.pipe(withLatestFrom(clickStream));

  combined.subscribe(([value, event]) => console.log(value, event));
  // Output: 0 [MouseEvent], 1 [MouseEvent], 2 [MouseEvent], ...
  ```

- `exhaustMap`: Maps each source value to an inner Observable, ignores subsequent values until the inner Observable completes, and repeats this process for each new value emitted by the source Observable. It is useful for scenarios where you want to ignore new source values until the current inner Observable completes.
  ```javascript
  import { interval, of } from 'rxjs';
  import { exhaustMap, take } from 'rxjs/operators';

  const source = interval(1000).pipe(take(3));
  const inner = of('A', 'B', 'C').pipe(delay(500));
  const result = source.pipe(exhaustMap(() => inner));

  result.subscribe(value => console.log(value));
  // Output: A, B, C
  ```
Useful Links:
- https://thinkrx.io/rxjs/
- https://rxjs.dev/
