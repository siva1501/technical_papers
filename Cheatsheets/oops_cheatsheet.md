# Python OOPs Cheat Sheet

A beginner-friendly reference for Object-Oriented Programming (OOP) in
Python.

## 1. What is OOP?

**OOP (Object-Oriented Programming)** is a way of writing programs by
organizing code into **classes** and **objects**.

It helps us: - Reuse code. - Organize related data and behaviour. -
Maintain and extend programs more easily.

The four main pillars of OOP are: 1. Encapsulation 2. Inheritance 3.
Polymorphism 4. Abstraction

## 2. Class

A **class** is a blueprint used to create objects. It defines the data
and behaviour that its objects can have.

``` python
class Student:
    college = "MTIST"
```

## 3. Object

An **object** is an instance of a class.

``` python
class Student:
    college = "MTIST"

student1 = Student()
print(student1.college)
```

Output:

``` text
MTIST
```

`student1` is an object of the `Student` class.

## 4. Constructor: `__init__()`

`__init__()` is a special method that Python calls automatically when a
new object is created. It is commonly used to initialize an object's
attributes.

``` python
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

student1 = Student("Siva", 22)

print(student1.name)
print(student1.age)
```

Output:

``` text
Siva
22
```

**Remember:** `__init__()` initializes an object; it is not technically
the method that creates the object. Object creation is handled by
`__new__()`.

## 5. The `self` Parameter

`self` refers to the current object. It lets an instance method access
or update that object's attributes and call its other methods.

``` python
class Student:
    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)

student1 = Student("Siva")
student1.display()
```

`self` is a naming convention, but it is strongly recommended. Python
passes the current object automatically when an instance method is
called through an object.

## 6. Attributes: Instance Variables and Class Variables

### Instance variables

Instance variables belong to an individual object. Different objects can
have different values.

``` python
class Student:
    def __init__(self, name):
        self.name = name

student1 = Student("Siva")
student2 = Student("Ravi")

print(student1.name)  # Siva
print(student2.name)  # Ravi
```

### Class variables

Class variables are defined in the class body and are shared through the
class by its instances, unless an instance shadows the name with its own
attribute.

``` python
class Student:
    college = "MTIST"

    def __init__(self, name):
        self.name = name

student1 = Student("Siva")
student2 = Student("Ravi")

print(student1.college)
print(student2.college)
```

### Difference

  Instance variable              Class variable
  ------------------------------ ---------------------------
  Belongs to an object           Belongs to the class
  Usually defined using `self`   Defined in the class body
  Can differ between objects     Shared through the class
  Example: `self.name`           Example: `college`

## 7. Methods in Python Classes

### Instance method

Works with an object's data. Its first parameter is conventionally
`self`.

``` python
class Student:
    def __init__(self, name):
        self.name = name

    def display(self):
        print(self.name)

student = Student("Siva")
student.display()
```

### Class method

Works with class-level data. It uses `@classmethod` and receives the
class as `cls`.

``` python
class Student:
    college = "MTIST"

    @classmethod
    def change_college(cls, new_college):
        cls.college = new_college

Student.change_college("ABC College")
print(Student.college)
```

### Static method

A utility function placed inside a class because it is related to that
class. It does not automatically receive `self` or `cls`.

``` python
class Calculator:
    @staticmethod
    def add(first_number, second_number):
        return first_number + second_number

print(Calculator.add(10, 20))
```

### Quick comparison

  -----------------------------------------------------------------------
  Method type             First parameter         Typical use
  ----------------------- ----------------------- -----------------------
  Instance method         `self`                  Work with object data

  Class method            `cls`                   Work with class data or
                                                  provide alternative
                                                  constructors

  Static method           No automatic first      Related utility
                          parameter               operation
  -----------------------------------------------------------------------

## 8. The Four Pillars of OOP

### 8.1 Encapsulation

