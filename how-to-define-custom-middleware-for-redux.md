```jsx
const asyncMiddleware = (store) => (nextMiddleware) => (action) => {
  // (1) Pull out data from passed in action
  const { 
    type, 
    payload 
  } = action
  const { 
    isAsyncRequest
    endpoint, 
    onSuccess, 
    onFailure
  } = payload

  // (2) Define some helpers
  const extractJsonCargo = (response) => response.json()
  const onRequestSuccess = (jsonData) => store.dispatch(onSuccess(jsonData))
  const onRequestFailure = (error) => store.dispatch(onFailure(error))    

  // (3A) Resolve the request and pass action back into top of middleware chain
  if (isAsyncRequest) {
    return fetch(endpoint)
      .then(extractJsonCargo)
      .then(onRequestSuccess)
      .catch(onRequestFailure)

  }

  // (3B) Pass action onto the next middleware in the chain
  return nextMiddleware(action)
}
```



