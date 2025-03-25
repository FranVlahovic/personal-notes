## Maps Fundamentals

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

```js
const rest = new Map();
rest.set("name", "Classico Italiano");
console.log(rest); // Map(1) { 'name' => 'Classico Italiano' }
```

- We use `set` method to add key value pair to the `Map`

```js
rest
  .set("categories", ["Italian", "Pizzeria", "Vegetarian", "Organic"])
  .set("open", 11)
  .set("close", 23)
  .set(true, "We open")
  .set(false, "We closed");
```

- We `set` `categories` key and value of an array
- We can chain `set` so we don't have to write each separately

```js
console.log(rest.get("name")); // Classico Italiano
console.log(rest.get(true)); // We open
```

- We use `get` to retrieve value from a `key`

```js
const time = 21;
console.log(rest.get(time > rest.get("open") && time < rest.get("close"))); // We open
```

- We check if an given `time` value is between `open` and `close` key
- We use `rest.get` to retrieve `true` or `false` value in order to get value from key value pair of (`.set(true, "We open").set(false, "We closed")`)

```js
console.log(rest.has("categories")); // true
```

- Checks if there is a `key` in a map that we ask for

```js
console.log(rest); // Map(6) {'name' => 'Classico Italiano','categories' => [ 'Italian', 'Pizzeria', 'Vegetarian', 'Organic' ],'open' => 11,'close' => 23,true => 'We open',false => 'We closed'}
console.log(rest.size); // 6
```

- We retrieve num of entries in a `Map`

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