**Encapsulation** means keeping related data and methods together in a
class and controlling how the data is accessed or changed.

Python naming conventions:

  -----------------------------------------------------------------------
  Style                   Example                 Meaning
  ----------------------- ----------------------- -----------------------
  Public                  `name`                  Can be accessed
                                                  normally

  Protected convention    `_name`                 Intended for internal
                                                  or subclass use

  Private name-mangled    `__name`                Python changes the
                                                  attribute name to
                                                  reduce accidental
                                                  access
  -----------------------------------------------------------------------

Example:

``` python
class BankAccount:
    def __init__(self, balance):
        self.__balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount

    def get_balance(self):
        return self.__balance

account = BankAccount(1000)
account.deposit(500)
print(account.get_balance())
```

Output:

``` text
1500
```

**Note:** Python's double underscore does not create absolute security.
It performs name mangling.

### 8.2 Inheritance

**Inheritance** allows a child class to reuse and extend the attributes
and methods of a parent class.

-   Parent class: base class.
-   Child class: derived class.

``` python
class Animal:
    def eat(self):
        print("Eating")

class Dog(Animal):
    def bark(self):
        print("Barking")

dog = Dog()
dog.eat()
dog.bark()
```

Output:

``` text
Eating
Barking
```

#### Types of inheritance

1.  **Single inheritance:** One child inherits from one parent.
2.  **Multiple inheritance:** One child inherits from more than one
    parent.
3.  **Multilevel inheritance:** A class inherits from a child class,
    forming a chain.
4.  **Hierarchical inheritance:** Multiple child classes inherit from
    one parent.
5.  **Hybrid inheritance:** A combination of inheritance types.

### 8.3 Polymorphism

**Polymorphism** means that the same method name or interface can behave
differently for different objects.

``` python
class Dog:
    def sound(self):
        print("Bark")

class Cat:
    def sound(self):
        print("Meow")

animals = [Dog(), Cat()]

for animal in animals:
    animal.sound()
```

Output:

``` text
Bark
Meow
```

Python also supports polymorphism through inheritance and method
overriding.

### 8.4 Abstraction

**Abstraction** means exposing essential operations while hiding
implementation details.

Python provides the `abc` module to define abstract base classes.

``` python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        print("Bark")

dog = Dog()
dog.sound()
```

A class with an unimplemented abstract method cannot normally be
instantiated. A concrete child class must implement the required
abstract methods.

## 9. Method Overriding

**Method overriding** happens when a child class provides its own
implementation of a method defined by its parent class.

``` python
class Animal:
    def sound(self):
        print("Some animal sound")

class Dog(Animal):
    def sound(self):
        print("Bark")

dog = Dog()
dog.sound()
```

Output:

``` text
Bark
```

## 10. Method Overloading in Python

Traditional method overloading means defining multiple methods with the
same name but different parameter lists. Python does not support this
form of overloading directly: a later method definition replaces an
earlier one.

You can often achieve similar behaviour with default arguments or
flexible arguments.

``` python
class Calculator:
    def add(self, first_number, second_number, third_number=0):
        return first_number + second_number + third_number

calculator = Calculator()

print(calculator.add(10, 20))
print(calculator.add(10, 20, 30))
```

Output:

``` text
30
60
```

## 11. The `super()` Function

`super()` provides access to methods in the next class in the method
resolution order (MRO). It is commonly used to call a parent class's
initializer or method.

``` python
class Parent:
    def __init__(self):
        print("Parent constructor")

class Child(Parent):
    def __init__(self):
        super().__init__()
        print("Child constructor")

child = Child()
```

Output:

``` text
Parent constructor
Child constructor
```

## 12. Composition

**Composition** means building a class using objects of other classes.
It represents a "has-a" relationship.

``` python
class Engine:
    def start(self):
        print("Engine started")

class Car:
    def __init__(self):
        self.engine = Engine()

    def start(self):
        self.engine.start()

car = Car()
car.start()
```

