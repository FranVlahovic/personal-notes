## Regular Functions || Arrow Functions

- Don't use `arrow functions` as a `method`.

- Use `arrow functions` inside object `method`.

- An `arrow function` inherits `this` keyword from parents scope.

```JavaScript
const jonas = {
  firstName: 'Jonas',
  year: 1991,
  calcAge: function () {
    console.log(this); // 'this' == 'jonas'
    console.log(2037 - this.year);

    const isMillenial = () => {
      console.log(this); // 'this' == 'jonas'
      console.log(this.year >= 1981 && this.year <= 1996);
    };
    isMillenial();
  },
  // Arrow Function as method.
  greet: () => {
    console.log(this); // 'this' == global object
    console.log(`Hey ${this.firstName}`);
  },
};
jonas.greet(); // 'Hey undefined'
jonas.calcAge(); // 46, true


// Arguments keyword
// Regular Function
const addExpr = function (a, b) {
  console.log(arguments); // [2, 5]
  return a + b;
};
addExpr(2, 5); // logs: [2, 5]

// Arrow Function
var addArrow = (a, b) => {
  console.log(arguments);
  return a + b;
};
addArrow(2, 5, 8);
```
