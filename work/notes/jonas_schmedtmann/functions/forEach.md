## forEach Loop

- The `forEach()` executes a provided `function` once for each `array element`.

```js
const movementsFor = [200, 450, -400, 3000, -650, -130, 70, 1300];
```

### Using for..Of

```js
for (const movement of movementsFor) {
  if (movement > 0) {
    console.log(`You deposited ${movement}`);
  } else {
    console.log(`You withdrew ${Math.abs(movement)}`);
  }
  // You deposited 200
  // You deposited 450
  // You withdrew 400
  // You deposited 3000
  // You withdrew 650
  // You withdrew 130
  // You deposited 70
  // You deposited 1300
}
```

### Using forEach

```js
movementsFor.forEach((movement) => {
  if (movement > 0) {
    console.log(`You deposited ${movement}`);
  } else {
    console.log(`You withdrew ${Math.abs(movement)}`);
  }

  // You deposited 200
  // You deposited 450
  // You withdrew 400
  // You deposited 3000
  // You withdrew 650
  // You withdrew 130
  // You deposited 70
  // You deposited 1300
});
```

```js
movementsFor.forEach((mov, i, arr) => {
  if (mov > 0) {
    console.log(`Movement ${i + 1}: You deposited ${mov}`);
  } else {
    console.log(`Movement ${i + 1}: You withdrew ${Math.abs(mov)}`);
  }

  // Movement 1: You deposited 200
  // Movement 2: You deposited 450
  // Movement 3: You withdrew 400
  // Movement 4: You deposited 3000
  // Movement 5: You withdrew 650
  // Movement 6: You withdrew 130
  // Movement 7: You deposited 70
  // Movement 8: You deposited 1300
});
```

- `mov` : The `current element` being processed in the array.

- `i` : The `index` of the `current element` being processed in the array.

- `arr` : The `array` forEach() was called upon.

> Simmilar to `(const [i, movement] of movements.entries())`
