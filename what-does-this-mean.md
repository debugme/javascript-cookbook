```js
//=======================================================
// Remember the acronym GONE (Global,Object,New,Explicit)
// It describes the different execution contexts within
// which "this" is evaluated in your code.
//=======================================================
```

```js
//=======================================================
//Global Execution Context
//=======================================================
this.console;                                      // (1)
//=======================================================
// (1) Outside of a function, "this" means the global object.
//     In a browser the global object is the window object.
//     So the code above is the same as window.console;
//=======================================================
```

```js
//=======================================================
// Object Execution Context
//=======================================================
var square = {
  width: 5,
  height: 5,
  getArea: function () {
    return this.width * this.height;                // (1)
  }
}

console.log("Area of square is " + square.getArea());
//=======================================================
// (1) When a function is called on an object, the value
//     of "this" inside that function, is the object that
//      the function is called on i.e. square.
//=======================================================
```

```js
//=======================================================
// New Execution Context
//=======================================================
function Human(name) {
  this.name = name;                                 // (1)
  this.printName = function () {
    console.log("My name is " + this.name);         // (2)
  }
}

var andy = new Human("Andrew");
andy.printName()
//=======================================================
// (1) When the "new" keyword is used along with a function call,
//     the function behaves like a constructor. It's almost
//     as if the function is rewritten to look like this:
//
//    function Human(name) {
//      var this = {};
//      this.name = name;
//      this.printName = function () {
//         console.log("My name is " + this.name);
//      }
//      return this;
//    }
//
//    It's the "this" object which the function generates
//    that gets returned assigned to the variable andy.
//
// (2) The value of "this" corresponds to the "this" object
//     that gets implicitly generated and returned on behalf
//     of your function.
//=======================================================
```

```js
//=======================================================
// Explicit Execution Context
//=======================================================
var resultA = {};
var resultB = {};
var resultC = {};

function sum(a, b) {
  this.answer = a + b;
}

function product(a, b) {
  this.answer = a * b;
}

sum.call(resultA, 2, 3);                            // (1)

product.apply(resultB, [2, 3]);                     // (2)

var product2 = product.bind(resultC);               // (3)
product2(4, 5);

console.log("2 + 3 is " + resultA.answer);
console.log("2 * 3 is " + resultB.answer);
console.log("4 * 5 is " + resultC.answer);
//=======================================================
// (1) We use the call() method on the sum() function to
//     explicitly use resultA as the value for "this"
//     inside of the sum() function
// (2) We use the apply() method on the product() function to
//     explicitly use resultB as the value for "this"
//     inside of the product() function
// (3) We use the bind() method on the product() function to
//     explicitly use resultC as the value for "this"
//     inside of the curried product() function
//
// [*] You may have noticed that call/apply result in a function call.
//     However, bind results in a new function, which you can call later on.
//=======================================================
```



