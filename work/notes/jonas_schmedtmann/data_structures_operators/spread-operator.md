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

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
