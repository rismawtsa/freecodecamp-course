## Javascript Algorithms and Data Structure > [Basic Data Structures](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/basic-data-structures)

### - Use an Array to Store a Collection of Data

```
let yourArray = [1, true, 'string', 'okay', 2]; // Change this line
```

### - Access an Array's Contents Using Bracket Notation

```
let x = yourArray[0] // x = 1

yourArray[0] = 2; // set the 1st position to 2

console.log(yourArray) // [2, true, 'string', 'okay', 2];
```

### - Add Items to an Array with push() and unshift()

push: adds elements to the end of an array
unshift: adds elements to the beginning of an array

```
let arr = [1, 2, 3];
arr.push(4, 5);
console.log(arr) // [1, 2, 3, 4, 5]

arr.unshift(-1, 0);
console.log(arr) // [-1, 0, 1, 2, 3, 4, 5]
```

### - Remove Items from an Array with pop() and shift()

pop: removes ==an element== from the end of an array
shift: removes ==an element== from the end of an array

```
function popShift(arr) {
  let popped = arr.pop(); // Change this line
  let shifted = arr.shift(); // Change this line
  return [shifted, popped];
}

console.log(popShift(['challenge', 'is', 'not', 'complete'])); // ['challenge', 'complete']
```

### - Remove Items Using splice()

splice: remove any number of consecutive elements from anywhere in an array.

take 3 parameters: start, deleteCount and item1, item2, ...optional (The elements to add to the array)

```
// just remove
let arr = [1, 2, 3, 4, 5, 6];
arr.splice(1, 2)
console.log(arr) // [1, 4, 5, 6];

arr.splice(2)
console.log(arr) // [1, 4];
```
learn more about slice on mdn https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice

### - Add Items Using splice()

splice: can also add elements to array using the third parameter.

```
function htmlColorNames(arr) {
  arr.splice(0, 2, 'DarkSalmon', 'BlanchedAlmond'). // remove the first to elements and add 'DarkSalmon' and 'BlanchedAlmond' in their respective places
  return arr;
}

console.log(htmlColorNames(['DarkGoldenRod', 'WhiteSmoke', 'LavenderBlush', 'PaleTurquoise', 'FireBrick']));

output: 
[ 'DarkSalmon',
  'BlanchedAlmond',
  'LavenderBlush',
  'PaleTurquoise',
  'FireBrick' ]
```

### - Copy Array Items Using slice()

slice() takes only 2 parameters — the first is the index at which to begin extraction, and the second is the index at which to stop extraction (extraction will occur up to, but not including the element at this index)

```
function forecast(arr) {
  const newArr = arr.slice(2, 4) // extracts array from index 2 to 3 and assign it to newArr variabel
  return newArr;
}

console.log(forecast(['cold', 'rainy', 'warm', 'sunny', 'cool', 'thunderstorms']));
output: ['warm', 'sunny']
```

### - Copy an Array with the Spread Operator

```
function copyMachine(arr, num) {
  let newArr = [];
  while (num >= 1) {
    // Only change code below this line
    newArr.push([...arr])
    // Only change code above this line
    num--;
  }
  return newArr;
}

console.log(copyMachine([true, false, true], 2));
```

### - Combine Arrays with the Spread Operator

```
function spreadOut() {
  let fragment = ['to', 'code'];
  let sentence = ['learning', ...fragment, 'is', 'fun']; // Change this line
  return sentence;
}

console.log(spreadOut());
```

### - Check For The Presence of an Element With indexOf()

indexOf() returns the position or index of that element or -1 if the element does not exist on the array.

```
function quickCheck(arr, elem) {
  return arr.indexOf(elem) >= 0 ? true : false
}

console.log(quickCheck(['squash', 'onions', 'shallots'], 'mushrooms'));
```

### - Iterate Through All an Array's Items Using For Loops

```
function filteredArray(arr, elem) {
  let newArr = [];
  // Only change code below this line
  for (let i = 0; i<arr.length; i++) {
    if(arr[i].indexOf(elem) === -1) {
      newArr.push(arr[i])
    }
  }
  // Only change code above this line
  return newArr;
}

console.log(filteredArray([[3, 2, 3], [1, 6, 3], [3, 13, 26], [19, 3, 9]], 3));
```

### -  Create complex multi-dimensional arrays

```
let myNestedArray = [
  // Only change code below this line
  ['unshift', false, 1, 2, 3, 'complex', 'nested'],
  [
    ['loop', 'shift', 6, 7, 1000, 'deep'],
  ],
  [
    [
      ['mutate', 1327.98, 'splice', 'slice', 'deeper'],
    ],
    [
      [
        ['iterate', 1.3849, 7, '8.4876', 'arbitrary', 'deepest']
      ]
    ]
  ]
  // Only change code above this line
];
```

-----

### - Add Key-Value Pairs to JavaScript Objects

**Instruction**

A foods object has been created with three entries. Using the syntax of your choice, add three more entries to it: bananas with a value of 13, grapes with a value of 35, and strawberries with a value of 27.

**Code**

