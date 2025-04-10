## Data Structures Challenge #2

```js
// Challenge 2
const game = {
  team1: "Bayern Munich",
  team2: "Borrussia Dortmund",
  players: [
    [
      "Neuer",
      "Pavard",
      "Martinez",
      "Alaba",
      "Davies",
      "Kimmich",
      "Goretzka",
      "Coman",
      "Muller",
      "Gnarby",
      "Lewandowski",
    ],
    [
      "Burki",
      "Schulz",
      "Hummels",
      "Akanji",
      "Hakimi",
      "Weigl",
      "Witsel",
      "Hazard",
      "Brandt",
      "Sancho",
      "Gotze",
    ],
  ],
  score: "4:0",
  scored: ["Lewandowski", "Gnarby", "Lewandowski", "Hummels"],
  date: "Nov 9th, 2037",
  odds: {
    team1: 1.33,
    x: 3.25,
    team2: 6.5,
  },
};
```

### 1. Loop over the game.scored array and print each player name to the console, along with the goal number (Example: "Goal 1: Lewandowski")

```js
for (const [i, player] of game.scored.entries()) {
  console.log(`Goal ${i + 1}: ${player}`);
  // Goal 1: Lewandowski
  // Goal 2: Gnarby
  // Goal 3: Lewandowski
  // Goal 4: Hummels
}
```

- Loops through an array and returns iterator that contains `index value` pairs

### 2. Use a loop to calculate the average odd and log it to the console (We already studied how to calculate averages, you can go check if you don't remember)

```js
const odds = Object.values(game.odds);
let average = 0;
for (const odd of odds) {
  average += odd;
}
average /= odds.length;
console.log(average); // 3.6933333333333334
```

- We extract values from `game.odds` object properties and return them as an array
- Then to calculate `average` we loop over array to concatenate average sum, than it gets divided by `odds.length`

### 3. Print the 3 odds to the console, but in a nice formatted way, exactly like this: Odd of victory Bayern Munich: 1.33 Odd of draw: 3.25 Odd of victory Borrussia Dortmund: 6.5

```js
for (const [team, odd] of Object.entries(game.odds)) {
  const teamStr = team === "x" ? "draw" : `victory ${game[team]}`;
  console.log(`Odd of ${teamStr}: ${odd}`);

  // Odd of victory Bayern Munich: 1.33
  // Odd of draw: 3.25
  // Odd of victory Borrussia Dortmund: 6.5
}
```

- We loop over an `entries` array of key-value pairs and we destructure each key-value pair
- If team is equal to `X` `draw` gets returned, if not than display `victory` and team name which gets extracted from game (`game['team1'] //Bayern Munich `)

### 4. Create an object called 'scorers' which contains the names of the players who scored as properties, and the number of goals as the value. In this game, it will look like this: { Gnarby: 1, Hummels: 1, Lewandowski: 2 }

```js
const scorers = {};
for (const player of game.scored) {
  scorers[player] ? scorers[player]++ : (scorers[player] = 1);
}
```

- We loop through `game.scored` array
- If `player` is already in `scorers` their count is `incremented`, if not their `count` is set to `1`

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
