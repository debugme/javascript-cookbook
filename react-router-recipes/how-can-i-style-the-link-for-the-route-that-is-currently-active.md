

```scss
a { margin: 5px; }
a, a.visited { color: blue; }
a.active { color: red; }
```

```jsx
import React from 'react'
import { BrowserRouter, Route, NavLink } from 'react-router-dom'

const isActive = (match, location) => { console.log(match, location); return match }

const Links = () => (
  <nav>
    <NavLink exact activeClassName='active' to='/'>Home</NavLink>
    <NavLink activeStyle={{ color: 'red' }} to={{ pathname: '/about' }}>About</NavLink>
    <NavLink isActive={isActive} activeClassName='active' to="/contact">Contact</NavLink>
  </nav>
)

const App = () => (
  <BrowserRouter>
    <div>
      <Links />
      <Route exact path='/' component={() => <h1>Home</h1>} />
      <Route path='/about' component={() => <h1>About</h1>} />
      <Route path='/contact' component={() => <h1>Contact</h1>} />
    </div>
  </BrowserRouter>
)

export default App
```



