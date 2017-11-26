```jsx
import React from 'react'

import { BrowserRouter, Route } from 'react-router-dom'

const Home = (props) => {
  console.log('Home props: ', props)
  return <h1>Home</h1>
}

const About = (props) => {
  console.log('About props: ', props)
  return <h1>About</h1>
}

const Contact = (props) => {
  console.log('Contact props: ', props)
  return <h1>Contact</h1>
}

const Location = (props) => {
  return props.match && <h1>Location</h1>
}

const App = () => (
  <BrowserRouter>
    <div>
      <Route exact path='/' component={Home} />
      <Route strict path='/about/' component={About} />
      <Route path='/contact' render={Contact} />
      <Route path='/location' children={Location} />
    </div>
  </BrowserRouter>
)

export default App
```



