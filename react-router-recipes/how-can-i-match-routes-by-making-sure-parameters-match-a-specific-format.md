```jsx
import React from 'react'
import { BrowserRouter, Route } from 'react-router-dom'

// Only match route with parameter in `dd-ddd` format
const path = '/:a(\\d{2}-\\d{3})'

const render = ({match: { params: { a }}}) => <h1>{`${a}`}</h1>

const App = () => (
  <BrowserRouter>
    <div>
      <Route path={path} render={render} />
    </div>
  </BrowserRouter>
)

export default App

```