A car **has an** engine.

### Inheritance vs Composition

  -----------------------------------------------------------------------
  Inheritance                         Composition
  ----------------------------------- -----------------------------------
  Represents an "is-a" relationship   Represents a "has-a" relationship

  Child reuses or specializes parent  One object uses another object
  behaviour                           

  Example: `Dog` is an `Animal`       Example: `Car` has an `Engine`
  -----------------------------------------------------------------------

## 13. Magic (Dunder) Methods

Magic methods are special methods whose names begin and end with double
underscores. Python calls them for operations such as object creation,
printing, comparison, and arithmetic.

  Method         Purpose
  -------------- --------------------------------------
  `__init__()`   Initialize a new object's attributes
  `__str__()`    Human-readable string representation
  `__repr__()`   Developer-oriented representation
  `__len__()`    Behaviour for `len(object)`
  `__add__()`    Behaviour for `object1 + object2`
  `__eq__()`     Behaviour for `object1 == object2`
  `__del__()`    Finalizer; timing is not guaranteed

Example:

``` python
class Student:
    def __init__(self, name):
        self.name = name

    def __str__(self):
        return self.name

student = Student("Siva")
print(student)
```

Output:

``` text
Siva
```

## 14. Property Decorator

`@property` lets you access a method like an attribute. It is useful for
validating or controlling attribute access.

``` python
class Student:
    def __init__(self, marks):
        self._marks = marks

    @property
    def marks(self):
        return self._marks

    @marks.setter
    def marks(self, new_marks):
        if 0 <= new_marks <= 100:
            self._marks = new_marks
        else:
            raise ValueError("Marks must be between 0 and 100")

student = Student(80)
student.marks = 90
print(student.marks)
```

## 15. SOLID Principles

SOLID is a group of five principles for designing maintainable
object-oriented software.

  -----------------------------------------------------------------------
  Letter                  Principle               Simple meaning
  ----------------------- ----------------------- -----------------------
  S                       Single Responsibility   A class should have one
                          Principle               clear responsibility.

  O                       Open/Closed Principle   Software should be open
                                                  for extension but
                                                  closed for
                                                  modification.

  L                       Liskov Substitution     A child object should
                          Principle               be usable wherever its
                                                  parent type is expected
                                                  without breaking
                                                  correct behaviour.

  I                       Interface Segregation   Prefer small, focused
                          Principle               interfaces over large
                                                  interfaces that force
                                                  unused methods.

  D                       Dependency Inversion    High-level logic should
                          Principle               depend on abstractions,
                                                  not directly on
                                                  low-level details.
  -----------------------------------------------------------------------

## 16. Useful OOP Vocabulary

  -----------------------------------------------------------------------
  Term                                Meaning
  ----------------------------------- -----------------------------------
  Class                               Blueprint for creating objects

  Object                              Instance of a class

  Attribute                           Data stored on an object or class

  Method                              Function defined in a class

  Instance                            An object created from a class

  Constructor / initializer           Common term for setup performed by
                                      `__init__()`

  Parent class                        Class being inherited from

  Child class                         Class that inherits from another
                                      class

  Override                            Replace inherited method behaviour
                                      in a child class

  MRO                                 Method Resolution Order; the order
                                      Python follows to look up methods

  Interface                           A description of operations an
                                      object should provide
  -----------------------------------------------------------------------




## Quick Revision

-   **Class:** Blueprint.
-   **Object:** Instance of a class.
-   **`self`:** Current object.
-   **`__init__()`:** Initializes object attributes.
-   **Encapsulation:** Keep data and related methods together; control
    access.
-   **Inheritance:** Reuse and extend another class.
-   **Polymorphism:** Same interface, different behaviour.
-   **Abstraction:** Expose essential operations and hide implementation
    details.
-   **Composition:** Build a class using other objects.
-   **`super()`:** Access the next implementation in the MRO.
