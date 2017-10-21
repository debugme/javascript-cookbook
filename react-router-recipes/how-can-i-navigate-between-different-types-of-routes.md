```jsx
import React from 'react'

import { BrowserRouter, Route, Link } from 'react-router-dom'

const Links = () => (
  <nav>
    <Link to="/">Home</Link>
    <Link to={{pathname: '/about'}}>About</Link>
    <Link replace to="/contact">Contact</Link>
  </nav>
)

const App = () => (
  <BrowserRouter>
    <div>
      <Links />
      <Route exact path='/' component={() => <h1>Home</h1>} />
      <Route exact path='/about' component={() => <h1>About</h1>} />
      <Route exact path='/contact' component={() => <h1>Contact</h1>} />
    </div>
  </BrowserRouter>
)

export default App
```





