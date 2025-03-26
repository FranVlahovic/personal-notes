## Strings

### Split and join

```js
console.log("a+very+nice+string".split("+")); // ["a", "very", "nice", "string"]
console.log("Jonas Schmedtmann".split(" ")); // ["jonas", "schmedtmann]
```

- Extracts values from `string` by a parameter and puts it into an `array`.

```js
const [firstName, lastName] = "Jonas Schmedtmann".split(" ");
```

- Puts values into `firstName` and `lastName` from array made by split.

```js
const newName = ["Mr.", firstName, lastName.toUpperCase()].join(" ");
console.log(newName);
```

- We capitalized `lastName` value and then joined all values with `join` from `array` separated by `" "`

```js
const capitalizeName = function (name) {
  const names = name.split(" ");
  const namesUpper = [];

  for (const n of names) {
    // namesUpper.push(n[0].toUpperCase() + n.slice(1));
    namesUpper.push(n.replace(n[0], n[0].toUpperCase()));
  }
  console.log(namesUpper.join(" "));
};

capitalizeName("jessica ann smith davis");
capitalizeName("jonas schmedtmann");
```

- We `extracted` values into `names`
- We `looped` over given `array`
- We `replaced` first letter of a value with `toUpperCase` of that letter
- We `pushed` values into array `namesUpper`.
- We `joined` values separated by `" "`

### Padding

```js
const message = "Go to gate 23!";
console.log(message.padStart(20, "+").padEnd(30, "+"));
console.log("Jonas".padStart(20, "+").padEnd(30, "+"));
```

- We check if `string` is at least `20` characters long. If the `string` is `shorter`, it pads the beginning of the `string` with `+` characters until the `string` reaches the specified length.

```js
const maskCreditCard = function (number) {
  const str = number + "";
  const last = str.slice(-4);
  return last.padStart(str.length, "*");
};

console.log(maskCreditCard(64637836));
console.log(maskCreditCard(43378463864647384));
console.log(maskCreditCard("334859493847755774747"));
```

### Repeat

```js
const message2 = "Bad waether... All Departues Delayed... ";
console.log(message2.repeat(5));
```

- Repeats the `message` variable `5` times

```js
const planesInLine = function (n) {
  console.log(`There are ${n} planes in line ${"🛩".repeat(n)}`);
};
planesInLine(5);
planesInLine(3);
planesInLine(12);
```

- Repeats `🛩` emoji number of times that we specified.
