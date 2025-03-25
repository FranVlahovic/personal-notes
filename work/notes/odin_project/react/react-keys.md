## Keys in React

- We can use `crypto.randomUUID()` to generate a unique id

```jsx
const todos = [
    { task: "mow the yard", id:crypto.randomUUID() },
    { task:"Work on Odin Projects", id:crypto.randomUUID() },
    { task:"feed the cat", id:crypto.randomUUID() },
}];

function TodoList(){
    return (
        <ul>
            {todos.map((todo) => (
                <li key={todo.id}>{todo.task}</li>
            ))}
        </ul>
    )
}
```

- If we are sure the list will remain unchanged we can use the array index as a key

  > This is not recommended since it can lead to confusing bugs if the list changes.

```jsx
const months = [
  "January",
  "February",
  "March",
  "April",
  "May",
  "June",
  "July",
  "August",
  "September",
  "October",
  "November",
  "December",
];

function MonthList() {
  return (
    <ul>
      {months.map((month, index) => (
        <li key={index}>{month}</li>
      ))}
    </ul>
  );
}
```

- `key` should be inferred from the data itself, not while rendering `(key={crypto.randomUUID()})`

```jsx
const todos [
    { task: "mow the yard", id:crypto.randomUUID() }
    { task: "Work on Odin Projects", id:crypto.randomUUID() }
    { task: "feed the cat", id:crypto.randomUUID() }
];

function TodoList(){
    return (
        <ul>
            {todos.map((todo) => (
                <li key={crypto.randomUUID()}>{todo.task}</li>
            ))}
        </ul>
    )
}
```

- Keys tell React which array item each component corresponds to so it can match them up later.
- Rather than generating keys on the fly we should include them in our data

```jsx
// data.js
export const people = [
  {
    id: 0, // Used in JSX as a key
    name: "Creola Katherine Johnson",
    profession: "mathematician",
    accomplishment: "spaceflight calculations",
    imageId: "MK3eW3A",
  },
  {
    id: 1, // Used in JSX as a key
    name: "Mario José Molina-Pasquel Henríquez",
    profession: "chemist",
    accomplishment: "discovery of Arctic ozone hole",
    imageId: "mynHUSa",
  },
  {
    id: 2, // Used in JSX as a key
    name: "Mohammad Abdus Salam",
    profession: "physicist",
    accomplishment: "electromagnetism theory",
    imageId: "bE7W1ji",
  },
  {
    id: 3, // Used in JSX as a key
    name: "Percy Lavon Julian",
    profession: "chemist",
    accomplishment:
      "pioneering cortisone drugs, steroids and birth control pills",
    imageId: "IOjWm71",
  },
  {
    id: 4, // Used in JSX as a key
    name: "Subrahmanyan Chandrasekhar",
    profession: "astrophysicist",
    accomplishment: "white dwarf star mass calculations",
    imageId: "lrWQx8l",
  },
];

// App.jsx
import { people } from "./data.js";
import { getImageUrl } from "./utils.js";

export default function List() {
  const listItems = people.map((person) => (
    <li key={person.id}>
      <img src={getImageUrl(person)} alt={person.name} />
      <p>
        <b>{person.name}</b>
        {" " + person.profession + " "}
        known for {person.accomplishment}
      </p>
    </li>
  ));
  return <ul>{listItems}</ul>;
}
```

- if our data is coming from a database we can use database keys/IDs which are unique by nature

- If our data is generated and persisted locally use an `incrementing counter`, `crypto.randomUUID()` or package `uuid` when creating items.

#### ↩️ [Odin Project Main](/work/notes/odin_project/the-odin-project.md)
