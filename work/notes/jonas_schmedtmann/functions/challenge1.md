## Coding Challenge #1

> > TEST DATA 1: Julia's data [3, 5, 2, 12, 7], Kate's data [4, 1, 15, 8, 3]

> > TEST DATA 2: Julia's data [9, 16, 6, 8, 3], Kate's data [10, 5, 6, 1, 4]

```js
const checkDogs = function (dogsJulia, dogsKate) {
  const dogsJuliaCorrected = dogsJulia.slice();
  console.log(dogsJuliaCorrected);
  // [ 3, 5, 2, 12, 7 ]

  dogsJuliaCorrected.splice(0, 1);
  dogsJuliaCorrected.splice(-2);

  console.log(dogsJuliaCorrected); // [ 5, 2 ]

  const dogs = [...dogsJuliaCorrected, ...dogsKate];

  console.log(dogs); // [ 5, 2, 4, 1, 15, 8, 3]

  dogs.forEach((dog, i) => {
    if (dog >= 3) {
      console.log(`Dog number ${i + 1} is an adult, and is ${dog} years old.`);
    } else {
      console.log(`Dog number ${i + 1} is still a puppy`);
    }
  });
};

checkDogs([3, 5, 2, 12, 7], [4, 1, 15, 8, 3]);
```

### 1. Julia found out that the owners of the FIRST and the LAST TWO dogs actually have cats, not dogs! So create a `shallow copy` of Julia's `array`, and `remove` the cat `ages` from that copied `array` (because it's a bad practice to mutate function parameters)

```js
const dogsJuliaCorrected = dogsJulia.slice();
console.log(dogsJuliaCorrected);
// [ 3, 5, 2, 12, 7 ]

dogsJuliaCorrected.splice(0, 1);
dogsJuliaCorrected.splice(-2);
```

### 2. Create an `array` with both `Julia`'s (corrected) and `Kate`'s `data`

````js
const dogs = [...dogsJuliaCorrected, ...dogsKate];```
````

### 3. For each remaining dog, log to the console whether it's an adult ("Dog number 1 is an adult, and is 5 years old") or a puppy ("Dog number 2 is still a puppy 🐶")

```js
dogs.forEach((dog, i) => {
  if (dog >= 3) {
    console.log(`Dog number ${i + 1} is an adult, and is ${dog} years old.`);
  } else {
    console.log(`Dog number ${i + 1} is still a puppy`);
  }
});
```
