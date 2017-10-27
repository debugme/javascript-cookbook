```js
const eventFrom = document.querySelector('#buttonStuff')
const eventType = 'click'
const clickStream = Rx.Observable.fromEvent(eventFrom, eventType)

clickStream
  .filter(event => event.detail > 1)
  .debounceTime(500)
  .map(doubleClick => new Date().getTime())
  .subscribe(timestamp => console.log(timestamp))
```



