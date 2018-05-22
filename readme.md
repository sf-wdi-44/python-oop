# Intro to Object-Oriented Programming in Python

## Learning Objectives

- Review the principles of Object Oriented Programming
- Describe the relationship between a **class** and an **instance**
- Define a Python Class and **instantiate** it
- Distinguish between **local**, **instance**, and **class** variables
- Interact with objects through methods
- Explain inheritance in Python
- Look at Python's **"magic methods"** or **dunder methods**

## Framing: Review, why OOP?

### Objects are Intuitive!

Objects help us build programs that model how we tend to think about the world.
Human minds tend to break down the world into objects: trees, leaves, roads,
desks, cars, tacos, Britney Spears songs, and so on (all the *things*). Since 
it is our  natural mental tendency to understand the world in terms of objects,
 this is very useful for *modelling* things in the real world in our programs.

Instead of a bunch of variables and functions (procedural style), we can group
relevant data and functions into objects, grouping related data and behavior
together. We think about them as individual, self-contained units. This 
grouping of properties (data) and methods is a kind of **encapsulation**.

### Objects Manage Complexity

Encapsulation is especially important as our programs get more and more 
complex. We can't keep all the code (and what it does) in our head at once.
Instead, we often want to only think about a portion of the code in a given
moment.

Objects help us organize and think about our programs. If I'm looking at code
for a Squad object, and I see it has associated *people*, and those people can
dance when the squad dances, I don't need to think about or see all the code
related to a person dancing. I can just think at a high level "ok, when a squad
dances, all it's associated people dance". This is a form of *abstraction*... I
don't need to think about the details, just what's happening at a high-level.

### Ensuring Consistency

Another advantage of *encapsulation* (grouping data and methods into objects) 
is that these objects can be in control of their data. This usually means 
ensuring consistency of their data.

Consider the bank account example... I might define a bank account object
such that you can't directly change it's balance. Instead, you have to use the
`withdraw` and `deposit` methods. Those methods are the **interface** to the
account, and they can enforce rules for consistency, such as "balance can't be
less than zero".

### Modularity

Objects should stand on their own and play well with others. If our objects
are well-designed, then they interact with each other in well-defined ways.
This allows us to refactor (rewrite) any object, and it should not impact
(cause bugs) in other areas of our programs.

## OOP Syntax: JavaScript vs. Python

In JavaScript, we could write this class...

```js
class User {
  constructor (name) {
    this.name = name
  }

  greet () {
    console.log(`Hi! My name is ${this.name}.`)
  }
}

const me = new User('John')
me.greet()
```

Let's have a look at what this might look like in Python...

```bash
$ ipython
```

> You may have to run `pip install ipython` if you see error messages about it not being installed.

```py
class User:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f'Hi! My name is {self.name}')

me = User('John')
me.greet()
```

Let's break down this syntax. On the first line, we declare and name the class
-- this one is called `User`. A class declaration is always followed by a `:`.

Then, on the next line, we see a method called
`__init__`. The `__init__` method is the initializer -- for the purposes of this
class we will be using it like the `constructor` in JavaScript. We use it to set
the initial values of our instance's attributes. The `__init__` method takes two
parameters: `self` and `name`. By convention `self` is the first parameter to
each method in a Python class--`self` refers to the instance of the class, for
 example, a `User` object.

A particular `User` or instance of the `User` class will have a `name`
attribute that we will set in our `__init__` method. Finally, the `greet`
method displays a greeting formatted with the `User` instance's name. At the
end, we **instantiate** a new user with `me = User("John")`. 
