## Sets

- Not as useful as `arrays`

- Used when working with unique values

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
const ordersSet = new Set([
  "Pasta",
  "Pizza",
  "Pizza",
  "Risotto",
  "Pasta",
  "Pizza",
]);
console.log(ordersSet); // Set(3) { 'Pasta', 'Pizza', 'Risotto' }
```

- Searches through `array` and extracts `unique values` (without duplicates)

```js
console.log(new Set('Anna')); // Set(3) { 'A', 'n', 'a' }
console.log(new Set('Jonas)); // Set(5) { 'J', 'o', 'n', 'a', 's' }
```

- Splits strings into individual characters, duplicates are removed to create the set of unique values.

```js
console.log(ordersSet.size); // 3
```

- Similar as `array.length`, returns number of values inside the set

```js
console.log(ordersSet.has("Pizza")); // true
console.log(ordersSet.has("Gnocci")); // false
```

- Similar to `array.includes` it returns if value is inside the set or not.

```js
ordersSet.add("Garlic Bread");
console.log(ordersSet); // Set(4) { 'Pasta', 'Pizza', 'Risotto', 'Garlic Bread' }

ordersSet.delete("Risotto");
console.log(ordersSet); // Set(3) { 'Pasta', 'Pizza', 'Garlic Bread' }
```

- `set.add` adds an value to the set, `set.delete` deletes it

```js
for (const order of ordersSet) {
  console.log(order); // 'Pasta' 'Pizza' 'Garlic Bread'
}
```

- Loops through `ordersSet` set and extracts each unique value

### Example

```js
const staff = ["Waiter", "Chef", "Waiter", "Manager", "Chef", "Waiter"];
const staffUnique = [...new Set(staff)];
console.log(staffUnique); // ["Waiter", "Chef", "Manager"]
```

- We create an array named staff with repeated values
- We use Set constructor to filter out duplicate entries from the array
- We spread the `Set` with `...` into new `array` `staffUnique`
