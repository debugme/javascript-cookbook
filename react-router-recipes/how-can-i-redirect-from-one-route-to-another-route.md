```jsx
import React from 'react'
import { BrowserRouter, Route, Link, Switch, Redirect } from 'react-router-dom'

const Links = () => (
  <nav>
    <Link to='/'>Home</Link>
    <Link to='/old/123'>Old</Link>
    <Link to='/new/456'>New</Link>
    <Link to='/protected'>Protected</Link>
  </nav>
)

const loggedIn = false

const App = () => (
  <BrowserRouter>
    <div>
      <Links />
      <Route exact path='/' render={() => <h1>Home</h1>} />
      <Route path='/new/:value' render={({ match }) => <h1>{match.params.value}</h1>} />
      <Route path='/old/:value' render={({ match }) => <Redirect to={`/new/${match.params.value}`} />} />
      <Route path='/protected' render={() => (
        loggedIn ? <h1>Welcome to protected page</h1> : <Redirect to='/new/Login' />
      )} />
    </div>
  </BrowserRouter>
)

export default App
```

```js
// Notes
// (1) Clicking the `Old` link will redirect to te `New` page (Carrying over any parameters)
// (2) Clicking the `Protected` link will either render or redirect based on the value of `loggedIn`
```



