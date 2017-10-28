```js
const { from, of, pairs, fromEvent, fromPromise } = Rx.Observable
const { info } = console

// How can I create a stream of characters from a string
const word = 'abcde'
from(word).subscribe(char => info(char))

// How can I create a stream of strings from an array
const animals = ['ape', 'bat', 'cat']
from(animals).subscribe(animal => info(animal))

// How can I create a stream of name-value pairs from an object
const insects = { a: 'ant', b: 'bee', c: 'centipede'}
pairs(insects).subscribe(insect => info(insect))

// How can I create a stream of values from a list of numbers
of(1, 2, 3).subscribe(value => info(value))

// How can I create a stream of events from a click on a button
const button = document.querySelector('.btn')
fromEvent(button, 'click').subscribe(event => info('clicked'))

// How can I create an Observable from a Promise
const url = 'https://swapi.co/api/people/1'
fromPromise(fetch(url).then(response => response.json()))
  .subscribe(data => info(data))

// How can I get a count of total clicks accumulated so far
fromEvent(button, 'click').scan((x, y) => x + 1, 0).subscribe(count => info(count))

// How can I make multiple asynch requests
const ids = [1, 2, 3]
from(ids)
  .map(id => `https://swapi.co/api/people/${id}`)
  .flatMap(url => fetch(url))
  .flatMap(response => response.json())
  .subscribe(x => info(x.name))
  
// How can I create an Observable that returns custom values?
new Rx.Observable((observer) => {
  observer.next('first-value')
  observer.next('second-value')
  observer.complete()
  }).subscribe(value => info(value))
```



