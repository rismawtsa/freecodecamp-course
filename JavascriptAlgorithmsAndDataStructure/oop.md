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


Add the property numLegs and the two methods eat() and describe() to the prototype of Dog by setting the prototype to a new object.

```
function Dog(name) {
  this.name = name;
}

Dog.prototype = {
  // Only change code below this line
  numLegs: 4,
  eat: function() {
    console.log("eat");
  },
  describe: function() {
    console.log("describe")
  }
};
```

> A more efficient way is to set the prototype to a new object that already contains the properties. This way, the properties are added all at once:

### -  Remember to Set the Constructor Property when Changing the Prototype

There is one crucial side effect of manually setting the prototype to a new object. It erases the constructor property! This property can be used to check which constructor function created the instance, but since the property has been overwritten, it now gives false results:

```
duck.constructor === Bird;
duck.constructor === Object;
duck instanceof Bird;
```

In order, these expressions would evaluate to false, true, and true.

**Instruction**

Define the constructor property on the Dog prototype.

```
function Dog(name) {
  this.name = name;
}

// Only change code below this line
Dog.prototype = {
  constructor: Dog,
  numLegs: 4,
  eat: function() {
    console.log("nom nom nom");
  },
  describe: function() {
    console.log("My name is " + this.name);
  }
};
```

### - Understand Where an Object’s Prototype Comes From

Just like people inherit genes from their parents, an object inherits its prototype directly from the constructor function that created it. For example, here the Bird constructor creates the duck object:

```
function Bird(name) {
  this.name = name;
}

let duck = new Bird("Donald");
```

duck inherits its prototype from the Bird constructor function. You can show this relationship with the isPrototypeOf method:

`Bird.prototype.isPrototypeOf(duck);`

This would return `true`.

**Instruction**

Use isPrototypeOf to check the prototype of beagle.

```
function Dog(name) {
  this.name = name;
}

let beagle = new Dog("Snoopy");

// Only change code below this line
Dog.prototype.isPrototypeOf(beagle)
```

### - Understand the Prototype Chain

All objects in JavaScript (with a few exceptions) have a prototype. Also, an object’s prototype itself is an object.

```
function Bird(name) {
  this.name = name;
}

typeof Bird.prototype;
```

Because a `prototype` is an `object`, a `prototype` can have its own `prototype`! In this case, the `prototype` of `Bird.prototype` is `Object.prototype`:

`Object.prototype.isPrototypeOf(Bird.prototype);`

How is this useful? You may recall the `hasOwnProperty` method from a previous challenge:

```
let duck = new Bird("Donald");
duck.hasOwnProperty("name");
```

The `hasOwnProperty` method is defined in `Object.prototype`, which can be accessed by `Bird.prototype`, which can then be accessed by `duck`. This is an example of the `prototype` chain. In this `prototyp`e chain, `Bird` is the `supertype` for `duck`, while `duck` is the `subtype`. `Object` is a `supertype` for both `Bird` and `duck`. `Object` is a `supertype` for all objects in JavaScript. Therefore, any object can use the `hasOwnProperty` method.

**Instruction**

Modify the code to show the correct prototype chain.

**Code**

```
function Dog(name) {
  this.name = name;
}

let beagle = new Dog("Snoopy");

Dog.prototype.isPrototypeOf(beagle);  // yields true

// Fix the code below so that it evaluates to true
Object.prototype.isPrototypeOf(Dog.prototype);
```

### - Use Inheritance So You Don't Repeat Yourself

The eat method is repeated in both Cat and Bear. Edit the code in the spirit of DRY (Dont Repeat Yourself) by moving the eat method to the Animal supertype.

```
function Cat(name) {
  this.name = name;
}

Cat.prototype = {
  constructor: Cat
};

function Bear(name) {
  this.name = name;
}

Bear.prototype = {
  constructor: Bear
};

function Animal() { }

Animal.prototype = {
  constructor: Animal,
  eat: function() {
    console.log("nom nom nom");
  }
};
```

