## What is JSX?

### Rules of JSX

#### 1) Return a single root element

- If we wish to return multiple elements in a component we can do it by wrapping them in a parent tag
- This can be a `div`, or if we don't want the elements to have a container we can use React fragment `'<></>'`

##### Incorrect:

```jsx
function App(){
    return (
        <h1> Example h1 </h1>
        <h2> Example h2 </h2>
    );
}
```

##### Correct:

```jsx
function App() {
  return (
    <>
      <h1>Example h1</h1>
      <h2>Example h2</h2>
    </>
  );
}
```

#### 2) Close all tags

- In JSX we must explicitly close and wrap tags
- `<input>` becomes `<input />`, and `<li>` becomes `<li></li>`

##### Incorrect:

```jsx
function App() {
  return (
    <>
      <input>
      <li>
    </>
  );
}
```

##### Correct:

```jsx
function App() {
  return (
    <>
      <input />
      <li></li>
    </>
  );
}
```

#### 3) CamelCase most things

- Many HTML attributes are written in camelCase
- Instead of `stroke-width` we'd use `strokeWidth` and instead of `class` we'd use `className`

##### Incorrect

```jsx
function App() {
  return (
    <div class="container">
      <svg>
        <circle cx="25" cy="75" r="20" stroke="green" stroke-width="2" />
      </svg>
    </div>
  );
}
```

##### Correct

```jsx
function App() {
  return (
    <div className="container">
      <svg>
        <circle cx="25" cy="75" r="20" stroke="green" strokeWidth="2" />
      </svg>
    </div>
  );
}
```

### Converting HTML to JSX

#### HTML

```HTML
<h1>Test title</h1>
<svg>
  <circle cx="25" cy="75" r="20" stroke="green" stroke-width="2" />
</svg>
<form>
  <input type="text">
</form>
```

#### JSX

```jsx
<div>
  <h1>Test title</h1>
  <svg>
    <circle cx="25" cy="75" r="20" stroke="green" strokeWidth="2" />
  </svg>
  <form>
    <input type="text" />
  </form>
</div>
```

### Converting Challenge

#### Start

```jsx
export default function Bio() {
  return (
    <div class="intro">
      <h1>Welcome to my website!</h1>
    </div>
    <p class="summary">
      You can find my thoughts here.
      <br><br>
      <b>And <i>pictures</b></i> of scientists!
    </p>
  );
}
```

#### Final

```jsx
export default function Bio() {
  return (
    <div>
      <div className="intro">
        <h1>Welcome to my website!</h1>
      </div>
      <p className="summary">
        You can find my thoughts here.
        <br />
        <br />
        <b>
          And <i>pictures</i>
        </b> of scientists!
      </p>
    </div>
  );
}
```

1. Wrapped elements in parent tag: `<div></div>`
1. Moved closing bold tag `</b>` outside italic `<i></i>`
1. Added closing tag for `<br>`

### Passing Strings with quotes

- When we want to pass a string attribute to JSX we put it in single or double quotes

```jsx
export default function Avatar() {
  return (
    <img
      className="avatar"
      src="https://i.imgur.com/7vQD0fPs.jpg"
      alt="Gregorio Y. Zara"
    />
  );
}
```

- When we want to dynamically specify the `src` or `alt` text we could use a value from JS by using `{ }`

```jsx
export default function Avatar() {
  const avatar = "https://i.imgur.com/7vQD0fPs.jpg";
  const description = "Gregorio Y. Zara";
  return <img className="avatar" src={avatar} alt={description} />;
}
```

### Using Curly braces: Window into JS World

```jsx
export default function TodoList() {
  const name = "Gregorio Y.Zara";
  return <h1>{name}'s To Do List </h1>;
}
```

- Any JS Expression will work inside curly braces, including function calls

```jsx
const today = new Date();

function formatDate(date) {
  return new Intl.DateTimeFormat("en-us", { weekday: "long" }).format(date);
}

export default function TodoList() {
  return <h1>To Do List for {formatDate(today)}</h1>;
}
```

### Using double curlies

- In order to pass a JS Object in JSX we need to wrap the object in another pair of curly braces: <br>`person={{ name: 'Fran v', inventions: 5 }}`

```jsx
export default function TodoList() {
  return (
    <ul
      style={{
        backgroundColor: "black",
        color: "pink",
      }}
    >
      <li>Improve the videophone</li>
      <li>Prepare aeronautics lectures</li>
      <li>Work on the alcohol-fuelled engine</li>
    </ul>
  );
}
```

- Inline style properties are written in camelCase `<ul style={{ backgroundColor: "black" color: "pink"}}>`

```jsx
const person = {
  name: "Gregorio Y. Zara",
  theme: {
    backgroundColor: "black",
    color: "pink",
  },
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src="https://i.imgur.com/7vQD0fPs.jpg"
        alt="Gregorio Y. Zara"
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

### JSX Curly Braces Challenge

#### Starter

```jsx
const baseUrl = "https://i.imgur.com/";
const person = {
  name: "Gregorio Y. Zara",
  imageId: "7vQD0fP",
  imageSize: "s",
  theme: {
    backgroundColor: "black",
    color: "pink",
  },
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src="{baseUrl}{person.imageId}{person.imageSize}.jpg"
        alt={person.name}
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

#### Final

```jsx
const baseUrl = "https://i.imgur.com/";
const person = {
  name: "Gregorio Y. Zara",
  imageId: "7vQD0fP",
  imageSize: "s",
  theme: {
    backgroundColor: "black",
    color: "pink",
  },
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src={baseUrl + person.imageId + person.imageSize + ".jpg"}
        alt={person.name}
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

#### Or

```jsx
// utils.js
export function getImageUrl(obj) {
  const baseUrl = "https://i.imgur.com/";
  return `${baseUrl}${obj.imageId}${obj.imageSize}.jpg`;
}

// main file
import { getImageUrl } from "./utils.js";

const person = {
  name: "Gregorio Y. Zara",
  imageId: "7vQD0fP",
  imageSize: "s",
  theme: {
    backgroundColor: "black",
    color: "pink",
  },
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img className="avatar" src={getImageUrl(person)} alt={person.name} />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

#### ↩️ [Odin Project Main](/work/notes/odin_project/the-odin-project.md)
