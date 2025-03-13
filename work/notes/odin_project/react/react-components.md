## React Components

<details>
<summary style="font-size: 1.2em;font-weight: bold;"> Expand Example Code</summary>

### How to Create Components

> Greeting.jsx

```jsx
function Greeting() {
  return <h1>&quot;Hello, my name is Fran&quot;</h1>;
}
```

- React components must be capitalized or they will not function as expected, which is why we capitalized `Greeting()` it uses the capitalization to tell the difference between an `HTML tag` and `React component`.

- `&quot;` is an escape code we use to render `"`. Your linter will greet you with an error if you use regular quotes.

### Where do Components live

- While independence is great, we do want the component to use functionality created elsewhere, and to share itself with other components; we use `import` and `export` for that

#### Exporting Component

> Greeting.jsx

```jsx
function Greeting() {
  return <h1>&quot;Hello, my name is Fran&quot;</h1>;
}

export default Greeting;
```

#### Importing Components

> Main.jsx

```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.jsx";
import Greeting from "./Greeting.jsx";
import "./index.css";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <Greeting />
  </StrictMode>
);
```

- The `components` inside `.render()` will be displayed in the browser.

### Named Exports

- Unlike `default export`, you must use the same `name` when `importing`

- Used to `export` multiple `components`

> FavoriteFood.jsx

```jsx
export function FavoriteFood() {
  return <p>My favorite food is Pasta</p>;
}
```

- Uses `destructuring` in `function parameters` to access `status` and `name` props.

- Dynamically inserts `status` and `name` inside JSX using `'{}'`

> Relationship.jsx

```jsx
export function Relationship({ status, name }) {
  return (
    <p>
      Im currently {status} with {name}
    </p>
  );
}
```

> Main.jsx

```jsx
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import "./index.css";
import App from "./App.jsx";
import Greeting from "./Greeting.jsx";
import { FavoriteFood } from "./FavoriteFood.jsx";
import { Relationship } from "./Relationship.jsx";

createRoot(document.getElementById("root")).render(
  <StrictMode>
    <>
      <Greeting />
      <FavoriteFood />
      <Relationship status="married" name="Doris" />
    </>
  </StrictMode>
);
```

- React fragments (`<>...</>`) allow grouping multiple `components` without adding extra divs to the DOM

- It is a `named export` component, meaning it must be `imported` with `'{}'`

- `'<Relationship status="married" name="Doris" />'` → Passes props to dynamically display relationship details.

</details>