### - Inherit Behaviors from a Supertype

In the previous challenge, you created a supertype called Animal that defined behaviors shared by all animals:

```
function Animal() { }
Animal.prototype.eat = function() {
  console.log("nom nom nom");
};
```

This and the next challenge will cover how to reuse the methods of `Animal` inside `Bird` and `Dog` without defining them again. It uses a technique called `inheritance`. This challenge covers the first step: make an instance of the `supertype` (or parent). You already know one way to create an instance of `Animal` using the new operator:

`let animal = new Animal();`

There are some disadvantages when using this syntax for inheritance, which are too complex for the scope of this challenge. Instead, here's an alternative approach without those disadvantages:

`let animal = Object.create(Animal.prototype);`

O`bject.create(obj)` creates a new object, and sets `obj` as the new object's prototype. Recall that the `prototype` is like the "recipe" for creating an object. By setting the `prototype` of `animal` to be the `prototype` of `Animal`, you are effectively giving the animal instance the same "recipe" as any other instance of `Animal`.

```
animal.eat();
animal instanceof Animal;
```

The instanceof method here would return true.

**Instruction**

Use `Object.create` to make two instances of `Animal` named `duck` and `beagle`.

**Code**

```
function Animal() { }

Animal.prototype = {
  constructor: Animal,
  eat: function() {
    console.log("nom nom nom");
  }
};

// Only change code below this line
let duck = Object.create(Animal.prototype); // Change this line
let beagle = Object.create(Animal.prototype); // Change this line
```

### - Set the Child's Prototype to an Instance of the Parent

In the previous challenge you saw the first step for inheriting behavior from the supertype (or parent) `Animal`: making a new instance of `Animal`.

This challenge covers the next step: set the `prototype` of the subtype (or child)—in this case, `Bird`—to be an instance of `Animal`.

`Bird.prototype = Object.create(Animal.prototype);`

Remember that the `prototype` is like the "recipe" for creating an object. In a way, the recipe for `Bird` now includes all the key "ingredients" from `Animal`.

```
let duck = new Bird("Donald");
duck.eat();
```

`duck` inherits all of `Animal`'s properties, including the eat method.

**Instruction**

Modify the code so that instances of Dog inherit from Animal.

**Code**

```
function Animal() { }

Animal.prototype = {
  constructor: Animal,
  eat: function() {
    console.log("nom nom nom");
  }
};

function Dog() { }

// Only change code below this line
Dog.prototype = Object.create(Animal.prototype)

let beagle = new Dog();
```

### - Reset an Inherited Constructor Property

When an object inherits its prototype from another object, it also inherits the supertype's constructor property.

Here's an example:

```
function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
let duck = new Bird();
console.log(duck.constructor) // output [Function: Animal]
```

But `duck` and all instances of `Bird` should show that they were constructed by `Bird` and not `Animal`. To do so, you can manually set the constructor property of `Bird` to the `Bird` object:

```
Bird.prototype.constructor = Bird;
duck.constructor
```

**Instruction**

Fix the code so duck.constructor and beagle.constructor return their respective constructors.

```
function Animal() { }
function Bird() { }
function Dog() { }

Bird.prototype = Object.create(Animal.prototype);
Dog.prototype = Object.create(Animal.prototype);

// Only change code below this line
Bird.prototype.constructor = Bird;
Dog.prototype.constructor = Dog;

let duck = new Bird();
let beagle = new Dog();

console.log(duck.constructor, beagle.constructor)
```

### - Add Methods After Inheritance

A constructor function that inherits its `prototype` object from a supertype constructor function can still have its own methods in addition to inherited methods.

For example, `Bird` is a constructor that inherits its `prototype` from `Animal`:

```
function Animal() { }
Animal.prototype.eat = function() {
  console.log("nom nom nom");
};
function Bird() { }
Bird.prototype = Object.create(Animal.prototype);
Bird.prototype.constructor = Bird;
```

