## Challenge 4

### Write a program that receives a list of variable names written in underscore_case and convert them to camelCase.

- The input will come from a textarea inserted into the DOM (see code below), and conversion will happen when the button is pressed.

### THIS TEST DATA (pasted to textarea)

```
underscore_case
 first_name
Some_Variable
  calculate_AGE
delayed_departure
```

### SHOULD PRODUCE THIS OUTPUT (5 separate console.log outputs)

```
underscoreCase ✅
firstName ✅✅
someVariable ✅✅✅
calculateAge ✅✅✅✅
delayedDeparture ✅✅✅✅✅
```

```js
document.body.append(document.createElement("textarea"));
document.body.append(document.createElement("button"));

document.querySelector("button").addEventListener("click", () => {
  const text = document.querySelector("textarea").value;
  console.log(text);
  // "underscore_case
  //    first_name"
  const rows = text.split("\n");
  console.log(rows); // ["underscore_case"," first_name"]

  for (const [i, row] of rows.entries()) {
    console.log(i, row);
    // 1 " first_name"

    const [first, second] = row.toLowerCase().trim().split("_");
    console.log(first, second);
    // "first" "name"

    const output = `${first}${second.replace(
      second[0],
      second[0].toUpperCase()
    )}`;
    console.log(output);
    // "firstName"

    console.log(`${output.padEnd(20)}${"✅".repeat(i + 1)}`);
    // "firstName           ✅✅"
  }
});
```

- We take `values` from `textarea` input

- We take `values` and we split them into an array by next row `'\n'`

- We loop over `rows` array with `for of` loop extracting `key value` pair with `entries()`

- We take value in array `row` and we use `toLowerCase.trim().split("_")` to convert value into `lower case`, we `remove whitespace` and we `split` them into an `array` by `_`

- When we `split` values we put it into two variables `first` and `second`

- We put both values in `output` variable, but on `second` we `replace` `first letter` from `lowerCase` to `upperCase`

- We give our `output values` `padding` of `20` and `"✅"` for each value in array
