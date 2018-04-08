```jsx
// Define the reference using a string (Deprecated)
class AppOne extends Component {
  blur = () => this.refs.message.blur(),
  focus = () => this.refs.message.focus(),
  render = () => {
    return (
      <Fragment>
        <input type="text" ref="message" />
        <input type="button" onClick={this.blur} value="blur"/>
        <input type="button" onClick={this.focus} value="focus"/>
      </Fragment>
    )
  }
}

// Define the reference using a function (React 16.2 and below)
class AppTwo extends Component {
  blur = () => this.refs.message.blur(),
  focus = () => this.refs.message.focus(),  
  setReference = (reference) => this.message = reference,
  render = () => {
    return (
      <Fragment>
        <input type="text" ref={this.setReference} />
        <input type="button" onClick={this.blur} value="blur"/>
        <input type="button" onClick={this.focus} value="focus"/>
      </Fragment>
    )
  }  
}

// Define the reference using `createRef()` (React 16.3 and above)
class AppTwo extends Component {
  message = React.createRef()
  blur = () => this.message.current.blur(),
  focus = () => this.message.current.focus(),  
  render = () => {
    return (
      <Fragment>
        <input type="text" ref={this.message} />
        <input type="button" onClick={this.blur} value="blur"/>
        <input type="button" onClick={this.focus} value="focus"/>
      </Fragment>
    )
  }  
}



```



