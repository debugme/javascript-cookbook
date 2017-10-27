```js
// How can I transform an array of numbers?
Rx.Observable.from([1, 'asad', 3, null, 5, {}, 7])  
  .map(value => parseInt(value, 10))
  .filter(value => !isNaN(value))
  .reduce((total, value) => total + value)
  .subscribe(result => console.log(result))

// How can I listen to debounced double-click events on an HTML element?
Rx.Observable.fromEvent(document.querySelector('#buttonStuff'), 'click')
  .map(event => event.detail)
  .filter(clickCount => clickCount > 1)
  .debounceTime(500)
  .map(doubleClick => new Date().getTime())
  .subscribe(timeStamp => console.log(timeStamp))
```



