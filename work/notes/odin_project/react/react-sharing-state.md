## Sharing States between components

### Challenge 1

#### Synced Inputs

##### Starter

<details>
<summary style="font-size: 1em;font-weight: bold;"> Expand Code</summary>

```jsx
import { useState } from "react";

export default function SyncedInputs() {
  return (
    <>
      <Input label="First input" />
      <Input label="Second input" />
    </>
  );
}

function Input({ label }) {
  const [text, setText] = useState("");

  function handleChange(e) {
    setText(e.target.value);
  }

  return (
    <label>
      {label} <input value={text} onChange={handleChange} />
    </label>
  );
}
```

</details>

##### Solution

```jsx
import { useState } from "react";

export default function SyncedInputs() {
  const [text, setText] = useState("");

  function handleChange(e) {
    setText(e.target.value);
  }

  return (
    <>
      <Input label="First input" value={text} onChange={handleChange} />
      <Input label="Second input" value={text} onChange={handleChange} />
    </>
  );
}

function Input({ label, value, onChange }) {
  return (
    <label>
      {label} <input value={value} onChange={onChange} />
    </label>
  );
}
```

### Challenge 2

#### Filtering List

##### Starter

<details>
<summary style="font-size: 1em;font-weight: bold;"> Expand Code</summary>

```jsx
import { useState } from "react";
import { foods, filterItems } from "./data.js";

export default function FilterableList() {
  return (
    <>
      <SearchBar />

      <hr />
      <List items={foods} />
    </>
  );
}

function SearchBar() {
  const [query, setQuery] = useState("");

  function handleChange(e) {
    setQuery(e.target.value);
  }

  return (
    <label>
      Search: <input value={query} onChange={handleChange} />
    </label>
  );
}

function List({ items }) {
  return (
    <table>
      <tbody>
        {items.map((food) => (
          <tr key={food.id}>
            <td>{food.name}</td>
            <td>{food.description}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```

</details>

##### Solution

```jsx
import { useState } from "react";
import { foods, filterItems } from "./data.js";

export default function FilterableList() {
  const [query, setQuery] = useState("");
  const results = filterItems(foods, query);

  function handleChange(e) {
    setQuery(e.target.value);
  }

  return (
    <>
      <SearchBar query={query} onChange={handleChange} />

      <hr />
      <List items={results} />
    </>
  );
}

function SearchBar({ query, onChange }) {
  return (
    <label>
      Search: <input value={query} onChange={onChange} />
    </label>
  );
}

function List({ items }) {
  return (
    <table>
      <tbody>
        {items.map((food) => (
          <tr key={food.id}>
            <td>{food.name}</td>
            <td>{food.description}</td>
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```
