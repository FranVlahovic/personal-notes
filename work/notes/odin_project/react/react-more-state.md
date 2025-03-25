## MORE ON STATE

### Structure State

```jsx
import { useState } from "react";

export default function Person() {
  const [person, setPerson] = useState({ name: "John", age: 100 });

  const handleIncreaseAge = () => {
    const newPerson = { ...person, age: person.age + 1 };
    setPerson(newPerson);
  };

  return (
    <>
      <h1>{person.name}</h1>
      <h2>{person.age}</h2>
      <button onClick={handleIncreaseAge}>Increase age</button>
    </>
  );
}
```

- We should always provide a new `Object` for `setState` to trigger a rerender.

### How state updates

- whenever we call the `setState` function, React will apply the update in the next component render

### Controlled Components

```jsx
export function CustomInput() {
  const [value, setValue] = useState("");

  return (
    <input
      type="text"
      value={value}
      onChange={(event) => setValue(event.target.value)}
    />
  );
}
```

## State as a Snapshot

### Setting state triggers renders

```jsx
import { useState } from "react";

export default function Form() {
  const [isSent, setIsSent] = useState(false);
  const [message, setMessage] = useState("Hi!");
  if (isSent) {
    return <h1>Your message is on its way!</h1>;
  }
  return (
    <form
      onSubmit={(e) => {
        e.preventDefault();
        setIsSent(true);
        sendMessage(message);
      }}
    >
      <textarea
        placeholder="Message"
        value={message}
        onChange={(e) => setMessage(e.target.value)}
      />
      <button type="submit">Send</button>
    </form>
  );
}

function sendMessage(message) {
  // ...
}
```

- The `onSubmit` event handler executes.
- `setIsSent(true)` sets `isSent` to true and queues a new render.
- React re-renders the component according to the new `isSent` value.

### Rendering takes a snapshot in time

```jsx
import { useState } from "react";

export default function Counter() {
  const [number, setNumber] = useState(0);

  return (
    <>
      <h1>{number}</h1>
      <button
        onClick={() => {
          setNumber(number + 1);
          setNumber(number + 1);
          setNumber(number + 1);
        }}
      >
        +3
      </button>
    </>
  );
}
```

- Even though we called `setNumber(number + 1)` three times, in this render’s event handler `number` is always `0`, so we set the state to `1` `three times`
- After your event handler finishes, React re-renders the component with `number` equal to `1` rather than `3`.

### State over time

```jsx
import { useState } from "react";

export default function Counter() {
  const [number, setNumber] = useState(0);

  return (
    <>
      <h1>{number}</h1>
      <button
        onClick={() => {
          setNumber(number + 5);
          alert(number);
        }}
      >
        +5
      </button>
    </>
  );
}
```

- State Updates in React are asynchronous, meaning the `alert()` displays the state value `at the moment the button is clicked`, not the `updated state`.

- The `setNumber(number + 5)` queues a state update, but React processes it after the event handler completes.

### Challenge

#### Add an alert to the click handler. When the light is green and says “Walk”, clicking the button should say “Stop is next”. When the light is red and says “Stop”, clicking the button should say “Walk is next”.

##### Solution

```jsx
import { useState } from "react";

export default function TrafficLight() {
  const [walk, setWalk] = useState(true);

  function handleClick() {
    setWalk(!walk);
    alert(walk ? "Stop is next" : "Walk is next");
  }

  return (
    <>
      <button onClick={handleClick}>Change to {walk ? "Stop" : "Walk"}</button>

      <h1
        style={{
          color: walk ? "darkgreen" : "darkred",
        }}
      >
        {walk ? "Walk" : "Stop"}
      </h1>
    </>
  );
}
```

- Whether you put it before or after the `setWalk` call makes no difference. That render’s value of walk is fixed. Calling `setWalk` will only change it for the next render, but will not affect the event handler from the previous render

### Challenge 2: Add two separate input fields for the first name and the last name. Either of these should be able to update the full name in the h1 element with every keystroke.

#### Method 1

```jsx
import { useState } from "react";

export default function Person() {
  const [person, setPerson] = useState({
    firstName: "",
    lastName: "",
    age: 100,
  });

  const fullName = person.firstName + " " + person.lastName;

  const handleFirstNameChange = (e) => {
    const firstNameChange = { ...person, firstName: e.target.value };
    setPerson(firstNameChange);
  };

  const handleLastNameChange = (e) => {
    const lastNameChange = { ...person, lastName: e.target.value };
    setPerson(lastNameChange);
  };

  const handleIncreaseAge = () => {
    const newPerson = { ...person, age: person.age + 1 };
    setPerson(newPerson);
  };

  return (
    <>
      <label>
        First name:{" "}
        <input value={person.firstName} onChange={handleFirstNameChange} />
      </label>

      <label>
        Last name:{" "}
        <input value={person.lastName} onChange={handleLastNameChange} />
      </label>

      <h1>{fullName}</h1>
      <h2>{person.age}</h2>
      <button onClick={handleIncreaseAge}>Increase age</button>
    </>
  );
}
```

#### Method 2

```jsx
import { useState } from "react";

export default function Person() {
  const [firstName, setFirstName] = useState("");
  const [lastName, setLastName] = useState("");
  const [age, setAge] = useState(100);

  const fullName = firstName + " " + lastName;

  const handleFirstNameChange = (e) => {
    setFirstName(e.target.value);
  };

  const handleLastNameChange = (e) => {
    setLastName(e.target.value);
  };

  const handleIncreaseAge = () => {
    setAge(age + 1);
  };

  return (
    <>
      <label>
        First name: <input value={firstName} onChange={handleFirstNameChange} />
      </label>

      <label>
        Last name: <input value={lastName} onChange={handleLastNameChange} />
      </label>

      <h1>{fullName}</h1>
      <h2>{age}</h2>
      <button onClick={handleIncreaseAge}>Increase age</button>
    </>
  );
}
```

#### ↩️ [Odin Project Main](/work/notes/odin_project/the-odin-project.md)
