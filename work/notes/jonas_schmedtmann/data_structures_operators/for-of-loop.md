## For..Of Loop

<details>
<summary style="font-size: 1.2em;font-weight: bold;"> Expand Example Code</summary>

```js
"use strict";

const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],

  openingHours: {
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
  },
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

const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];

for (const item of menu) {
  console.log(item); // Focaccia Bruschetta Garlic Bread Caprese Salad Pizza Pasta Risotto
}

for (const [i, el] of menu.entries()) {
  console.log(`${i + 1}) ${el}`); // 1) Focaccia 2) Bruschetta 3) Garlic Bread...
}
```

</details>

### Basic for of loop

> Iterates over each element in the `menu` array

> `item` represent the current element in the iteration

```js
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];
// ["Focaccia" "Bruschetta" "Garlic" "Bread" "Caprese Salad" "Pizza" "Pasta ""Risotto"]

for (const item of menu) {
  console.log(item); // Focaccia Bruschetta Garlic Bread Caprese Salad Pizza Pasta Risotto
}
```

### Menu Entries (Array.entries)

> `menu.entries()` returns an iterable of `[index, element]` pairs.

> Using destructuring `[i, el]`, we extract the index `i` and the element `el` from each pair.

```js
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];
// ["Focaccia" "Bruschetta" "Garlic" "Bread" "Caprese Salad" "Pizza" "Pasta ""Risotto"]

for (const [i, el] of menu.entries()) {
  console.log(`${i + 1}) ${el}`); // 1) Focaccia 2) Bruschetta 3) Garlic Bread...
}
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
