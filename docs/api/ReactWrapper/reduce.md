# `.reduce(fn[, initialValue]) => Any`

Applies the provided reducing function to every node in the wrapper to reduce to a single value.
Each node is passed in as a `ReactWrapper`, and is processed from left to right.


#### Arguments

1. `fn` (`Function`): A reducing function to be run for every node in the collection, with the
following arguments:
  - `value` (`T`): The value returned by the previous invocation of this function
  - `node` (`ReactWrapper`): A wrapper around the node being processed
  - `index` (`Number`): The index of the node being processed

2. `initialValue` (`T` [optional]): If provided, this will be passed in as the first argument to the first invocation of the reducing function. If omitted, the first `node` will be provided and the iteration will begin on the second node in the collection.


#### Returns

`T`: Returns an array of the returned values from the mapping function...


#### Example

```jsx
function Foo() {
  return (
    <div>
      <Bar amount={2} />
      <Bar amount={4} />
      <Bar amount={8} />
    </div>
  );
}
```

```jsx
const wrapper = mount(<Foo />);
const total = wrapper.find(Bar).reduce((amount, n) => amount + n.prop('amount'), 0);
expect(total).to.equal(14);
```


#### Related Methods

- [`.reduceRight(fn[, initialValue]) => Any`](reduceRight.md)
- [`.forEach(fn) => ReactWrapper`](forEach.md)
- [`.map(fn) => Array<Any>`](map.md)
