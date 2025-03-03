## Scope & Scope Chain

### Global Scope

- Outside of any function or block
- Variables declared in global scope are accessible everywhere

```
const me = 'Jonas';
const job = 'Teacher';
const year = 1989;
```

### Function Scope

- Variables are accessible only inside function, not outside.

```
function calcAge(birthYear){
    const now = 2037;
    const age = now - birthYear;
    return age;
}
console.log(now); // Reference Error
```

### Block Scope

- Variables are accessible only inside block `{ }`  
  (if block, for loop etc.)
- Only applies to `let` and `const`
- Functions are also block scoped.

```
if(year >= 1981 && year <= 1996){
    const millennial = true;
    const food = 'Avocado toast';
}
console.log(millennial); // Reference Error
```

### Scope Chain

_Order in which functions are written in the code, !called_

```
const myName = 'Jonas';

function first(){
    const age = 30;

    if(age >= 30){
        const decade = 3;
        var millennial = true;
    }

    function second(){
        const job = 'teacher';

        console.log(`${myName} is a ${age}-old ${job}`);
        // Jonas is 30-old teacher
    }

    second();
}

first();
```

- Global Scope - `myName = 'Jonas'`
- first() Scope - `age = 30 millennial = true myName= 'Jonas'`
- second() Scope - `job = 'teacher' age = 30 millennial = true myName= 'Jonas'`
- if block Scope - `decade = 3 age = 30 millennial = true myName= 'Jonas'`

  > Scope has access to variables from all outer scopes, so it looks up for required variables. Second Scope (&| if block Scope) > First Scope > Global Scope

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