In addition to what is inherited from `Animal`, you want to add behavior that is unique to `Bird` objects. Here, `Bird `will get a `fly()` function. Functions are added to `Bird`'s `prototype` the same way as any constructor function:

```
Bird.prototype.fly = function() {
  console.log("I'm flying!");
};
```

Now instances of `Bird` will have both `eat()` and `fly()` methods:

```
let duck = new Bird();
duck.eat();
duck.fly();
```

`duck.eat()` would display the string `nom nom nom` in the console, and `duck.fly()` would display the string `I'm flying!`.

**Instruction**

Add all necessary code so the `Dog` object inherits from `Animal` and the `Dog`'s `prototype` constructor is set to `Dog`. Then add a `bark()` method to the `Dog` object so that `beagle` can both `eat()` and `bark()`. The `bark()` method should print `Woof!` to the console.

```
function Animal() { }
Animal.prototype.eat = function() { console.log("nom nom nom"); };

function Dog() { }

// Only change code below this line
Dog.prototype = Object.create(Animal.prototype)
Dog.prototype.constructor = Dog;
Dog.prototype.bark = function() {
  console.log('Woof!')
}


// Only change code above this line

let beagle = new Dog();
```

### - Override Inherited Methods

In previous lessons, you learned that an object can inherit its behavior (methods) from another object by referencing its `prototype` object:

`ChildObject.prototype = Object.create(ParentObject.prototype);`

Then the `ChildObject` received its own methods by chaining them onto its `prototype`:

`ChildObject.prototype.methodName = function() {...};`

It's possible to override an inherited method. It's done the same way - by adding a method to `ChildObject.prototype` using the same method name as the one to override. Here's an example of `Bird` overriding the `eat()` method inherited from `Animal`:

```
function Animal() { }
Animal.prototype.eat = function() {
  return "nom nom nom";
};
function Bird() { }

Bird.prototype = Object.create(Animal.prototype);

Bird.prototype.eat = function() {
  return "peck peck peck";
};
```

If you have an instance `let duck = new Bird();` and you call `duck.eat()`, this is how JavaScript looks for the method on the `prototype` chain of `duck`:

duck => Is `eat()` defined here? No.
Bird => Is `eat()` defined here? => Yes. Execute it and stop searching.
Animal => `eat()` is also defined, but JavaScript stopped searching before reaching this level.
Object => JavaScript stopped searching before reaching this level.

**Instruction**

Override the `fly()` method for `Penguin` so that it returns the string `Alas, this is a flightless bird`.

```
function Bird() { }

Bird.prototype.fly = function() { return "I am flying!"; };

function Penguin() { }
Penguin.prototype = Object.create(Bird.prototype);
Penguin.prototype.constructor = Penguin;

// Only change code below this line
Penguin.prototype.fly = function() {
  return "Alas, this is a flightless bird."
}


// Only change code above this line

let penguin = new Penguin();
console.log(penguin.fly());
```

### - Use a Mixin to Add Common Behavior Between Unrelated Objects

As you have seen, behavior is shared through inheritance. However, there are cases when inheritance is not the best solution. Inheritance does not work well for unrelated objects like `Bird` and `Airplane`. They can both `fly`, but a `Bird` is not a type of `Airplane` and vice versa.

For unrelated objects, it's better to use *mixins*. A *mixin* allows other objects to use a collection of functions.

```
let flyMixin = function(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  }
};
```

The `flyMixin` takes any object and gives it the fly method.

```
let bird = {
  name: "Donald",
  numLegs: 2
};

let plane = {
  model: "777",
  numPassengers: 524
};

flyMixin(bird);
flyMixin(plane);
```

Here `bird` and `plane` are passed into `flyMixin`, which then assigns the `fly` function to each object. Now `bird` and `plane` can both `fly`:

```
bird.fly();
plane.fly();
```

The console would display the string `Flying, wooosh!` twice, once for each `.fly()` call.

> Note how the *mixin* allows for the same `fly` method to be reused by unrelated objects `bird` and `plane`.

