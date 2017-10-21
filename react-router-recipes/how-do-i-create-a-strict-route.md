```jsx
import React from 'react'

import { BrowserRouter, Route } from 'react-router-dom'

const Home = (props) => <h1>Home</h1>

const App = () => (
  <BrowserRouter>
    <div>
      <Route strict path='/home' component={Home} />
    </div>
  </BrowserRouter>
)

export default App
```

```js
// The above route will only match the following path
// http://localhost:3000/home
```



