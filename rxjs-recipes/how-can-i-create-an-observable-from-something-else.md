```js

const { from, of, pairs, fromEvent } = Rx.Observable
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
```



