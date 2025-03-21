## New Operations for Sets

```js
'use strict';
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
	name: 'Classico Italiano',
	location: 'Via Angelo Tavanti 23, Firenze, Italy',
	categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
	starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
	mainMenu: ['Pizza', 'Pasta', 'Risotto'],


	order: function(starterIndex, mainIndex) {
		return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
	},

	orderDelivery: function({ starterIndex, mainIndex, time, address }){
	console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`);
	// Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
	},

	orderPasta: function(ing1, ing2, ing3){
		console.log(`Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`)
	},

    orderPizza: function(ingredient1, ...otherIngredients){
        console.log(ingredient1);
        console.log(otherIngredients);
    },

    const italianFoods = new Set(['pasta', 'gnocchi', 'tomatoes', 'olive oil', 'garlic', 'basil']);

    const mexicanFoods = new Set(['tortillas', 'beans', 'rice', 'tomatoes', 'avocado', 'garlic']);
};
```

### New Methods that are introduced in ES2025

### Intersection

- Extracts duplicates from `set`

```js
const commonFoods = italianFoods.intersection(mexicanFoods);
console.log("Intersection: ", commonFoods); // Intersection:  Set(2) { 'tomatoes', 'garlic' }
console.log([...commonFoods]); // [ 'tomatoes', 'garlic' ]
```

### Union

- Unite 2 sets but without duplicates

```js
const italianMexicanFusion = italianFoods.union(mexicanFoods);
console.log("Union:", italianMexicanFusion); // Union: Set(10) {'pasta', 'gnocchi', 'tomatoes', 'olive oil', 'garlic', 'basil', 'tortillas', 'beans', 'rice', 'avocado'}
```

### Difference

- Extracts element which are unique from `first set`

```js
const uniqueItalian = italianFoods.difference(mexicanFoods);
console.log("Difference italian:", uniqueItalian); // Difference italian: Set(4) { 'pasta', 'gnocchi', 'olive oil', 'basil' }
```

### SymmetricDifference

- Extracts unique elements from both sets, but doesnt include duplicates

```js
const uniqueItalianAndMexicanFoods =
  italianFoods.symmetricDifference(mexicanFoods);
console.log(uniqueItalianAndMexicanFoods); // Set(8) {'pasta', 'gnocchi', 'olive oil', 'basil', 'tortillas', 'beans', 'rice', 'avocado'};
```

### isDisjointFrom

- Check whether sets `!duplicates`

```js
console.log(italianFoods.isDisjointFrom(mexicanFoods));
```
