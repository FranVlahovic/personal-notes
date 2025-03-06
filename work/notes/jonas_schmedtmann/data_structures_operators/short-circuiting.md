## Short Circuiting (&& amd ||)

<details>
<summary style="font-size: 1.2em;font-weight: bold;"> Expand Example Code</summary>

```js
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

// Spread beacuse on RIGHT side of '='
const arr = [1, 2, ...[3, 4]];

// Rest beacuse on LEFT side of '='
const [a, b, ...others] = [1, 2, 3, 4, 5];
console.log(a, b, others); // 1 2 [3, 4, 5];

const [pizza, , risotto, ...otherFood] = [
  ...restaurant.mainMenu,
  ...restaurant.starterMenu,
];
console.log(pizza, risotto, otherFood); // Pizza Risotto ["Focaccia", "bruschetta", "garlic", "salad"]

// Objects
const { sat, ...weekdays } = restaurant.openingHours;
console.log(weekdays); // {thu: {}, fri: {}

// Functions
const add = function (...numbers) {
  let sum = 0;
  for (let i = 0; i < numbers.length; i += 1) {
    numbers[i];
    console.log(sum);
  }
};
add(2, 3);
add(5, 3, 7, 2);
add(8, 2, 5, 3, 2, 1, 4);

const x = [23, 5, 7];
add(...x);

restaurant.orderPizza("mushrooms", "onion", "olives", "spinach");
//    orderPizza: function(ingredient1, ...otherIngredients){
//        console.log(ingredient1); // mushrooms
//        console.log(otherIngredients); ["onion", "olives", "spinach"]
//    }

// OR OPERATOR
// Short Circuiting

// The or operator returns the first truthy value among the operands, or the last operand if none are truthy. Used for implementing default values in real-life scenarios.
console.log(3 || "Jonas"); // 3
console.log("" || "Jonas"); // Jonas
console.log(true || 0); // true
console.log(undefined || null); // null
console.log(undefined || 0 || "Hello" || 23); // Hello

restaurant.numGuests = 23;
const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
console.log(guests1); // 23

const guests2 = restaurant.numGuests || 10;
console.log(guests2); // 23

// AND OPERATOR
// The and operator returns the first falsy value among the operands, or the last operand if all are truthy.

console.log(0 && "Jonas"); // 0
console.log(7 && "Jonas"); // Jonas

console.log("Hello" && 23 && null && "Jonas");

// Practical Example
// Often used to execute the second operand only if the first one is truthy.
if (restaurant.orderPizza) {
  restaurant.orderPizza("mushrooms", "spinach");
}

restaurant.orderPizza && restaurant.orderPizza("mushrooms", "spinach");
//    orderPizza: function(ingredient1, ...otherIngredients){
//        console.log(ingredient1); // mushrooms
//        console.log(otherIngredients); ["spinach"]
//    }
```

</details>

### OR Operator (||)

> The OR operator (`||`) returns the first **truthy** value it encounters.
> If all values are **falsy**, it returns the last operand.

> Useful for setting default values.

#### Examples:

```js
console.log(3 || "Jonas"); // 3

console.log("" || "Jonas"); // 'Jonas'

console.log(true || 0); // true

console.log(undefined || null); // null

console.log(undefined || 0 || "Hello" || 23); // 'Hello'
```

> If `restaurant.numGuests` exists, it will be assigned, otherwise it defaults to 10.

```js
restaurant.numGuests = 23;

const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
console.log(guests1); // 23

const guests2 = restaurant.numGuests || 10;
console.log(guests2); // 23
```

### AND Operator (&&)

> The AND operator (`&&`) returns the first **falsy** value it encounters.
> If all values are **truthy**, it returns the last operand.

> Commonly used for executing code only if a condition is met.

#### Examples:

```js
console.log(0 && "Jonas"); // 0

console.log(7 && "Jonas"); // 'Jonas'

console.log("Hello" && 23 && null && "Jonas"); // null
```

> If `orderPizza` exists, than execute `restaurant.orderPizza("mushrooms", "spinach")`

```js
if (restaurant.orderPizza) {
  restaurant.orderPizza("mushrooms", "spinach");
}

restaurant.orderPizza && restaurant.orderPizza("mushrooms", "spinach");
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
