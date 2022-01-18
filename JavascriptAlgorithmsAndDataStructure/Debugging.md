## Javascript Algorithms and Data Structure > [Debugging](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/debugging)

### - Use typeof to Check the Type of a Variable

**Instruction**

Add two console.log() statements to check the typeof each of the two variables seven and three in the code.

**Code**

```
let seven = 7;
let three = "3";
console.log(seven + three);
// Only change code below this line
console.log(typeof seven)
console.log(typeof three)
```

### Catch Misspelled Variable and Function Names

> Transposed, missing, or mis-capitalized characters in a variable or function name will have the browser looking for an object that doesn't exist - and complain in the form of a reference error. JavaScript variable and function names are case-sensitive.

We can avoid this error using eslint (linting tool for JS)

### Catch Unclosed Parentheses, Brackets, Braces and Quotes

Using eslint and enable autofix will fix it

### Catch Mixed Usage of Single and Double Quotes

Using eslint and enable autofix will fix it

### Catch Use of Assignment Operator Instead of Equality Operator

### Catch Missing Open and Closing Parenthesis After a Function Call

```
function myFunction() {
  return "You rock!";
}
let varOne = myFunction; // [Function: myFunction]
let varTwo = myFunction(); // You rock!
```

### Catch Off By One Errors When Using Indexing

### Use Caution When Reinitializing Variables Inside a Loop

### Prevent Infinite Loops with a Valid Terminal Condition
