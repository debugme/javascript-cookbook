```js
class Person {
  constructor() { this.name = 0 }
  setName1(name) { this.name = name }
  setName2 = function(name) { this.name = name }
  setName3 = (name) => this.name = name
}

const personOne = new Person()
const personTwo = new Person()

// Case1: Rebinding `this` IS allowed
personOne.setName1.call(personTwo, '1')
console.log('1: ', personTwo)

// Case2: Rebinding `this` IS allowed
personOne.setName2.call(personTwo, '2')
console.log('2: ', personTwo)

// Case3: Rebinding `this` NOT allowed
personOne.setName3.call(personTwo, '3')
console.log('3: ', personTwo)
```



