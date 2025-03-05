## Rest Pattern & Parameters

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

    orderPizza: function(ingredient1, ...otherIngredients){
        console.log(ingredient1);
        console.log(otherIngredients);
    }
};

// Spread beacuse on RIGHT side of '='
const arr = [1, 2, ...[3, 4]];

// Rest beacuse on LEFT side of '='
const [a, b, ...others] = [1, 2, 3, 4, 5];
console.log(a, b, others); // 1 2 [3, 4, 5];

const [pizza, , risotto, ...otherFood] = [...restaurant.mainMenu, ...restaurant.starterMenu,];
console.log(pizza, risotto, otherFood); // Pizza Risotto ["Focaccia", "bruschetta", "garlic", "salad"]

// Objects
const { sat, ...weekdays } = restaurant.openingHours;
console.log(weekdays); // {thu: {}, fri: {}

// Functions
const add = function(...numbers){
    let sum = 0;
    for (let i = 0; i<numbers.length; i+=1){
        numbers[i];
        console.log(sum);
    }
}
add(2, 3);
add(5, 3, 7, 2);
add(8, 2, 5, 3, 2, 1, 4);

const x = [23, 5, 7];
add(...x);

restaurant.orderPizza('mushrooms', 'onion', 'olives', 'spinach');
//    orderPizza: function(ingredient1, ...otherIngredients){
//        console.log(ingredient1); // mushrooms
//        console.log(otherIngredients); ["onion", "olives", "spinach"]
//    }

```

</details>
