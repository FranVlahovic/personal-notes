## String Methods Practice

### Expected Result

```
 🔴 Delayed Departure from FAO to TXL (11h25)
              Arrival from BRU to FAO (11h45)
   🔴 Delayed Arrival from HEL to FAO (12h05)
            Departure from FAO to LIS (12h30)
```

```js
const flights =
  "_Delayed_Departure;fao93766109;txl2133758440;11:25+_Arrival;bru0943384722;fao93766109;11:45+_Delayed_Arrival;hel7439299980;fao93766109;12:05+_Departure;fao93766109;lis2323639855;12:30";

const getCode = (str) => str.slice(0, 3).toUpperCase();

for (const flight of flights.split("+")) {
  console.log(flight);
  // "_Delayed_Departure;fao93766109 txl2133758440;11:25"

  const [type, from, to, time] = flight.split(";");
  console.log(type, from, to, time);
  // "_Delayed_Departure" "fao93766109" "txl2133758440" "11:25"

  const output = `${type.startsWith("_Delayed") ? "🔴" : ""}${type.replaceAll(
    "_",
    " "
  )} ${getCode(from)} ${getCode(to)} (${time.replace(":", "h")})`.padStart(36);
  console.log(output);
}
```

- We `loop` over `flights` array made from values seperated by `'+'`
- We `split` `flight` value into array seperated by `';'`
- We deconstruct values into `type` `from` `to` `time` variables
- Output value:
  - If value from `type` `startsWitch` `_Delayed'` add `'🔴'`
  - Replace all `'_'` value from `type` to `' '`
  - We make `getCode` function to `slice` value to make it be `3 char` and `toUpperCase`
  - We put `from` and `to` values into `getCode` function
  - We replace `:` with `h` in `time` value
  - We put whitespace `padding` on the beginning with `padStart`

#### Console Logs

```js
console.log(flight);
// "_Delayed_Departure;fao93766109 txl2133758440;11:25"

const [type, from, to, time] = flight.split(";");
console.log(type, from, to, time);
// Logs: "_Delayed_Departure" "fao93766109" "txl2133758440" "11:25", "_Arrival" "bru0943384722" "fao93766109" "11:45", "_Delayed_Arrival" "hel7439299980" "fao93766109" "12:05", "_Departure" "fao93766109" "lis2323639855" "12:30"

console.log(type.startsWith("_Delayed") ? "🔴" : "");
// Logs: "🔴", "", "🔴", ""

console.log(type.replaceAll("_", " "));
// Logs: "Delayed Departure", "Arrival", "Delayed Arrival", "Departure"

console.log(getCode(from));
// Logs: "FAO", "BRU", "HEL", "FAO"

console.log(getCode(to));
// Logs: "TXL", "FAO", "FAO", "LIS"

console.log(time.replace(":", "h"));
// Logs: "11h25", "11h45", "12h05", "12h30"
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
