```js
const url = 'https://swapi.co/api/people/5'

const onPass = (response) => {
    if (response.ok) {
        return response.json()
    } else {
        throw new Error(error.status)
    }
}

const onFail = error => console.log(`error: ${error}`)

fetch(url)
    .then(onPass)
    .catch(onError)
    

     
```



