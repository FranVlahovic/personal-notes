## Looping Objects

<details>
<summary style="font-size: 1.2em;font-weight: bold;"> Expand Example Code</summary>

```js
"use strict";
const openingHours = {
  thu: {
    open: 12,
    close: 22,
  },
  fri: {
    open: 11,
    close: 23,
  },
  sat: {
    open: 0, // Open 24 hours
    close: 24,
  },
};

const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],

  order: function (starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
  },

  orderDelivery: function ({ starterIndex, mainIndex, time, address }) {
    console.log(
      `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
    );
    // Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
  },

  orderPasta: function (ing1, ing2, ing3) {
    console.log(
      `Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`
    );
  },

  orderPizza: function (ingredient1, ...otherIngredients) {
    console.log(ingredient1);
    console.log(otherIngredients);
  },
};
```

</details>

### Property Names

```js
const properties = Object.keys(openingHours);
console.log(properties); // [ 'thu', 'fri', 'sat' ]

let openStr = `We are open on ${properties.length} days: `;
for (const day of properties) {
  openStr += `${day}, `;
}
console.log(openStr); // We are open on 3 days: thu, fri, sat,
```

- We retrive property names (keys) of an object and return them as an array `properties` by using `Object.keys(openingHours)`
- We use `for..of` loop to loop over `properties` array and concatenate the string `openStr`

### Property VALUES

```js
const values = Object.values(openingHours);
console.log(values); // [{ open: 12, close: 22 },{ open: 11, close: 23 },{ open: 0, close: 24 }]
```

- We extract values from `openingHours` object properties and return them as an array

### Entire object

```js
const entries = Object.entries(openingHours);
console.log(entries); // [['thu', { open: 12, close: 22 } ],[ 'fri', { open: 11, close: 23 } ],[ 'sat', { open: 0, close: 24 }]]

for (const x of entries) {
  console.log(x); // [ 'thu', { open: 12, close: 22 } ] [ 'fri', { open: 11, close: 23 } ] [ 'sat', { open: 0, close: 24 } ]
}
```

- We convert an object `openingHours` into an array of key-value pairs

### [key, value]

```js
for (const [key, { open, close }] of entries) {
  console.log(`On ${key} we open at ${open} and close at ${close}`); // On thu we open at 12 and close at 22 On fri we open at 11 and close at 23 On sat we open at 0 and close at 24
}
```

- We loop over an `entries` array of key-value pairs and we destructure each key-value pair
- `key` represents the property name (e.g., "thu"), and `{ open, close }` destructures the object value to access specific properties (`open` and `close`).

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
