```jsx
// (1) Install the correct packages
npm add webpack-dev-middleware
npm add webpack-hot-middleware

// (2) Update your webpack configuration
  entry: [
    'webpack-hot-middleware/client?reload=true',
    'babel-regenerator-runtime',
    path.resolve(__dirname, 'source/')
  ],
  plugins: [
    new webpack.HotModuleReplacementPlugin(),
    new webpack.NamedModulesPlugin()
  ],

// source/client/index.jsx
import React from 'react'
import ReactDOM from 'react-dom'
import { Provider } from 'react-redux'
import Application from './application'
import getStore from './getStore'
const store = getStore()
const render = (Tag) => {
  const element = (
    <Provider store={store}>
      <Tag />
    </Provider>
  )
  const domNode = document.querySelector('main')
  ReactDOM.render(element, domNode)
}
render(Application)
if (module.hot) {
  module.hot.accept('./application', () => {
    const NextApplication = require('./application').default
    render(NextApplication)
  })
}

// source/server/server.jsx
import webpack from 'webpack'
const server = express()
const inDevelopmentMode = (process.env.NODE_ENV === 'development')
if (inDevelopmentMode) {
  const config = require('../webpack.config.dev.babel').default
  const compiler = webpack(config)
  const devMiddleware = require('webpack-dev-middleware')(compiler, { noInfo: true })
  const hotMiddleware = require('webpack-hot-middleware')(compiler)
  server.use(devMiddleware)
  server.use(hotMiddleware)
}
```



