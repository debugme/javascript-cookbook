```js
// A list of promises that pass using await and async
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
```

```js
// A list of promises that fail using await and async
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

```js
// The return value of an async function is wrapped in a promise
const getMessage = async () => 'hello'
getMessage().then((message) => console.log(message))
```

```js
// How can I make async requests in parallel fashion (Faster)

// Approach 1: Requests are made in parallel
async function getMovieDetails(){
  const request1 = $.getJSON('https://omdbapi.com?t=temple&apikey=thewdb')
  const request2 = $.getJSON('https://omdbapi.com?t=tide&apikey=thewdb')
  const details1 = await request1
  const details2 = await request2
  return [details1, details2]  
}

getMovieDetails().then(detailsList => detailsList.map(detail => console.log(detail)))


// Approach 2: requests are also made in parallel

```

```js
// How can I make async requests in serial fashion (Slower)
async function getMovieDetails(){
  const details1 = await $.getJSON('https://omdbapi.com?t=temple&apikey=thewdb')
  const details2 = await $.getJSON('https://omdbapi.com?t=tide&apikey=thewdb')  
  return [details1, details2]
}

getMovieDetails().then(detailsList => detailsList.map(detail => console.log(detail)))
```



