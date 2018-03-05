```jsx
// How to instantiate a class using an object of that class
class Point {
  constructor(x, y) {
    this.x = x
    this.y = y
  }
  toString(){ return `(${this.x},${this.y})` }
}

const topLeft = new Point(0, 0)
const bottomRight = new topLeft.constructor(10, 10)
console.log(`topLeft is ${topLeft} bottomRight is ${bottomRight}`)
```



