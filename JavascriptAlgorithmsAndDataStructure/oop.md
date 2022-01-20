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
