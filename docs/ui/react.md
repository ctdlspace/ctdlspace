# React Coding Convention

## Components Naming
- ComponentName is always in PascalCase, subComponent name is always in camelCase. Example: ComponentName_subComponentName
- Underscore '\_' sets hard hierarchy. Which means that <ComponentName_subComponent/> have to always have <ComponentName/> as a direct parent. If strong hierachy is set this also means that parent can't accept other children except of based on hierarchy
- Underscore + UCFirst  '\_\[A-Z]{1}' sets soft hierarchy. Which is means that <ComponentName_SoftSubComponent/> have to be somewere in <ComponentName/> tree but not neccessary directly. 
- Uppercase means extension / composition
- Exportable components are real functions — becouse this way React show components name in the inspector

```javascript
function Page(props) {
  const {children} = props
  return <div>{children}<div>
}

function Page_content(props) {
  const {children} = props
  return <div>{children}<div>
}

function Component_Title(props) {
  const {children} = props
  return <div>{children}<div>
}

function Form(props) {
  const {children} = props
  return <form>{children}<div>
}

function FormAjax(props) {
  const {children, onSubmit} = props
  const forwarSubmitEvent = e => {
    e.preventDefault()
    onSumbit(e)
  }
  return <Form onSubmit={forwarSubmitEvent}>{children}<div>
}

// Wrong - hard hierarchy is broken
<Page>
  <div className="wrapper"><Page_content>content</Page_content></div>
</Page>

// Wrong - soft hierarchy is broken
<div>
  <Page_Title>Title 1</Page_Title>
  <Page>
    <div className="wrapper"><Page_content>content</Page_content></div>
  </Page>
</div>

// Wrone - you can use soft hierarchy elements everywhere under parent tree but Page have hard hierarchy defined so its cant accept Page__title anymore&
<Page>
  <Page_Title>Title 1</Page_Title>
  <Page_content>
    <Page_Title>Title 2</Page_Title>
    content
    </Page_content/>
</Page>

// Correct - you can use hard hierarchy elements directly under the parent
<Page>
  <Page_content>content</Page_content/>
</Page>

// Correct 
// - you can use hard hierarchy elements directly under the parent
// - if parent have strong hierarchy set it can't contain anything except of defined children
// - Page_Title is soft hierarchy element and can be used everywhere under Page tree
<Page>
  <Page_content>
    <div className="pageTitleWrapper"><Page_Title>Page title</Page_Title></div>
    content
  </Page_content/>
</Page>

```


```javascript
export function Component(props) {
  const {} = props
  return (
    <div className="component">...</div>
  )
}

export function Component_hardSubComponent(props) {
  const {} = props
  return (
    <div className="component_hardSubComponent">...</div>
  )
}

export function Component__softSubComponent(props) {
  const {} = props
  return (
    <div className="component__hardSubComponent">...</div>
  )
}
```

## Composition

## [Data Driven Components](#data-driven-components) 
Data-driven components are the components attended to render datasets. 

- IMPORTANT: rule for all the data-driven components is that they only can be used where data is explicitly coming from the external data sources (databases, API's)
- IMPORTANT: rull for all the data driven components is that they should be renderable manually. Once more: if you can provide data to the component this should not block you from render the same manually. 

Bad
```
const data = [
  { title: 'Name1' },
  { title: 'Name2' }
]
<Table data={data}/>
```

Good
```
<Table>
  <Tr>
    <Td>Name 1</Td>
  <Tr>
  <Tr>
    <Td>Name 2</Td>
  <Tr>
</Table>

or

const data = fetchDataFromApiOrDatabase()
const data = [
  { title: 'Name1' },
  { title: 'Name2' }
]
<Table data={data}/>

```
