## React State

- `State` is components memory

```jsx
import React, { useState } from "react";
import "./App.css";

const COLORS = ["pink", "green", "blue", "yellow", "purple"];

function App() {
  const [backgroundColor, setBackgroundColor] = useState(COLORS[0]);

  const onButtonClick = (color) => () => {
    setBackgroundColor(color);
  };

  return (
    <div
      className="App"
      style={{
        backgroundColor,
      }}
    >
      {COLORS.map((color) => (
        <button
          type="button"
          key={color}
          onClick={onButtonClick(color)}
          className={backgroundColor === color ? "selected" : ""}
        >
          {color}
        </button>
      ))}
    </div>
  );
}

export default App;
```

- we set current state value which is `backgroundColor`
- `useState(COLORS[0])` is default value, as soon as the `setBackgroundColor` gets 'triggered' this gets ignored
- `setBackgroundColor` is a function to update the state value
- we use `map` to extract values from `COLORS` array
- each '`color`' gets event listener which `setsBackgroundColor` to value from array which is `color` we want
- each `color` gets className selected if `backgroundColor` is equal to `color` (means its clicked)

### Hooks

- `hooks` are recognizable by the use prefix
- hook rules:
  - `hooks` can only be called from the top level of functional component
  - `hooks` cant be called from inside loops or conditions

### Adding State Variable

```jsx
import { useState } from "react";
import { sculptureList } from "./data.js";

export default function Gallery() {
  const [index, setIndex] = useState(0);

  function handleClick() {
    setIndex(index + 1);
  }

  let sculpture = sculptureList[index];

  return (
    <>
      <button onClick={handleClick}>Next</button>
      <h2>
        <i>{sculpture.name} </i> by {sculpture.artist}
      </h2>
      <h3>
        ({index + 1}) of {sculptureList.length}
      </h3>
      <img src={sculpture.url} alt={sculpture.alt} />
      <p>{sculpture.description}</p>
    </>
  );
}
```

- Your component renders the first time. Because you passed 0 to `useState` as the initial value for `index`, it will return `[0, setIndex]`. React remembers 0 is the `latest state value`.

- You update the state. When a user clicks the button, it calls `setIndex(index + 1)`. `index` is `0`, so it’s `setIndex(1)`. This tells React to remember index is 1 now and triggers another render.

- Your component’s second render. React still sees `useState(0)`, but because React remembers that you set index to 1, it returns `[1, setIndex]` instead.

### Giving component multiple state variables

```jsx
import { useState } from "react";
import { sculptureList } from "./data.js";

export default function Gallery() {
  const [index, setIndex] = useState(0);
  const [showMore, setShowMore] = useState(false);

  function handleNextClick() {
    setIndex(index + 1);
  }

  function handleMoreClick() {
    setShowMore(!showMore);
  }

  let sculpture = sculptureList[index];

  return (
    <>
      <button onClick={handleNextClick}>Next</button>
      <h2>
        <i>{sculpture.name} </i> by {sculpture.artist}
      </h2>
      <h3>
        ({index + 1}) of {sculptureList.length}
      </h3>
      <button onClick={handleMoreClick}>
        {showMore ? "Hide" : "Show"} details
      </button>
      {showMore && <p>{sculpture.description}</p>}
      <img src={sculpture.url} alt={sculpture.alt} />
    </>
  );
}
```

- we use `handleMoreClick` to toggle between hidden and shown description. default value is hidden

- State is local to a component instance on the screen. In other words, if you render the same component twice, each copy will have completely isolated state! Changing one of them will not affect the other.

### Challenges

#### 1) Fix the crash that happens when pressing "Next" on the last sculpture by updating the logic or disabling the button when no further action is possible. Then, add a "Previous" button to navigate to the prior sculpture, ensuring it does not crash on the first sculpture.

##### Solution

