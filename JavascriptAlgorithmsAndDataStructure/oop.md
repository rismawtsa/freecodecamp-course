## Javascript Algorithms and Data Structure > [Object Oriented Programming](https://www.freecodecamp.org/learn/javascript-algorithms-and-data-structures/object-oriented-programming)

### - Create a Basic JavaScript Object

```
let dog = {
  name: 'dog',
  numLegs: 4
};
```

### - Use Dot Notation to Access the Properties of an Object

```
let dog = {
  name: "Spot",
  numLegs: 4
};
// Only change code below this line
console.log(dog.name)
console.log(dog.numLegs)
```

### - Create a Method on an Object

Objects can have a special type of property, called a method.

Methods are properties that are functions. This adds different behavior to an object.

**Instruction**

Using the dog object, give it a method called sayLegs. The method should return the sentence This dog has 4 legs.

**Code**

```
let dog = {
  name: "Spot",
  numLegs: 4,
  sayLegs: function() {
    return `This dog has ${this.numLegs} legs.`
  }
};

console.log(dog.sayLegs());
```

### - Make Code More Reusable with the this Keyword

```
let dog = {
  name: "Spot",
  numLegs: 4,
  sayLegs: function() {return "This dog has " + this.numLegs + " legs.";}
};

dog.sayLegs();
```
### - Define a Constructor Function

Constructors are functions that create new objects. They define properties and behaviors that will belong to the new object. Think of them as a blueprint for the creation of new objects.

```
function Dog() {
  this.name = 'Dog';
  this.color = 'Black';
  this.numLegs = 4;
}
```

- Constructors are defined with a capitalized name to distinguish them from other functions that are not constructors.
- Constructors use the keyword this to set properties of the object they will create. Inside the constructor, this refers to the new object it will create.
- Constructors define properties and behaviors instead of returning a value as other functions might.

### - Use a Constructor to Create Objects

Use the Dog constructor from the last lesson to create a new instance of Dog, assigning it to a variable hound.

```
function Dog() {
  this.name = "Rupert";
  this.color = "brown";
  this.numLegs = 4;
}
// Only change code below this line
const hound = new Dog()
```

> Without the new operator, this inside the constructor would not point to the newly created object, giving unexpected results.

### - Extend Constructors to Receive Arguments

Create another `Dog` constructor. This time, set it up to take the parameters `name` and `color`, and have the property `numLegs` fixed at `4`. Then create a new `Dog` saved in a variable `terrier`. Pass it two strings as arguments for the `name` and `color` properties.

```
function Dog(name, color) {
  this.name = name;
  this.color = color;
  this.numLegs = 4;
}

const terrier = new Dog('Doge', 'Brown')
```

### - Verify an Object's Constructor with instanceof

> Anytime a constructor function creates a new object, that object is said to be an instance of its constructor. JavaScript gives a convenient way to verify this
> with the instanceof operator. instanceof allows you to compare an object to a constructor, returning true or false based on whether or not that object was
> created with the constructor

**Instruction**

Create a new instance of the House constructor, calling it myHouse and passing a number of bedrooms. Then, use instanceof to verify that it is an instance of House.

```
function House(numBedrooms) {
  this.numBedrooms = numBedrooms;
}

// Only change code below this line
const myHouse = new House(3);

myHouse instanceof House 
```

### - Understand Own Properties

Add the own properties of canary to the array ownProps.

```
function Bird(name) {
  this.name = name;
  this.numLegs = 2;
}

let canary = new Bird("Tweety");
let ownProps = [];
// Only change code below this line
for (let prop in canary) {
  if(canary.hasOwnProperty(prop)) {
    ownProps.push(prop)
  }
}
```

`name` and `numLegs` are called own properties, because they are defined directly on the instance object. That means that `canary` has its own separate copy of these properties. In fact every instance of `Bird` will have its own copy of these properties

### - Use Prototype Properties to Reduce Duplicate Code

Add a numLegs property to the prototype of Dog

```
function Dog(name) {
  this.name = name;
}


Dog.prototype.numLegs = 2
// Only change code above this line
let beagle = new Dog("Snoopy");
```

### - Iterate Over All Properties

Add all of the own properties of beagle to the array ownProps. Add all of the prototype properties of Dog to the array prototypeProps.

```
function Dog(name) {
  this.name = name;
}

Dog.prototype.numLegs = 4;

let beagle = new Dog("Snoopy");

let ownProps = [];
let prototypeProps = [];

// Only change code below this line
for (let prop in beagle) {
  if(beagle.hasOwnProperty(prop)) {
    ownProps.push(prop)
  } else {
    prototypeProps.push(prop)
  }
}
```

### - Understand the Constructor Property

Write a joinDogFraternity function that takes a candidate parameter and, using the constructor property, return true if the candidate is a Dog, otherwise return false.

```
function Dog(name) {
  this.name = name;
}

// Only change code below this line
function joinDogFraternity(candidate) {
  if (candidate.constructor === Dog) {
    return true
  } else {
    return false
  }
}
```

### - Change the Prototype to a New Object
