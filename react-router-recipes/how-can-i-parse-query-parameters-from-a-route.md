```jsx
import React from 'react'
import { BrowserRouter, Route, Link } from 'react-router-dom'

const Links = () => (
  <nav>
    <Link to='/?id=123'>Inline</Link>
    <Link to={{ pathname: '/', search: 'id=456'}}>Object</Link>
  </nav>
)

const render = ({ match, location }) => (
  <div>
    <p>root</p>
    <p>{JSON.stringify(match)}</p>
    <p>{JSON.stringify(location)}</p>
    <p>{new URLSearchParams(location.search).get('id')}</p>
  </div>
)

const App = () => (
  <BrowserRouter>
    <div>
      <Links />
      <Route path='/' render={render} />
    </div>
  </BrowserRouter>
)

export default App

```



