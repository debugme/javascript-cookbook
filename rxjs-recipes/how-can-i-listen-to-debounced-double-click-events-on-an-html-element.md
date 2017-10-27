```js
Rx.Observable.fromEvent(document.querySelector('#buttonStuff'), 'click')
  .map(event => event.detail)
  .filter(clickCount => clickCount > 1)
  .debounceTime(500)
  .map(doubleClick => new Date().getTime())
  .subscribe(timeStamp => console.log(timeStamp))
```



