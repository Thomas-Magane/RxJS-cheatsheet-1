# RxJS cheatsheet

This is my personal cheat sheet, i didn't commented this very well because my intention is just to make my life easier when i forget something about RxJS.


# Commands

### sampleTime
```js
const btn = document.querySelector('button');

// will get the MOST RECENTLY emitted value within the time interval set as parameter
Rx.Observable
  .fromEvent(btn, 'click')
  .sampleTime(5000)
  .subscribe(
    () => console.log('clicked')
   );
```