## Meaningful Text

### Links

- Specify when linking stuff so user knows where it takes them, especially if there are multiple links with same text ('click here').

```
<!-- Example 1: Where's "here"? -->
<a href='...'>Click here</a> to start your career in web development!

<!-- Example 2: I love that place! -->
Visit <a href='...'>The Odin Project</a> to start your career in web development!
```

- Indicate to the user what the link does.

```
<!-- Example 1: Now the user is aware that this link will open or download a PDF file. -->
<a href='...'>2021 Sign Up Statistics (PDF, 1MB)</a>

<!-- Example 2: And now the user knows this link opens in a new tab! -->
<a href='...'>GitHub (opens in new tab)</a>
```

### Forms

- Provide meaningful errors to users when filling out the form, so they know why the input is invalid for them. <br>
  (Inform them what input caused the error and, when possible, how to fix the error or why the error occurred in some way)

```
<!-- Example 1: Huh? -->
<div class='input-error'>Error: Invalid input.</div>

<!-- Example 2: That makes more sense. -->
<div class='input-error'>Error: Email is invalid.</div>

<!-- Example 3: Even better! -->
<div class='input-error'>Error: 'JohnSmith@@test.com' is not valid. Example of a valid email: example@yourdomain.com.</div>
```

- For instructions that are unique to an input, they should be placed alongside the input itself. Instructions that are more global, such as indicating which inputs are required, should be placed at the top of the form (“ \* indicates a required field”).

### Alternative Text

- Important for screen reader in order to tell user what image is being displayed.

- Put empty alt attribute if image isn't important for the user to be aware of.
