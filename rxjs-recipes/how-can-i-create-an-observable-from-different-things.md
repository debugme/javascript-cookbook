```js
{
  console.group('How to subscribe to a series of numbers')
  const stream = Rx.Observable.of(1, 2, 3, 4, 5)
  const subscription = stream.subscribe(value => console.log(value))
  console.groupEnd()
}

{
  console.group('How to subscribe to an array of numbers')
  const stream = Rx.Observable.from([1, 2, 3, 4, 5])
  stream.subscribe(value => console.log(value))
  console.groupEnd()  
}

{
  console.group('How to transform an array of numbers')
  const stream = Rx.Observable.from([1, 'asad', 3, null, 5, {}, 7])  
  stream
    .map(value => parseInt(value, 10))
    .filter(value => !isNaN(value))
    .reduce((total, value) => total + value)
    .subscribe(result => console.log(result))
  console.groupEnd()
}
```



