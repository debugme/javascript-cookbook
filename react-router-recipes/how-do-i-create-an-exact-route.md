```jsx
import React from 'react'

import { BrowserRouter, Route } from 'react-router-dom'

const Home = (props) => <h1>Home</h1>

const App = () => (
  <BrowserRouter>
    <div>
      <Route exact path='/' component={Home} />
    </div>
  </BrowserRouter>
)

export default App
```

```js
// The above route will only match the following paths
// http://localhost:3000
// http://localhost:3000/
```



