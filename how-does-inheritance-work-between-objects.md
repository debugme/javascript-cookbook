```js
// Define a constructor function
function Person(name) {
  this.name = name
}

// A constructor function has a `prototype` property
console.log(Person.prototype)

// The `prototype` property has a `constructor` property that points back to the constructor function
console.log(Person.prototype.constructor === Person)

// Instances of the constructor function are given a property of `__proto__`
const ben = new Person('Ben')
console.log(ben.__proto__)

// The `__proto__` property points to the constructor function's prototype
console.log(ben.__proto__ === Person.prototype)



```



