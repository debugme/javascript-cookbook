```jsx
import React from 'react'

import { BrowserRouter, Route } from 'react-router-dom'

const Home = (props) => <h1>Home</h1>

const App = () => (
  <BrowserRouter>
    <div>
      <Route path='/' component={Home} />
    </div>
  </BrowserRouter>
)

export default App
```

```js
// The above route will match any path that contains the default path e.g.
// http://localhost:3000
// http://localhost:3000/
// http://localhost:3000/hello
```



