```jsx
// Approach 1 - Higher Order Component
const withChuck = (Joke) => {
  class WithChuck extends Component {
    constructor(props) {
      super(props)
      this.state = { content: '', loading: false }
    }
    fetchJoke = asynch () => {
      this.setState({ loading: true })
      const endpoint = 'https://api.chucknorris.io/jokes/random'
      const response = await fetch(endpoint)
      this.setState({ loading: false, joke: response.value })
    }
    componentDidMount = () => {
      this.fetchJoke()
    }
    render = () => {
      const { content, loading } = state
      return <Joke {... { content, loading }} />
    }
  }
  return WithChuck
}

const Joke = ({ content, loading }) => {
  const text = loading 
    ? 'loading...please wait...' 
    : content
  return <div>{text}</div>  
}

const WithChuckJoke = withChuck(Joke)
RenderDOM.render(<Joke />, document.querySelector('main'))
```

```jsx
// Approach 2 - Render Props
class ChuckJoke extends Component {
  constructor(props) {
    super(props)
    this.state = { content: '', loading: false }
  }
  fetchJoke = asynch () => {
    const { endpoint } = this.props
    this.setState({ loading: true })
    const endpoint = 'https://api.chucknorris.io/jokes/random'
    const response = await fetch(endpoint)
    this.setState({ loading: false, joke: response.value })
  }
  componentDidMount = () => {
    this.fetchJoke()
  }
  render = () => {
    const { fetchJoke } = this
    const { content, loading, children } = this.props
    const props = {
      content,
      loading
    }
    return { children(props) }
  }
}

const Joke = () => {
  const renderProp = ({ content, loading }) => {
    const text = loading 
      ? 'loading...please wait...' 
      : content
    return <div>{text}</div>
  }
  return (
    <ChuckJoke>
      { renderProp }
    </ChuckJoke>  
  )
}

RenderDOM.render(<Joke />, document.querySelector('main'))


```



