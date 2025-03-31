## Closures

- `Closure` is a function that remembers the variables from its lexical scope, even after the `outer function` has `finished executing`. This allows the `inner function` to `access and modify` those `variables`.

```js
const secureBooking = function () {
  let passengerCount = 0;

  return function () {
    passengerCount++;
    console.log(`${passengerCount} passengers`);
  };
};

const booker = secureBooking();

booker();
booker();
booker();

console.dir(booker);
```

- `secureBooking` creates `passengerCount` and returns an `inner function`.

- Even though `secureBooking` has already finished executing, the inner function still has access to `passengerCount` because of closures.

- Calling `booker()` increments `passengerCount`, and the `updated value` is `remembered` across calls.

### Coding Challenge #2

#### Take the IIFE below and at the end of the function, attach an event listener that changes the color of the selected h1 element ('header') to blue, each time the BODY element is clicked. Do NOT select the h1 element again!

```js
(function () {
  const header = document.querySelector("h1");
  header.style.color = "red";

  document.querySelector("body").addEventListener("click", function () {
    header.style.color = "blue";
  });
})();
```

- The function is an `Immediately Invoked Function Expression (IIFE)`, meaning it `runs immediately` after it's `defined`.

- The `header` variable is inside the `IIFE`, but the `event listener` still has `access` to it due to `closures`.

- When `clicking` the `body`, the `event listener` changes `header.style.color` to "`blue`", even though `header` was `declared` inside the `IIFE`.
