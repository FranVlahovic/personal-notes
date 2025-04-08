## Simple array methods

```js
let arr = ["a", "b", "c", "d", "e"];
```

### SLICE

- The `slice()` method returns a `shallow copy` of a portion of an array into a `new array object` selected from `start to end` (end not included) where start and end represent the `index of items` in that `array`.

- The original `array` will not be `modified`
  .

```js
console.log(arr.slice(2));
// ['c', 'd', 'e']
console.log(arr.slice(2, 4));
// ['c', 'd']
console.log(arr.slice(-2));
// ['d', 'e']
console.log(arr.slice(-1));
// ['e']
console.log(arr.slice(1, -2));
// ['b', 'c']
console.log(arr.slice());
// ['a', 'b', 'c', 'd', 'e']
console.log([...arr]);
// ['a', 'b', 'c', 'd', 'e']
```

### SPLICE

- The `splice()` method changes the contents of an `array` by `removing` or `replacing` existing elements and/or `adding` new elements in place

```js
arr.splice(-1);
console.log(arr);
// ['a', 'b', 'c', 'd']

arr.splice(1, 2);
console.log(arr);
// ['a', 'd']
```

### REVERSE

```js
arr = ["a", "b", "c", "d", "e"];
const arr2 = ["j", "i", "h", "g", "f"];
console.log(arr2.reverse());
// ['f', 'g', 'h', 'i', 'j']
```

### CONCAT

- The `concat()` is used to `merge` two or more `arrays`.

- This method `does not change` the `existing arrays`, but instead `returns a new array`

```js
const letters = arr.concat(arr2);
// Same as: console.log([...arr, ...arr2])
console.log(letters);
// ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j']
```

## JOIN

- The `join()` creates and returns a new string by `concatenating` all of the elements in this `array`, separated by `commas` or a `specified separator string`.

- If the `array` has only one `item`, then that `item` will be `returned without` using the `separator`.

```js
console.log(letters.join("-"));
// a-b-c-d-e-f-g-h-i-j
```
