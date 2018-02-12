```jsx
// The code example below demonstrates the most common life-cycle methods.
// You can test this out by pasting the code below into the REPL here:
// https://jscomplete.com/repl/

class ReactContainer extends React.Component {
constructor (props) {
  super(props)
    this.state = { message: 'hello' }
    console.log('[container] constructor called...')
  }
  render() {
  console.log('[container] rendering state...')
  const { message } = this.state
  return <ReactLifeCycles message={message} />
  }
  componentDidMount() {
  setTimeout(() => {
    console.log('[container] updating state...')
    this.setState({ message: 'hi'})
    }, 1000)
  }
}

class ReactLifeCycles extends React.Component {
  constructor (props) {
    // Do NOT call setState() from this method  
    // Only put stuff in state if it will be used in the render() method
    super(props)
    this.state = { message: props.message }
    console.log('[component]   constructor called...')
  }
  
  componentWillMount () {
    // Do NOT call setState() from this method  
    console.log('[component]   componentWillMount called...')
  }
  
  componentDidMount () {
    // You can call setState() from this method if you need to  
    console.log('[component]   componentDidMount called...')
    this.headerTag.addEventListener('click', this.onClick)
    setTimeout(() => { 
    console.log('[component]   updating component state...')
    this.setState({ message: 'byebye' }) 
    }, 1000)
    setTimeout(() => { 
    console.log('[component]   updating component state again...')
    this.setState({ message: 'byebye' }) 
    }, 1000)
  }
  
  render () {
    // Do NOT call setState() from this method  
    const ref = (headerTag => (this.headerTag = headerTag))
    const { message } = this.state
    return <h1 ref={ref}>{message}</h1>
  }
  
  componentWillUpdate () {
    // Do NOT call setState() from this method
    console.log('[component]   componentWillUpdate called...')  
  }
  
  componentDidUpdate () {
    // Do NOT call setState() from this method
    console.log('[component]   componentDidUpdate called...')  
  }
  
  shouldComponentUpdate (nextProps, nextState) {
    // Do NOT call setState() from this method
    const isPropsChanged = (this.props.message !== nextProps.message)
    const isStateChanged = (this.state.message !== nextState.message)
    const isChanged = (isPropsChanged || isStateChanged)
    console.log(`[component]   shouldComponentUpdate called...${isChanged}`)
    return isChanged
  }
  
  componentWillReceiveProps () {
    // Do NOT call setState() from this method
    console.log('[component]   componentWillReceiveProps called...')
  }
  
  componentWillUnmount () {
    // Do NOT call setState() from this method
    console.log('[component]   componentWillUnmount called...')
    this.headerTag.removeEventListener('click', this.onClick)
  }
  
   onClick = (event) => console.log(`[component]   onClick called on ${event.target}`)
}

ReactDOM.render(<ReactContainer />, mountNode)

setTimeout(ReactDOM.unmountComponentAtNode.bind(ReactDOM, mountNode), 5000)


```