```jsx
import { useState } from "react";
import { sculptureList } from "./data.js";

export default function Gallery() {
  const [index, setIndex] = useState(0);
  const [showMore, setShowMore] = useState(false);

  let hasPrev = index > 0;
  let hasNext = index < sculptureList.length - 1;

  function handlePrevClick() {
    if (hasPrev) {
      setIndex(index - 1);
    }
  }

  function handleNextClick() {
    if (hasNext) {
      setIndex(index + 1);
    }
  }

  function handleMoreClick() {
    setShowMore(!showMore);
  }

  let sculpture = sculptureList[index];
  return (
    <>
      <button onClick={handlePrevClick} disabled={!hasPrev}>
        Previous
      </button>

      <button onClick={handleNextClick} disabled={!hasNext}>
        Next
      </button>
      <h2>
        <i>{sculpture.name} </i> by {sculpture.artist}
      </h2>
      <h3>
        ({index + 1}) of {sculptureList.length}
      </h3>
      <button onClick={handleMoreClick}>
        {showMore ? "Hide" : "Show"} details
      </button>
      {showMore && <p>{sculpture.description}</p>}
      <img src={sculpture.url} alt={sculpture.alt} />
    </>
  );
}
```

- we set `let hasPrev = index > 0` in order to let us know if we are at the beginning of an array of `sculpturesList`
- we set `let hasNext = index < sculptureList.length - 1` to let us know if we are at the end of the sculptureList
- if `hasPrev` is `true` we can go back with `setIndex(index - 1)`, if `hasNext` is true we can go forward with `setIndex(index + 1)`
- `showMore` is false and with `setShowMore(!showMore)` we make it toggle `true` or `false`
- extract single `sculpture` from `sculptureList` with `let sculpture = sculptureList[index]`
- disabled button with `disabled{!hasPrev}` and `disabled{!hasNext}` if there is no next `sculpture` and if there is no previous `sculpture`
- if `showMore` is `true` make `button` display "Hide details" and show `sculpture.description`

#### 2) Fix stuck form input

##### Solution

```jsx
export default function Form() {
  const [firstName, setFirstName] = useState("");
  const [lastName, setLastName] = useState("");

  function handleFirstNameChange(e) {
    setFirstName(e.target.value);
  }

  function handleLastNameChange(e) {
    setLastName(e.target.value);
  }

  function handleReset() {
    setFirstName("");
    setLastName("");
  }
  return (
    <form onSubmit={(e) => e.preventDefault()}>
      <input
        placeholder="First name"
        value={firstName}
        onChange={handleFirstNameChange}
      />
      <input
        placeholder="Last name"
        value={lastName}
        onChange={handleLastNameChange}
      />
      <h1>
        Hi, {firstName} {lastName}
      </h1>
      <button onClick={handleReset}>Reset</button>
    </form>
  );
}
```

- `handleFirstNameChange(e)` captures current input value with `e.target.value` `onChange{handleFirstNameChange}` triggers it
- `value={firstName}` connects the input field to a React state variable `firstName` it ensures that the input field's value always matches the `firstName` state
- The reconciliation algorithm works by comparing the current virtual DOM tree to the updated virtual DOM tree, and making the minimum number of changes necessary to bring the virtual DOM in line with the updated state.

### Challenge color changing bg

#### Counter for how many times background got changed

```jsx
import React, { useState } from "react";
import "./App.css";

const COLORS = ["pink", "green", "blue", "yellow", "purple"];

function App() {
  const [backgroundColor, setBackgroundColor] = useState(COLORS[0]);
  const [countChangeColor, setCountChangeColor] = useState(0);

  const onButtonClick = (color) => () => {
    if (color !== backgroundColor) {
      setBackgroundColor(color);
      setCountChangeColor((count) => count + 1);
    }
  };

  return (
    <div className="App" style={{ backgroundColor }}>
      <p>Background color has been changed {countChangeColor} times. </p>

      {COLORS.map((color) => (
        <button
          type="button"
          key={color}
          onClick={onButtonClick(color)}
          className={backgroundColor === color ? "selected" : ""}
        >
          {color}
        </button>
      ))}
    </div>
  );
}

export default App;
```

- if cliked `color` is not equal to `backgroundColor` we displayed that color with `setBackgroundColor` and we increment `counter` with `setCountChangeColor`