```
let foods = {
  apples: 25,
  oranges: 32,
  plums: 28
};

// Only change code below this line
foods.bananas = 13;
foods.grapes = 35;
foods.strawberries = 27;
// Only change code above this line

console.log(foods);
```

### - Modify an Object Nested Within an Object

**Instructions**

Here we've defined an object userActivity, which includes another object nested within it. Set the value of the online key to 45.

**Code**

```
let userActivity = {
  id: 23894201352,
  date: 'January 1, 2017',
  data: {
    totalUsers: 51,
    online: 42
  }
};

// Only change code below this line
userActivity.data.online = 45;
// Only change code above this line

console.log(userActivity);
```

### - Access Property Names with Bracket Notation

**Instruction**

We've defined a function, checkInventory, which receives a scanned item as an argument. Return the current value of the scannedItem key in the foods object. You can assume that only valid keys will be provided as an argument to checkInventory.

**Code**

```
let foods = {
  apples: 25,
  oranges: 32,
  plums: 28,
  bananas: 13,
  grapes: 35,
  strawberries: 27
};

function checkInventory(scannedItem) {
  // Only change code below this line
  return foods[scannedItem]
  // Only change code above this line
}

console.log(checkInventory("apples"));
```

### - Use the delete Keyword to Remove Object Properties

**Instruction**

Use the delete keyword to remove the oranges, plums, and strawberries keys from the foods object.

**Code**

```
let foods = {
  apples: 25,
  oranges: 32,
  plums: 28,
  bananas: 13,
  grapes: 35,
  strawberries: 27
};

// Only change code below this line
delete foods.oranges;
delete foods.plums;
delete foods.strawberries;
// Only change code above this line

console.log(foods);
```

### - Check if an Object has a Property

```
users.hasOwnProperty('Alan');
'Alan' in users;
```

**Instruction**

Finish writing the function so that it returns true if the object passed to it contains all four names, Alan, Jeff, Sarah and Ryan and returns false otherwise.

**Code**

```
let users = {
  Alan: {
    age: 27,
    online: true
  },
  Jeff: {
    age: 32,
    online: true
  },
  Sarah: {
    age: 48,
    online: true
  },
  Ryan: {
    age: 19,
    online: true
  }
};

function isEveryoneHere(userObj) {
  // Only change code below this line
  let arr = ['Alan', 'Jeff', 'Sarah', 'Ryan'];
  let result = true;

  arr.forEach(item => {
    if (!(item in userObj)) {
      result = false
    }
  })

  return result
  // Only change code above this line
}

console.log(isEveryoneHere(users));
```

### - Iterate Through the Keys of an Object with a for...in Statement

**Instruction**

We've defined a function countOnline which accepts one argument (a users object). Use a for...in statement within this function to loop through the users object passed into the function and return the number of users whose online property is set to true. An example of a users object which could be passed to countOnline is shown below. Each user will have an online property with either a true or false value

**Code**

```
const users = {
  Alan: {
    online: false
  },
  Jeff: {
    online: true
  },
  Sarah: {
    online: false
  }
}

function countOnline(usersObj) {
  // Only change code below this line
  let userOnlineCount = 0;
  for (let user in usersObj) {
    if(usersObj[user].online) {
      userOnlineCount +=1;
    }
  }
  return userOnlineCount
  // Only change code above this line
}

console.log(countOnline(users));
```

### - Generate an Array of All Object Keys with Object.keys()

> This will return an array with strings representing each property in the object. Again, there will be no specific order to the entries in the array.

**Instruction**

Finish writing the getArrayOfUsers function so that it returns an array containing all the properties in the object it receives as an argument.

**Code**

```
let users = {
  Alan: {
    age: 27,
    online: false
  },
  Jeff: {
    age: 32,
    online: true
  },
  Sarah: {
    age: 48,
    online: false
  },
  Ryan: {
    age: 19,
    online: true
  }
};

function getArrayOfUsers(obj) {
  // Only change code below this line
  return Object.keys(obj)
  // Only change code above this line
}

console.log(getArrayOfUsers(users));
```

### - Modify an Array Stored in an Object

**Instruction**

Take a look at the object we've provided in the code editor. The user object contains three keys. The data key contains five keys, one of which contains an array of friends. From this, you can see how flexible objects are as data structures. We've started writing a function addFriend. Finish writing it so that it takes a user object and adds the name of the friend argument to the array stored in user.data.friends and returns that array.

**Code**

```
let user = {
  name: 'Kenneth',
  age: 28,
  data: {
    username: 'kennethCodesAllDay',
    joinDate: 'March 26, 2016',
    organization: 'freeCodeCamp',
    friends: [
      'Sam',
      'Kira',
      'Tomo'
    ],
    location: {
      city: 'San Francisco',
      state: 'CA',
      country: 'USA'
    }
  }
};

function addFriend(userObj, friend) {
  // Only change code below this line
  userObj.data.friends.push(friend);

  return userObj.data.friends
  // Only change code above this line
}

console.log(addFriend(user, 'Pete'));
```

