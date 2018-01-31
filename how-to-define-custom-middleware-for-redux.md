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
  const extractJsonData = (response) => response.json()
  const dispatchSuccess = (jsonData) => store.dispatch(onSuccess(jsonData))
  const dispatchFailure = (error) => store.dispatch(onFailure(error))    

  // (3A) Resolve the request and pass action back into top of middleware chain
  if (isAsyncRequest) {
    return fetch(endpoint)
      .then(extractJsonData)
      .then(dispatchSuccess)
      .catch(dispatchFailure)

  }

  // (3B) Pass action onto the next middleware in the chain
  return nextMiddleware(action)
}
```



