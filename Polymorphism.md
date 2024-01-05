
__Polymorphism__ is a fundamental concept in object-oriented programming (OOP) that allows objects to be treated as instances of their parent class, even when they are instances of a subclass. It enables a single interface to represent different types or forms.

There are two main types of polymorphism in OOP:

__Compile-time Polymorphism (Method Overloading):__ This occurs when there are multiple methods in the same class with the same name but different parameters.

__Runtime Polymorphism (Method Overriding):__ This occurs when a method in a subclass has the same signature as a method in its superclass. The actual method that gets executed is determined at runtime based on the type of the object.

```python
class Parent:
    def __init__(self, name):
        self.name = name
    
    def display(self):
        print(f'Name: {self.name}')

class Child(Parent):  # Corrected class name to start with a capital letter
    def __init__(self, name, age):  # Added 'name' parameter to Child's constructor
        super().__init__(name)  # Used super() to call the parent class constructor
        self.age = age
    
    def display(self):
        print(f'Name: {self.name}, Age: {self.age}')

obj1 = Parent('Ram')
obj2 = Child('Shyam', 23)  # Provided 'name' parameter for the Child object

obj1.display()
obj2.display()
```

__Another Example:__      
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

class Rectangle(Shape):
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return self.length * self.width

class Triangle(Shape):
    def __init__(self, base, height):
        self.base = base
        self.height = height

    def area(self):
        return 0.5 * self.base * self.height

# Create instances of different shapes
circle = Circle(radius=5)
rectangle = Rectangle(length=4, width=3)
triangle = Triangle(base=5, height=2)

# Use a common interface for different shapes
shapes = [circle, rectangle, triangle]

for shape in shapes:
    print(f"Area of {shape.__class__.__name__}: {shape.area()}")
```
