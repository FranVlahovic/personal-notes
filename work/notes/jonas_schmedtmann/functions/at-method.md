## At Method

### AT

- The `at()` takes an `integer value` and returns the item at that `index`, allowing for `positive` and `negative integers`.

- `Negative integers` count back from the `last item` in the `array`.

```js
const arrAt = [23, 11, 64];
console.log(arrAt.at(0)); // 23
```

#### Getting last array element

```js
console.log(arrAt[arrAt.length - 1]);
// 64
console.log(arrAt.slice(-1)[0]);
// 64
console.log(arrAt.at(-1));
// 64
```

#### We can use same for strings

```js
console.log("jonas".at(0));
// j
console.log("jonas".at(-1));
// s
```
