```js
// Define a constructor function
function Person(name) {
  this.name = name
}

// A constructor function has a `prototype` property
console.log(Person.prototype)

// The `prototype` property has a `constructor` property that aliases the constructor function
console.log(Person.prototype.constructor === Person)

// Instances of the constructor function are given a property of `__proto__`
const ben = new Person('Ben')
console.log(ben.__proto__)

// The `__proto__` property aliases the constructor function's prototype
console.log(ben.__proto__ === Person.prototype)

// Methods added to the constructor function's `prototype` property are shared between instances
Person.prototype.setName = function(name) {
  this.name = name
}
const alexis = new Person('Alexis')
const roger = new Person('Roger')
roger.setName('Roget')
console.log(alexis.age === 20 && alexis.age === roger.age)
console.log(alexis.setAge === roger.setAge)


// Properties and methods added to `this` in the constructor function are not shared between instances
```



