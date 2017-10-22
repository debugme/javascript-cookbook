```jsx
import React from 'react'
import { BrowserRouter, Route, Link } from 'react-router-dom'

const Home = () => (<h1>Home</h1>)

const Menu = () => (
  <div>
    <h1>Menu</h1>
    <Link to='/menu/food'>Food</Link>
    <Link to='/menu/drink'>Drink</Link>
    <Route path='/menu/:part' render={(props) => <h2>{props.match.params.part}</h2>} />
  </div>
)

const App = () => (
  <BrowserRouter>
    <div>
      <Link to='/'>Home</Link>
      <Link to='/menu'>Menu</Link>
      <Route exact path='/' component={Home} />
      <Route path='/menu' component={Menu} />
    </div>
  </BrowserRouter>
)

export default App

```



