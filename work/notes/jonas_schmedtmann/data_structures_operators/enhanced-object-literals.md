## Enhanced Object Literals

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

  openingHours,

  order(starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
  },

  orderDelivery({ starterIndex, mainIndex, time, address }) {
    console.log(
      `Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`
    );
    // Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
  },

  orderPasta(ing1, ing2, ing3) {
    console.log(
      `Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`
    );
  },

  orderPizza(ingredient1, ...otherIngredients) {
    console.log(ingredient1);
    console.log(otherIngredients);
  },
};
```

</details>

### 1. ES6 Enchancement

#### Before

```js
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
```

#### After

> We use openingHours directly

```js
openingHours,
```

> openingHours should be defined as an object elsewhere in the code:
>
> ```js
> const openingHours = {
>    thu: {
>      open: 12,
>      close: 22,
>    },
>    fri: {
>      open: 11,
>      close: 23,
>    },
>    sat: {
>      open: 0, // Open 24 hours
>      close: 24,
>    },
> };
> const restaurant = {
> 	name: 'Classico Italiano',
> 	location: 'Via Angelo Tavanti 23, Firenze, Italy',
> 	categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
> 	starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad'],
> 	mainMenu: ['Pizza', 'Pasta', 'Risotto'],
>
> ```

### 2. ES6 Enhanced Method Syntax

#### Before

```js
order: function(starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
},

orderDelivery: function({ starterIndex, mainIndex, time, address }){
    console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`);
    // Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
},
```

#### After

> Using ES6 method shorthand for cleaner, modern syntax.

```js
order(starterIndex, mainIndex) {
		return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
},

orderDelivery({ starterIndex, mainIndex, time, address }){
    console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`);
    // Order received! Garlic Bread and Risotto will be delivered to Via del Sole, 21 at 22:30
},

orderPasta(ing1, ing2, ing3){
    console.log(`Here is your delicious pasta with ${ing1}, ${ing2} and ${ing3}`)
},

orderPizza(ingredient1, ...otherIngredients){
    console.log(ingredient1);
    console.log(otherIngredients);
},
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
