```js
Rx.Observable.from([1, 'asad', 3, null, 5, {}, 7])  
  .map(value => parseInt(value, 10))
  .filter(value => !isNaN(value))
  .reduce((total, value) => total + value)
  .subscribe(result => console.log(result))


```



