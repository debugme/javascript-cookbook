```jsx
// Approach 1 - Complex logic for conditional rendering in-situ with JSX fragment
const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    return ({ firstName && lastName && title && <FullName {...{firstName, lastName, title }}/> })
}

const FullName = (props) => {
    const { firstName, lastName, title } = props    
    // Elided code...
}
```

```jsx
// Approach 2 - Simple logic for conditional rendering in-situ with JSX fragment
const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    return ({ isVisible && <FullName {...{firstName, lastName, title }}/> })
}

const FullName = (props) => {
    const { firstName, lastName, title } = props    
    // Elided code...
}
```

```jsx
// Approach 3 - Logic for conditional rendering passed into JSX fragment
const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    return (<FullName {...{firstName, lastName, title, isVisible }}/>)
}

const FullName = (props) => {
    const { firstName, lastName, title, isVisible } = props    
    if (!isVisible) return null
    // Elided code...
}
```



