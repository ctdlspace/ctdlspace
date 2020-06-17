# React Coding Convention

## Components Naming
- exportable components are real functions — becouse this way React show components name in the inspector

```
export function Component(props) {
  const {} = props
  return (
    <div className="component">...</div>
  )
}

export function Component_subComponent(props) {
  const {} = props
  return (
    <div className="component_subComponent">...</div>
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
