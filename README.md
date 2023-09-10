# **Object-Oriented Programming (OOP)**

## Introduction to Object-Oriented Programming 
In python, there are mainly two approaches that are used to write programs:
1. Procedural Programming
2. Object-Oriented Programming (OOP)

Till now, we have followed Procedural Programming for example defining function, making loigcal statements using 
If-Else, Looping etc. 

Procedural Programming is about writing procedures of functions that perform operations on data, while Object- Oriented Programming is about creating objects that contains both, data and function. 

* OOP is a programming paradigm that organizes code into objects, which are instances of <span style = "color:red;">
classes</span>. 
* Its significance lies in promoting modularity, reusability, and a clear structure for managing and 
manipulating data. 
* It helps model real-world concepts more naturally in code. 
* Imagine you're creating a program to manage a library. You can use OOP to model the objects in your program, such as 
Book, Library, and Member, making your code more organized and intuitive. 
* Basic concept of OOP in Python is to use classes and objects to represent real-world concepts and entities.

## Class
* A class is like a blueprint or template for creating ***objects***. 
* It defines the properties (attributes) and methods that a class will have. 
* **Methods** are actions that can be performed by an object whereas, **Attributes** are traits of that object. 
* To create a class, use the <span style="color:red; background-color: lightgray;">class</span> keyword.
* Example: A <span style="color: red; background-color: lightgray;">class</span> Fruit can contain objects like 
  *Apple, Banana, Mango* etc.
* So a class is a template of object and an object is an instance of class. 
* When individual objects are created, they inherit all variable and functions from that class. 
```commandline
class Mycar:
    def __init__(self,make,car,model,displacement):
        self.make = make
        self.car = car
        self.model = model
        self.displacement = displacement
# When creating an instance of the class, you should pass the values as arguments to the constructor, 
not directly in the class definition.        
Car1 = Mycar(2023,"Mercedes","Benz 7","2800cc")
print(Mycar)
print(f'''The car I got for myself is {Car1.car}. It has an Engine Displacement of {Car1.displacement}. It was made 
in {Car1.make} and the model is {Car1.model}''')
```
**Note** : In Python, it's a convention (not a rule) to name classes using CamelCase,
which means starting with an uppercase letter.

### Reasons of When to Create a <span style="color: red; background-color: lightgrey;">class</span>

1. **Abstraction**: Classes allow you to abstract complex real-world concepts into code. For example, you can create a 
Car class to model cars in your program, encapsulating their attributes and behaviors.
```commandline
class Car:
    def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year

    def start_engine(self):
        print(f"{self.make} {self.model}'s engine started.")

    def stop_engine(self):
        print(f"{self.make} {self.model}'s engine stopped.")
```
2. **Code Reusability**: Classes enable you to define reusable templates for objects. You can create multiple `Car` 
objects with the same attributes and methods.
```commandline
car1 = Car("Toyota", "Camry", 2022)
car2 = Car("Honda", "Civic", 2023)
```
3. **Encapsulation***:  Classes encapsulate data (attributes) and behavior (methods) into a single unit, making it 
easier to manage and understand your code.
4. **Organization**: Classes help organize your code by grouping related data and functions together. 
This improves code readability and maintainability.
5. **Inheritance**: You can use classes to create hierarchies and relationships between objects. For example, you can 
have a base class `Vehicle` with subclasses like `Car`, `Motorcycle`, and `Truck`, inheriting common properties and behaviors.

### When not to Use <span style="color: red; background-color: lightgrey;">class</span>

Classes should be avoided when:
1. Our codes are very **simple**
2. We are performing **Procedural Programming**
3. Creating unnecessary classes can cause overheads which hinders **Performance**.
4. Avoid creating classes just for the sake of OOP if it does not make code clear and more readable. Avoid 
   **Overengineering**

## Create Object 
* After a class has been named, we can use it to create an object. 
```commandline
 In Continuation of Above Example
# Creating objects of the class
dog1 = Dog("Buddy", "Golden Retriever")
dog2 = Dog("Rex", "German Shepherd")
```
## Dunders (Double Underscores __) 
* Double underscores, also known as "dunders," are used to create special methods and attributes in Python classes. 
* They are not limited to classes but are often associated with them. For example, **__ init __** is a special method used for initializing objects. 
```commandline
class Dog:
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed

    def __str__(self):
        return f"{self.name} is a {self.breed}."

dog1 = Dog("Buddy", "Golden Retriever")
print(str(dog1))  # Outputs: "Buddy is a Golden Retriever."
```
## The <span style="color: red;">Self</span> Parameter
* The `self` parameter is used to access and modify object attributes within the class methods.
```commandline
class Dog:
    def __init__(self, name, breed):
        self.name = name
        self.breed = breed

    def bark(self):
        return f"{self.name} barks!"

dog1 = Dog("Buddy", "Golden Retriever")
print(dog1.bark())  # Outputs: "Buddy barks!"
```
* However, it does not have be named <span style="color: red;">self</span>, you can call it by whatever name BUT 
  **has to be first parameter of any function**.   
