## Destructuring Arrays

```js
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],

  order: function (starterIndex, mainIndex) {
    return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]];
  },
};
const arr = [2, 3, 4];
const [x, y, z] = arr;

console.log(x, y, z); // 2 3 4
console.log(arr); // [2, 3, 4]

let [main, , secondary] = restaurant.categories;
console.log(main, secondary); // Italian Vegetarian

[main, secondary] = [secondary, main];
console.log(main, secondary); // Vegetarian Italian

// Destructuring Way (Receive 2 return values from a function)
const [starter, mainCourse] = restaurant.order(2, 0);
console.log(starter, mainCourse); // Garlic Bread Pizza

// Nested Destructuring
const nested = [2, 4, [5, 6]];

// const [i, , j] = nested;
// console.log(i, j); // 2 [5, 6]

const [i, , [j, k]] = nested;
console.log(i, j, k); // 2 5 6

// Default Values
const [p = 1, q = 1, r = 1] = [8, 9];
console.log(p, q, r); // 8 9 1
```

### Assignment Destructuring Arrays

> Destructure the `books` array into two variables called `firstBook` and `secondBook`

```js
const [firstBook, secondBook] = books;
```

---

> Destructure the `books` array into a variable called `thirdBook`. You must skip the first two books

```js
const [, , thirdBook] = books;
```

---

> Below is the nested `ratings` array that contains two other arrays. Destructure the nested `ratings` arrays into two variables called `rating` and `ratingsCount`. In the result of your destructuring, the `ratings` variable should store a number 4.19, and the `ratingsCount` variable should store a number 144584.
> `const ratings =  [['rating',  4.19],  ['ratingsCount',  144584]];`

```js
const [[, rating], [, ratingsCount]] = ratings;
```

---

> Below is the `ratingStars` array. Destructure it into three variables called `fiveStarRatings`, `oneStarRatings` and `threeStarRatings`. Assign the `threeStarRatings` variable with a default value of 0.
> `const ratingStars = [63405, 1808];`

```js
const [fiveStarRatings, oneStarRatings, threeStarRatings = 0] = ratingStars;
console.log(ratingStars); // 63405 1808 0
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
