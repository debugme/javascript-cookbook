```js
Rx.Observable.fromEvent(document.querySelector('#buttonStuff'), 'click')
  .filter(event => event.detail > 1)
  .debounceTime(500)
  .subscribe(doubleClick => console.log(new Date().getTime()))
```



