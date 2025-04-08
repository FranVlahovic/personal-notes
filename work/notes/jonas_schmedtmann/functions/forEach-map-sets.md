## forEach Maps & Sets

### Map

```js
const currenciesFor = new Map([
  ["USD", "United States dollar"],
  ["EUR", "Euro"],
  ["GBP", "Pound sterling"],
]);

currenciesFor.forEach((value, key, map) => {
  console.log(`${key}: ${value}`);
});
```

### Set

```js
const currenciesUnique = new Set(["USD", "GBP", "USD", "EUR", "EUR"]);
console.log(currenciesUnique);
// {'USD', 'GBP', 'EUR'}
currenciesUnique.forEach((value, _, map) => {
  console.log(`${_}: ${value}`);
});
```
