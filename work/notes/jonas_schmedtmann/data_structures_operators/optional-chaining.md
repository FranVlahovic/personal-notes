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

if (restaurant.openingHours && restaurant.openingHours.mon) {
  console.log(restaurant.openingHours.mon.open);
}

// WITH OPTIONAL CHAINING
console.log(restaurant.openingHours.mon?.open); // undefined
console.log(restaurant.openingHours?.mon?.open); // undefined

// Example
const days = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"];
for (const day of days) {
  const open = restaurant.openingHours[day]?.open ?? "closed";
  console.log(`on ${day} we open at ${open}`);
  // on mon we open at closed on tue we open at closed on wed we open at closed on thu we open at 12 on fri we open at 11 on sat we open at 0 on sun we open at closed
}

// METHODS
console.log(restaurant.order?.(0, 1) ?? "Method does not exist"); // [ 'Focaccia', 'Pasta' ]
console.log(restaurant.orderRisotto?.(0, 1) ?? "Method does not exist"); // Method does not exist

//ARRAYS
const users = [{ name: "Jonas", email: "hello@gmail.com" }];

console.log(users[0]?.name ?? "User array empty"); // Jonas (if array is empty than 'User array empty')

// Same as above but much longer
if (users.length > 0) {
  console.log(users[0].name);
} else {
  console.log("User array empty");
}
```
