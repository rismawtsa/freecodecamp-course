## Javascript Algorithms and Data Structure > [Basic Algorithm Scripting](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-algorithm-scripting)

### - Convert Celsius to Fahrenheit

The algorithm to convert from Celsius to Fahrenheit is the temperature in Celsius times 9/5, plus 32.

You are given a variable celsius representing a temperature in Celsius. Use the variable fahrenheit already defined and assign it the Fahrenheit temperature equivalent to the given Celsius temperature. Use the algorithm mentioned above to help convert the Celsius temperature to Fahrenheit.

```
function convertToF(celsius) {
  let fahrenheit = celsius * 9/5 + 32;
  return fahrenheit;
}

convertToF(30);
```

### - Reverse a String

Reverse the provided string.

You may need to turn the string into an array before you can reverse it.

Your result must be a string.

```
function reverseString(str) {
  const arr = str.split('');
  return arr.reverse().join('');
}

reverseString("hello");

console.log(reverseString("hello"))
```

### - Factorialize a Number

```
function factorialize(num) {
  if (num === 0) return 1;

  let result = 1;
  for(let i=1; i<=num; i++) {
    result *=i;
  }
  return result;
}

console.log(factorialize(5));
```

### - Find the Longest Word in a String

Return the length of the longest word in the provided sentence.

Your response should be a number.

```
function findLongestWordLength(str) {
  const arr = str.split(' ');

  let result = 0;
  for(let i=0; i<arr.length; i++) {
    if(arr[i].length > result) {
      result = arr[i].length
    }
  }
  return result;
}

findLongestWordLength("The quick brown fox jumped over the lazy dog");
```

### - Return Largest Numbers in Arrays

Return an array consisting of the largest number from each provided sub-array. For simplicity, the provided array will contain exactly 4 sub-arrays.

Remember, you can iterate through an array with a simple for loop, and access each member with array syntax `arr[i]`.

```
function largestOfFour(arr) {
  let newArr = [];
  for(let i=0; i<arr.length; i++) {
    let maxVal = Number.NEGATIVE_INFINITY;
    for(let j=0; j<arr[i].length; j++) {
      if(maxVal < arr[i][j]) {
        maxVal = arr[i][j];
      }
    }
    newArr.push(maxVal)
  }

  return newArr;
}

console.log(largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]));
```

### - Confirm the Ending

Check if a string (first argument, str) ends with the given target string (second argument, target).

This challenge can be solved with the .endsWith() method, which was introduced in ES2015. But for the purpose of this challenge, we would like you to use one of the JavaScript substring methods instead.

```
function confirmEnding(str, target) {
  return str.substring(str.length - target.length) === target;
}

console.log(confirmEnding("Bastian", "n"));
```

### - Repeat a String Repeat a String

Repeat a given string str (first argument) for num times (second argument). Return an empty string if num is not a positive number. For the purpose of this challenge, do not use the built-in .repeat() method.

```
function repeatStringNumTimes(str, num) {
  if(num <= 0) return '';

  let result = '';
  let i = 0;
  while(i < num) {
    result += str;
    i++;
  }
  return result;
}

console.log(repeatStringNumTimes("abc", 3));
```

### - Truncate a String

Truncate a string (first argument) if it is longer than the given maximum string length (second argument). Return the truncated string with a ... ending.

```
function truncateString(str, num) {
  if (str.length > num) {
    return str.substring(0, num) + '...'
  }
  return str;
}
```

### - Finders Keepers

Create a function that looks through an array arr and returns the first element in it that passes a 'truth test'. This means that given an element x, the 'truth test' is passed if func(x) is true. If no element passes the test, return undefined.

```
function findElement(arr, func) {
  let num;

  let i = 0;
  while(i<arr.length){
    if(func(arr[i])){
      num = arr[i];
      break;
    }
    i++
  }
  return num;
}

findElement([1, 2, 3, 4], num => num % 2 === 0);
```

### - Boo who

Check if a value is classified as a boolean primitive. Return true or false.

Boolean primitives are true and false.

```
function booWho(bool) {
  return typeof bool === 'boolean' ? true : false;
}

booWho(null);
```

### - Title Case a Sentence

Return the provided string with the first letter of each word capitalized. Make sure the rest of the word is in lower case.

For the purpose of this exercise, you should also capitalize connecting words like the and of.

```
function titleCase(str) {
  const arr = str.split(' ');
  const data = arr.map(a => `${a[0].toUpperCase()}${a.substring(1).toLowerCase()}`)
  return data.join(' ');
}

console.log(titleCase("I'm a little tea pot"));
```

### - Slice and Splice

You are given two arrays and an index.

Copy each element of the first array into the second array, in order.

Begin inserting elements at index n of the second array.

Return the resulting array. The input arrays should remain the same after the function runs.

```
function frankenSplice(arr1, arr2, n) {
  const newArr = [...arr2]
  newArr.splice(n, 0, ...arr1)
  return newArr;
}

console.log(frankenSplice([1, 2, 3], [4, 5, 6], 1));
```

### - Falsy Bouncer

Remove all falsy values from an array.

Falsy values in JavaScript are `false`, `null`, `0`, `""`, `undefined`, and `NaN`.

Hint: Try converting each value to a Boolean.

```
function bouncer(arr) {
  let newArr = [];
  for(let i=0; i<arr.length; i++) {
    if(arr[i]){
      newArr.push(arr[i])
    }
  }
  return newArr;
}

console.log(bouncer([7, "ate", "", false, 9]));
```

### - Where do I Belong

Return the lowest index at which a value (second argument) should be inserted into an array (first argument) once it has been sorted. The returned value should be a number.

For example, getIndexToIns([1,2,3,4], 1.5) should return 1 because it is greater than 1 (index 0), but less than 2 (index 1).

Likewise, getIndexToIns([20,3,5], 19) should return 2 because once the array has been sorted it will look like [3,5,20] and 19 is less than 20 (index 2) and greater than 5 (index 1).

```
function getIndexToIns(arr, num) {
  arr.sort((a,b) => a-b);
  let index = 0;
  for(let i=0; i<arr.length - 1; i++) {
    if (num === arr[i]) {
      index = i;
    } else if (num > arr[i] && num < arr[i+1]) {
      index = i + 1;
    } else if (num > arr[i+1]) {
      index = i + 2;
    }
  }

  return index;
}
```

### - Mutations

Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

For example, \["hello", "Hello"], should return true because all of the letters in the second string are present in the first, ignoring case.

The arguments \["hello", "hey"] should return false because the string hello does not contain a y.

Lastly, \["Alien", "line"], should return true because all of the letters in line are present in Alien.

```
function mutation(arr) {
  let result = true;
  for (let c of arr[1].toLowerCase()) {
    if(arr[0].toLowerCase().indexOf(c) < 0) {
      result = false;
      break;
    }
  }
  return result;
}

console.log(mutation(["hello", "neo"]));
```
### - Chunky Monkey

Write a function that splits an array (first argument) into groups the length of size (second argument) and returns them as a two-dimensional array.

```
function chunkArrayInGroups(arr, size) {
  let newArr = [];
  for(let i=0; i<arr.length; i+=size) {
    let arr1 = [];
    for(let j=i; j< i+size && j < arr.length; j++) {
      arr1.push(arr[j]);
    }
    newArr.push(arr1)
  }
  return newArr;
}

console.log(chunkArrayInGroups([0, 1, 2, 3, 4, 5], 4));
```
