## Spread Operator

<details>
<summary style="font-size: 1.2em;font-weight: bold;"> Expand Example Code</summary>

```js
const restaurant = {
	name: 'Classico Italiano',
	location: 'Via Angelo Tavanti 23, Firenze, Italy',
	categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
	starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
	mainMenu: ['Pizza', 'Pasta', 'Risotto'],

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
	order: function(starterIndex, mainIndex) {
		return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
	}

	orderDelivery: function({ starterIndex, mainIndex, time, address }){
	console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`);
	// Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
	}

	orderPasta: function(ing1, ing2, ing3){
		console.log(`Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`)
	}
};

const arr = [7, 8, 9];

const newArr = [1, 2, ...arr]
console.log(newArr); // [1, 2, 7, 8, 9]

console.log(...newArr); // 1, 2, 7, 8, 9

const newMenu = [...restaurant.mainMenu, 'Gnocci'];
console.log(newMenu); // ['Pizza', 'Pasta', 'Risotto', 'Gnocci']

// Copy Array
const mainMenuCopy = [...restaurant.mainMenu]; // ['Pizza', 'Pasta', 'Risotto', 'Gnocci']

// Join 2 Arrays
const menu = [...restaurant.starterMenu,...restaurant.mainMenu ];
console.log(menu); // ['Focaccia', 'Bruschetta', 'Garlic', 'Pizza', 'Pasta', 'Risotto', 'Gnocci']

// Iterables: arrays, strings, maps, sets, !Objects
const str = 'Jonas';
const letters = [...str, '', 'S.']
console.log(letters); // ['J','o','n','a','s','','S.']
console.log(str); // J o n a s

// Real World Example
const ingredients = [
	promt("Let's make pasta! Ingredient 1?"),
	promt('Ingredient 2?'),
	promt('Ingredient 3?'),
];
restaurant.orderPasta(...ingredients);
// orderPasta: function(ing1, ing2, ing3){
//		console.log(`Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`) // Here is your delicious pasta with {promt 1} etc.
//	}

// Objects
const newRestaurant = { foundedIn: 1998, ...restaurant, founder: 'Franco' };
console.log(newRestaurant); // {foundedIn: 1998, name: "Classico Italiano", location: ..., founder: "Franco"....}

const restaurantCopy = { ...restaurant };
restaurantCopy.location = 'Croatia';
console.log(restaurantCopy.location); // Croatia
console.log(restaurant.location); // Via Angelo Tavanti 23, Firenze, Italy
```

</details>

### Expanding an Array

> The spread operator allows us to unpack elements of an array and insert them into a new array.

```js
const arr = [7, 8, 9];

const newArr = [1, 2, ...arr];

console.log(newArr); // [1, 2, 7, 8, 9]

console.log(...newArr); // 1 2 7 8 9
```

> Expands an array into individual elements.\
> Useful for inserting values from one array into another.

### Copying an Array (Shallow Copy)

> The spread operator can be used to create a **copy** of an existing array.

```js
const mainMenu = ["Pizza", "Pasta", "Risotto"];

const mainMenuCopy = [...mainMenu];

console.log(mainMenuCopy); // ['Pizza', 'Pasta', 'Risotto']
```

> Creates a **shallow copy** (changes in the copy do not affect the original).\
> A faster alternative to `.slice()`.

### Merging Arrays

> The spread operator makes it easy to **combine two or more arrays**.

```js
const starterMenu = ["Focaccia", "Bruschetta", "Garlic Bread"];

const mainMenu = ["Pizza", "Pasta", "Risotto"];

const menu = [...starterMenu, ...mainMenu];

console.log(menu);
// ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Pizza', 'Pasta', 'Risotto']
```

> Works similarly to `concat()` but is more flexible and readable.\
> Can be used with **more than two arrays**.

### Using Spread with Strings

> Since **strings are iterable**, we can use the spread operator to **split characters** into an array.

```js
const str = "Jonas";

const letters = [...str, "", "S."];

console.log(letters); // ['J', 'o', 'n', 'a', 's', '', 'S.']

console.log(...str); // J o n a s
```

> Each character is spread as an **individual element** in an array.\
> Useful for string manipulation.

### Using Spread in Function Calls

> We can use the spread operator to **pass array elements as arguments** to functions.

```js
const restaurant = {
  orderPasta: function (ing1, ing2, ing3) {
    console.log(
      `Here is your delicious pasta with ${ing1}, ${ing2}, and ${ing3}`
    );
  },
};

const ingredients = [
  prompt("Let's make pasta! Ingredient 1?"),
  prompt("Ingredient 2?"),
  prompt("Ingredient 3?"),
];

restaurant.orderPasta(...ingredients);
```

> Spread **expands an array** into individual function arguments.\
> Eliminates the need for manually passing elements.

### Using Spread with Objects

> The spread operator can be used to **copy objects** or **merge properties**.

```js
const restaurant = {
  name: "Classico Italiano",
  location: "Italy",
  categories: ["Italian", "Pizzeria"],
};

const restaurantCopy = { ...restaurant };

restaurantCopy.location = "Croatia";

console.log(restaurantCopy.location); // Croatia

console.log(restaurant.location); // Italy
```

> Works similarly to `Object.assign()`.\
> **Shallow copy** – only copies the first level of properties.\
> **Cannot spread nested objects deeply**.

### Adding New Properties while Copying Objects

> We can **extend** an object by adding new properties while copying it.

```js
const newRestaurant = { foundedIn: 1998, ...restaurant, founder: "Franco" };
console.log(newRestaurant);
// { foundedIn: 1998, name: "Classico Italiano", location: "Italy", categories: [...], founder: "Franco" }
```

> New properties can be added **before or after** spreading.
> The last property with the **same key** will overwrite previous values.

### Differences Between Spread and Rest

> Even though both use the `...` syntax, they serve **different purposes**.

| Feature      | Spread (`...`)                      | Rest (`...`)                             |
| ------------ | ----------------------------------- | ---------------------------------------- |
| **Use case** | Expands elements                    | Gathers elements                         |
| **Used in**  | Arrays, objects, function arguments | Function parameters, array destructuring |
| **Example**  | `const arr2 = [...arr1, 5, 6]`      | `function sum(...numbers) {}`            |

```js
// Spread: Expanding elements
const arr1 = [1, 2, 3];
const arr2 = [...arr1, 4, 5];
console.log(arr2); // [1, 2, 3, 4, 5]

// Rest: Collecting elements
const sum = (...numbers) => {
  return numbers.reduce((acc, num) => acc + num, 0);
};
console.log(sum(1, 2, 3, 4, 5)); // 15
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
