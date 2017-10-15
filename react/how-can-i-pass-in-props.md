```jsx
// Approach 1 - Imperative
const { first, last, prefix } = props
const fullname = <FullName firstName={first} lastName={last} title={prefix} />




```

```jsx
// Approach 2 - Imperative + Declarative
const { first: firstName, last: lastName, prefix: title } = props
const fullName = <FullName firstName={firstName} lastName={lastName} title={title} />


```

```jsx
// Approach 3 - Declarative
const { first: firstName, last: lastName, prefix: title } = props
const fullName = <FullName {...{ firstName, lastName, title }} />
```



