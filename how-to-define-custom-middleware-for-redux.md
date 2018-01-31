```jsx
const asyncMiddleware = (store) => (next) => (action) => {
  const { 
    type, 
    payload 
  } = action
  const { 
    isAsyncRequest
    endpoint, 
    buildSuccessAction, 
    buildFailureAction
  } = payload

  // Case1: Pass action onto the next middleware in the chain
  if (!isAsyncRequest) {
    return next(action)
  }

  // Case2: Resolve the request and pass action back into top of middleware chain
  return fetch(endpoint)
    .then((response) => response.json())
    .then((jsonData) => store.dispatch(buildSuccessAction(jsonData)))
    .then((error) => store.dispatch(buildFailureAction(error)))
}
```



