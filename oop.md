# Object Oriented Principles

## Inheritance - derive types to create more specialized behavior

Inheritance is one of the three primary characteristics of object-oriented programming. I think that was covered in the notes I took seven hours ago. The derived class inherits from the base class.
```
public class derived : base
```

I don't know what finalizers are but apparently they aren't inherited.

### Abstract and virtual methods

Both are inherited, virtual may be overridden, abstract has to be overriddenen.

### Abstract base classes

Abstract classes cannot be instantiated. If a class has an abstract member it must be declared abstract.

### Interfaces

Similar to an abstract class, except it only contains methods, and a derived class can benefit from any number of interfaces.

### Preventing further derivation

So THAT's what sealed does.

### Derived class hiding of base class members

Derived classes can conceal base class members by declaring members with the same name and signature.

## Abstract and Sealed Classes and Class Members

### Abstract Classes and Class Members

This was literally all review from the previous weeks reading. I'm liking that they capitalize words in their headings now though.

### Sealed Classes and Class Members

This can make some things run faster apparently.

## Polymorphism

Polymorphism is the third pillar of object-oriented programming. Did I miss the part where we covered encapsulation? Polymorphism has two aspects:
- At run time, objects of a derived class may be treated as objects of a base class in places such as method parameters and collections or arrays. When this polymorphism occurs, the object's declared type is no longer identical to its run-time type.
- Base classes may define and implement `virtual` methods, and derived classes can `override` them, wheich means they provide their own definition and implementation. At run-time, when client code calls the method, the CLR looks up the run-time type of the object, and invokes that override of the virtual method. In your source code you can call a method on a base class, and cause a derived class's version of the method to be executed.

If I had realized that was all about virtual classes I probably wouldn't have written it.

The `virtual` keyword lets you assign a default, which you can later use as is, incorporate, or override entirely.

## Object-Oriented programming

back to not capitalizing things I guess.

The four basic principles of object-oriented programming are:
- Abstraction: Modeling the relevant attributes and interactions of entities as classes to define an abstract representation of a system.
- Encapsulation: Hiding the internal state and functionality of an object and only allowing acces through a public set of functions.
- Inheritance: Ability to create new abstractions based on existing abstractions.
- Polymorphism: Ability to implement inherited properties or methods in different ways across multiple abstractions.

After this the entire page is a demo that implements all of the aforementioned OOP principles.

[<==Back](README.md)