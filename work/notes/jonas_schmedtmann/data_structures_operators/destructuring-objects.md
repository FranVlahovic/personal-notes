## Destructuring Objects

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
};

restaurant.orderDelivery({ time: '22:30', address: 'Via del Sole, 21', mainIndex: 2, starterIndex: 2 });

const { name, openingHours, categories } = restaurant;
console.log(name, openingHours, categories); // Classico Italiano {thu: .., fri: ..} ["italian", "pizzeria",...]

const { name: restaurantName, openingHours: hours, categories: tags } = restaurant;
console.log(restaurantName, hours, tags) // Classico Italiano {thu: .., fri: ..} ["italian", "pizzeria",...]

// Default values
const { menu = [], starterMenu: starters = [] } = restaurant;
console.log(menu, starters); // [] ["Focaccia", "Bruschetta"...]

// Mutating variables
let a = 111;
let b = 888;
const obj = { a: 23, b: 7, c:14 };
({ a, b } = obj);
console.log(a, b) // 23 7

// Nested objects
const { fri: { open, close } } = openingHours;
console.log(open, close); // 11 23
```

</details>

### Basic Destructuring

> Extracting properties from objects into variables.

```js
const { name, openingHours, categories } = restaurant;

console.log(name, openingHours, categories);
```

> Equivalent to:
>
> ```js
> const name = restaurant.name;
> const openingHours = restaurant.openingHours;
> const categories = restaurant.categories;
> ```

### Renaming Variables

> Assign new variable names while destructuring.

```js
const {
  name: restaurantName,
  openingHours: hours,
  categories: tags,
} = restaurant;

console.log(restaurantName, hours, tags);
```

### Default Values

> Assign default values to avoid `undefined`.

```js
const { menu = [], starterMenu: starters = [] } = restaurant;

console.log(menu, starters); // [] ["Focaccia", "Bruschetta", ...]
```

### Mutating Variables

> Updating existing variables using destructuring.

```js
let a = 111;

let b = 888;

const obj = { a: 23, b: 7, c: 14 };

({ a, b } = obj);

console.log(a, b); // 23 7
```

### Nested Destructuring

> Extracting values from nested objects.

```js
const {
  fri: { open, close },
} = restaurant.openingHours;

console.log(open, close); // 11 23
```

### Function Parameter Destructuring

> Passing an object as a function parameter and destructuring it.

```js
restaurant.orderDelivery({
  time: "22:30",
  address: "Via del Sole, 21",
  mainIndex: 2,
  starterIndex: 2,
});
```

> Logs.

```js
console.log(
  `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
); // Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
