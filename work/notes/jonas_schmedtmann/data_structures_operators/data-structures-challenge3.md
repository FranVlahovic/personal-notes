## Challenge #3 (Maps)

```js
const gameEvents = new Map([
  [17, "⚽️ GOAL"],
  [36, "🔁 Substitution"],
  [47, "⚽️ GOAL"],
  [61, "🔁 Substitution"],
  [64, "🔶 Yellow card"],
  [69, "🔴 Red card"],
  [70, "🔁 Substitution"],
  [72, "🔁 Substitution"],
  [76, "⚽️ GOAL"],
  [80, "⚽️ GOAL"],
  [92, "🔶 Yellow card"],
]);

// 1. Create an array 'events' of the different game events that happened (no duplicates)
const events = [...new Set(gameEvents.values())];
console.log(events);

// - unpack Set with spread operator (...)

// 2. After the game has finished, is was found that the yellow card from minute 64 was unfair. So remove this event from the game events log.
gameEvents.delete(64);

// 3. Print the following string to the console: "An event happened, on average, every 9 minutes" (keep in mind that a game has 90 minutes)
console.log(
  `An event happened, on average, every ${90 / gameEvents.size} minutes`
);

// 4. Loop over the events and log them to the console, marking whether it's in the first half or second half (after 45 min) of the game, like this:
for (const [min, event] of gameEvents) {
  const half = min <= 45 ? "FIRST" : "SECOND";
  console.log(`[${half} HALF] ${min}: ${event}`);
}
```

### 1. Create an array 'events' of the different game events that happened (no duplicates)

```js
const events = [...new Set(gameEvents.values())];
console.log(events); // [ '⚽️ GOAL', '🔁 Substitution', '🔶 Yellow card', '🔴 Red card' ]
```

- we use `Set` on `gameEvents.values()` in order to remove duplicates
- we put it in array in order to get array from it
- unpack `Set` with spread operator (`...`)

### 2. After the game has finished, is was found that the yellow card from minute 64 was unfair. So remove this event from the game events log.

```js
gameEvents.delete(64);
```

- we use `gameEvents.delete()` to remove the specified element from this map by key (`64`)

### 3. Print the following string to the console: "An event happened, on average, every 9 minutes" (keep in mind that a game has 90 minutes)

```js
console.log(
  `An event happened, on average, every ${90 / gameEvents.size} minutes`
);
```

- we use `gameEvents.size` in order to get the number of elements in a map
- we take the `90` minutes and divide it by number of elements

### 4. Loop over the events and log them to the console, marking whether it's in the first half or second half (after 45 min) of the game, like this:

```js
for (const [min, event] of gameEvents) {
  const half = min <= 45 ? "FIRST" : "SECOND";
  console.log(`[${half} HALF] ${min}: ${event}`);
}
```

- we use `for of` loop to extract key and value pair (`min, event`) from `gameEvents`
- we check what events are made in `first half`, and `second half`.
- we log `key`, `value` and `half`.

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
