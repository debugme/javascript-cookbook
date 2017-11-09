```js
// Define a constructor function
function Person(name) {
  this.name = name
}
```

```js
// A constructor function has a `prototype` property
console.log(Person.prototype)
```

```js
// Instances of the constructor function are given a property of `__proto__`
const ben = new Person('Ben')
console.log(ben.__proto__)
```

```js
// The `__proto__` property aliases the constructor function's prototype
const errorMessage = 'Error: __proto__ should alias prototype'
console.assert(ben.__proto__ === Person.prototype, errorMessage)
```

```js
// Methods added to the constructor function's `prototype` property are shared between instances
Person.prototype.setName = function(name) {
  this.name = name
}
const alexis = new Person('Alexis')
const roger = new Person('Roger')
roger.setName('Roget')
const errorMessage = 'Error: setName should be the same'
console.assert(alexis.setName === roger.setName, errorMessage)
```

```js
// Properties and methods added to `this` in the constructor function are not shared between instances
function Person(name) {
  this.name = name
  this.setName = function(name) {
    this.name = name
  }
}
const robin = new Person('Robin')
const mladen = new Person('Mladen')
const errorMessage = 'Error: setName should be different'
console.assert(robin.setName !== mladen.setName,errorMessage )
```

```js
// Define properties and methods defined on the prototype property
Person.prototype.age = 10
Person.prototype.setAge = function(age) {
  this.age = age
}

// Notice how you can access them via instances (Rather than explicitly via `prototype`)
```

```js

```



