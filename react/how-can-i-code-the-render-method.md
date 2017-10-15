```jsx
// Approach 1 - Imperative
const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    return (
        <p>{ firstName && lastName && title && <FullName {...{firstName, lastName, title }} > }</p>
    )
}

// Approach 2 - Imperative + Declarative
const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    return (
        <p>{ firstName && lastName && title && <FullName {...{firstName, lastName, title }} > }</p>
    )
}

// Approach 2 - Declarative
const NameHolder = (props) => {
    const { firstName, lastName, title } = props
    const isVisible = (firstName && lastName && title)
    return (
        <p><FullName {...{firstName, lastName, title, isVisible }} /></p>
    )
}









```