```commandline
class Person:
  def __init__(mysillyobject, name, age):
    mysillyobject.name = name
    mysillyobject.age = age

  def myfunc(abc):
    print("Hello my name is " + abc.name)

p1 = Person("John", 36)
p1.myfunc()
```
## Special Methods
Python supports special methods which are:
1. **__ init __()**: This is the constructor method used to initialize object attributes.
    * **__ init __()** is a built-in function and all classes have a function called __ init __
    * This is always executed when a class is created. 
    * Use the __init__() function to assign values to object properties, or other operations that are necessary to do 
      when the object is being created 
```commandline
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)

print(p1.name)
print(p1.age)
```
**Note**: The __init__() function is called automatically every time the class is being used to create a new object.
2. **__ str __()**: 
   * This function controls what should be returned when the class object is represented with string
   * If __ str__() function is not set, the string representation of object is returned. 
String representation without __ str__() function:
```commandline
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

p1 = Person("John", 36)

print(p1)
```
String representation WITH __ str__() function:
```commandline
class Person:
  def __init__(self, name, age):
    self.name = name
    self.age = age

  def __str__(self):
    return f"{self.name}({self.age})"

p1 = Person("John", 36)

print(p1)
```
3. **__ main__()**:
   * This is not a commonly used special method in classes
   * Typically it is found **if __ name __ == "__ main__:"** in scripts to see if the script is being run directly

These described methods are the commonly used methods. To see a full list, check **Appendix A** at the end of this 
chapter.

## Constructors 

* Constructors like `__init__()` are used to initialize object attributes when an object is created. 
* They are called automatically when you create object of class. 
* You can create your own constructors by creating custom **__init__()** methods in your class.
  * In the examples above, The __init__ method in the `Dog` class serves as a constructor, initializing the `name` and 
  `breed` attributes when a new `Dog` object is created.


# <span style="color: blue;">Appendix - A</span>: Special Methods/Magic Methods/Dunder Methods

Besides **__ init __**, **__ str __** and **__ main __** there are many more Special/Dunder/Magic methods:
These methods enable you to define custom behavior for various operations on objects of your classes. 
Here are some commonly used special methods:
1. `__init__(self, ...)`: The constructor method, called when an object is created from a class.
2. `__repr__(self)`: Returns an "official" string representation of the object, typically used for debugging.
3. `__eq__(self, other)`: Defines the behavior of the equality operator ==.
4. `__lt__(self, other)`: Defines the behavior of the less-than operator <.
5. `__le__(self, other)`: Defines the behavior of the less-than-or-equal-to operator <=.
6. `__gt__(self, other)`: Defines the behavior of the greater-than operator >.
7. `__ge__(self, other)`: Defines the behavior of the greater-than-or-equal-to operator >=.
8. `__ne__(self, other)`: Defines the behavior of the not-equal-to operator !=.
9. `__len__(self)`: Returns the length of the object when len(object) is called.
10. `__getitem__(self, key)`: Enables indexing of objects, like `object[key]`.
11. `__setitem__(self, key, value)`: Enables setting values using indexing, like `object[key] = value`.
12. `__delitem__(self, key)`: Enables deleting items using indexing, like del `object[key]`.
13. `__iter__(self)`: Returns an iterator object for the class, allowing iteration over the object.
14. `__next__(self)`: Defines the behavior when using the next() function with an iterator.
15. `__contains__(self, item)`: Defines the behavior of the in operator, like item in object.
16. `__call__(self, ...)`: Allows you to call an object as if it were a function.
17. `__enter__(self)`: Used for context management (with statement).
18. `__exit__(self, exc_type, exc_value, traceback)`: Used for context management (with statement).
19. `__add__(self, other)`: Defines the behavior of the addition operator +.
20. `__sub__(self, other)`: Defines the behavior of the subtraction operator -.
21. `__mul__(self, other)`: Defines the behavior of the multiplication operator *.
22. `__truediv__(self, other)`: Defines the behavior of the division operator /.
23. `__floordiv__(self, other)`: Defines the behavior of the floor division operator //.
24. `__mod__(self, other)`: Defines the behavior of the modulo operator %.
25. `__pow__(self, other, modulo=None)`: Defines the behavior of the exponentiation operator **.
