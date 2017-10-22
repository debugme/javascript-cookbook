```jsx
import React, { Component } from 'react'
import { BrowserRouter, Route, Link, Prompt } from 'react-router-dom'

const Home = () => (<h1>Home</h1>)

class Form extends Component {
  state = { dirty: false }
  setDirty = () => this.setState({ dirty: true })
  render = () => (
    <div>
      <h1>Form</h1>
      <input type="text" onInput={this.setDirty} />
      <Prompt when={this.state.dirty} message='Data will be lost!' />
    </div>
  )
}


const App = () => (
  <BrowserRouter>
    <div>
      <Link to='/'>Home</Link>
      <Link to='/form'>Form</Link>
      <Route exact path='/' component={Home} />
      <Route path='/form' component={Form} />
    </div>
  </BrowserRouter>
)

export default App
```



