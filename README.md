# RxJS cheatsheet

This is my personal cheat sheet, i didn't commented this very well because my intention is just to make my life easier when i forget something about RxJS.

# The Stream
![alt text](https://github.com/lucasfrosty/rxjs-cheatsheet/raw/master/stream.png "Stream img")

# The observer
Inside the subscribe parameter we put 3 methods:
- next: the event call, the value param passed is the data passed by the function **someRxEvent.next(value);**
- error: when a event emit an error
- complete: this will be called when we want to end the event stream calling **someRxEvent.complete();**
```js
Rx.Observable
  .fromEvent(btn, 'click')
  .sampleTime(100)
  .subscribe(
    (value) => {
      console.log('My event: ', value.clientX);
    },
    (err) => {
      console.log('Error:', err);
    },
    () => {
      console.log('Event was completed!!');
    }
  );
```

# Commands

### sampleTime
will get the **most recent** emitted value within the time interval set as parameter
```js
Rx.Observable
  .fromEvent(btn, 'click')
  .sampleTime(100)
  .subscribe(
    () => console.log('clicked')
   );
```

### throttleTime
emits the value, then ignore all other values passed by within the time interval set as parameter
```js
Rx.Observable
  .fromEvent(btn, 'click')
  .throttleTime(100)
  .subscribe(
    () => console.log('clicked')
   );
```

### debounceTime
it's like a delay, and only dispatch the last event emitted
```js
Rx.Observable
  .fromEvent(btn, 'click')
  .debounceTime(5000)
  .subscribe(
    () => console.log('clicked')
   );
```