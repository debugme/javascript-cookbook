```js
// Case 1: A list of promises that pass using await and async
async function f () {
  try {
    const a = await Promise.resolve(1)
    const b = await Promise.resolve(2)
    console.log(`[case1] pass: ${a + b}`)
  } catch (error) {
    console.log(`[case1] fail: ${error.toString()}`)
  }

}

f()

// Case 2: A list of promises that fail using await and async
async function g () {
  try {
    const a = await Promise.resolve(1)
    const b = await Promise.reject(2)
    console.log(`[case2] pass: ${a + b}`)
  } catch (error) {
    console.log(`[case2] fail: ${error.toString()}`)
  }

}

g()
```



