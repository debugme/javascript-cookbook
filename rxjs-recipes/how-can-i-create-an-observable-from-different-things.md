```js
// How to subscribe to a series of numbers
Rx.Observable.of(1, 2, 3, 4, 5)
  .subscribe(value => console.log(value))

// How to subscribe to an array of numbers
Rx.Observable.from([1, 2, 3, 4, 5])
  .subscribe(value => console.log(value))

// How to transform an array of numbers
Rx.Observable.from([1, 'asad', 3, null, 5, {}, 7])  
  .map(value => parseInt(value, 10))
  .filter(value => !isNaN(value))
  .reduce((total, value) => total + value)
  .subscribe(result => console.log(result))

// How to listen to events on an HTML element
Rx.Observable.fromEvent(document.querySelector('#buttonStuff'), 'click')
  .map(event => new Date().getTime())
  .subscribe(timeStamp => console.log(timeStamp))
```



