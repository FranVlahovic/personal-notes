## This Keyword

- Takes the value of (points to) the "owner" of the function in which the `this` keyword is used.
- Value is only assigned when the function is actually called.
- Doesn't point to the function itself or the variable environment.

### Method `this` = Object that is calling the method

```JavaScript
const jonas = {
	name: 'Jonas',
	year: 1989,
	calcAge: function(){
		return 2037 - this.year // 'this' == jonas
	}
};

jonas.calcAge(); // 48
```

### Function Call `this` = undefined

```JavaScript
function showYear() {
    console.log(this.year);
}

const jonas = {
    name: 'Jonas',
    year: 1989,
    calcAge: function(){
        return 2037 - this.year
    }
};

showYear(); // undefined (`this` is `undefined` in strict mode)
```

### Arrow Function `this` = surrounding function `this`

```JavaScript
const jonas = {
    name: 'Jonas',
    year: 1989,
    calcAge: function(){
        const arrowFunction = () => {
            console.log(this); // `this` == surrounding `calcAge` function's `this` (`jonas`)
            return 2037 - this.year;
        };
        return arrowFunction();
    }
};
console.log(jonas.calcAge()); // 48
```

### Event Listener `this` = DOM Element that the handler is attached to

```JavaScript
const button = document.createElement('button');
button.textContent = 'Calculate Age';

document.body.appendChild(button);

const jonas = {
    name: 'Jonas',
    year: 1989,
    calcAge: function(){
        return 2037 - this.year;
    }
};

button.addEventListener('click', function() {
    console.log(this.textContent); // "Calculate Age" (button element)
});

button.addEventListener('click', function() {
    console.log(jonas.calcAge()); // 48
});
```

#### ↩️ [Jonas Main](/work/notes/jonas_schmedtmann/jonas-schmedtmann-notes.md)