**Instruction**

Create a mixin named glideMixin that defines a method named glide. Then use the glideMixin to give both bird and boat the ability to glide.

```
let bird = {
  name: "Donald",
  numLegs: 2
};

let boat = {
  name: "Warrior",
  type: "race-boat"
};

// Only change code below this line
function glideMixin(obj) {
  return obj.glide = function() {
    console.log('glide')
  }
}

glideMixin(boat);
glideMixin(bird)
```

### - Use Closure to Protect Properties Within an Object from Being Modified Externally

In the previous challenge, `bir`d had a public property name. It is considered public because it can be accessed and changed outside of `bird`'s definition.

`bird.name = "Duffy";`

Therefore, any part of your code can easily change the name of `bird` to any value. Think about things like passwords and bank accounts being easily changeable by any part of your codebase. That could cause a lot of issues.

The simplest way to make this public property private is by creating a variable within the constructor function. This changes the scope of that variable to be within the constructor function versus available globally. This way, the variable can only be accessed and changed by methods also within the constructor function.

```
function Bird() {
  let hatchedEgg = 10;

  this.getHatchedEggCount = function() { 
    return hatchedEgg;
  };
}
let ducky = new Bird();
ducky.getHatchedEggCount();
```

Here `getHatchedEggCount` is a privileged method, because it has access to the private variable `hatchedEgg`. This is possible because `hatchedEgg` is declared in the same context as `getHatchedEggCount`. In JavaScript, a function always has access to the context in which it was created. This is called `closure`.

**Instruction**

Change how `weight` is declared in the `Bird` function so it is a private variable. Then, create a method `getWeight` that returns the value of weight `15`.

```
function Bird() {
  let weight = 15;

  this.getWeight = function() {
    return weight;
  }
}
```

### - Understand the Immediately Invoked Function Expression (IIFE)

A common pattern in JavaScript is to execute a function as soon as it is declared:

```
(function () {
  console.log("Chirp, chirp!");
})();
```

This is an anonymous function expression that executes right away, and outputs Chirp, chirp! immediately.

Note that the function has no name and is not stored in a variable. The two parentheses () at the end of the function expression cause it to be immediately executed or invoked. This pattern is known as an *immediately invoked function expression* or IIFE.

**Instruction**

Rewrite the function makeNest and remove its call so instead it's an anonymous immediately invoked function expression (IIFE).

```
(function() {
  console.log("A cozy nest is ready");
})()
```

### - Use an IIFE to Create a Module

An immediately invoked function expression (IIFE) is often used to group related functionality into a single object or module. For example, an earlier challenge defined two mixins:

```
function glideMixin(obj) {
  obj.glide = function() {
    console.log("Gliding on the water");
  };
}
function flyMixin(obj) {
  obj.fly = function() {
    console.log("Flying, wooosh!");
  };
}
```

We can group these mixins into a module as follows:

```
let motionModule = (function () {
  return {
    glideMixin: function(obj) {
      obj.glide = function() {
        console.log("Gliding on the water");
      };
    },
    flyMixin: function(obj) {
      obj.fly = function() {
        console.log("Flying, wooosh!");
      };
    }
  }
})();
```

> Note that you have an immediately invoked function expression (IIFE) that returns an object `motionModule`. This returned object contains all of the *mixin*
> behaviors as properties of the object. The advantage of the module pattern is that all of the motion behaviors can be packaged into a single object that can then
> be used by other parts of your code. Here is an example using it:

```
motionModule.glideMixin(duck);
duck.glide();
```

**Instruction** 

Create a module named funModule to wrap the two mixins isCuteMixin and singMixin. funModule should return an object.

```
let funModule = (function() {
  return {
  isCuteMixin: function(obj) {
    obj.isCute = function() {
      return true;
    };
  },
  singMixin: function(obj) {
      obj.sing = function() {
        console.log("Singing to an awesome tune");
      };
    }
  }
})()
```

