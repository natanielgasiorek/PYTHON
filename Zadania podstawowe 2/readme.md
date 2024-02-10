```
#1.
import math

class Triangle:
    def __init__(self, base, height):
        if base <= 0 or height <= 0:
            raise ValueError("Both base and height must be positive values.")
        self.base = base
        self.height = height
        self.name = "Triangle"

    def calculate_area(self):
        return 0.5 * self.base * self.height

    def calculate_perimeter(self):
        return 2 * self.base + math.sqrt(2) * self.height

    def display_name(self):
        print("Figure:", self.name)


class Rectangle:
    def __init__(self, length, width):
        if length <= 0 or width <= 0:
            raise ValueError("Both length and width must be positive values.")
        self.length = length
        self.width = width
        self.name = "Rectangle"

    def calculate_area(self):
        return self.length * self.width

    def calculate_perimeter(self):
        return 2 * (self.length + self.width)

    def display_name(self):
        print("Figure:", self.name)


class Circle:
    def __init__(self, radius):
        if radius <= 0:
            raise ValueError("Radius must be a positive value.")
        self.radius = radius
        self.name = "Circle"

    def calculate_area(self):
        return math.pi * self.radius**2

    def calculate_perimeter(self):
        return 2 * math.pi * self.radius

    def display_name(self):
        print("Figure:", self.name)
```
```
#2.
class Turtle:
    def __init__(self, name, speed):
        self.name = name
        self.speed = speed
        self.__x = 0
    def say_name(self):
        print(f"Hello, I'm {self.name} the turtle, and my speed is {self.speed} units per second.")

    def move(self, distance):
        self.__x += distance

    def get_position(self):
        return self.__x
```
```
#3.
class Employee:
    def __init__(self, employee_id, name, position, salary):
        self.employee_id = employee_id
        self.name = name
        self.position = position
        self.salary = salary

    def display_info(self):
        print(f"Employee ID: {self.employee_id}")
        print(f"Name: {self.name}")
        print(f"Position: {self.position}")
        print(f"Salary: ${self.salary}")

    def promote(self, new_position, salary_increase):
        self.position = new_position
        self.salary += salary_increase
        print(f"{self.name} has been promoted to {new_position} with a salary increase of ${salary_increase}.")

    def work(self):
        print(f"{self.name} is working.")

class Monster:
    def __init__(self, name, health, damage):
        self.name = name
        self.health = health
        self.damage = damage

    def display_info(self):
        print(f"Monster: {self.name}")
        print(f"Health: {self.health}")
        print(f"Damage: {self.damage}")

    def attack(self, target):
        print(f"{self.name} attacks {target} for {self.damage} damage.")
        target.take_damage(self.damage)

    def take_damage(self, amount):
        self.health -= amount
        print(f"{self.name} takes {amount} damage. Current health: {self.health}")

class Refrigerator:
    def __init__(self, brand, model, capacity_liters):
        self.brand = brand
        self.model = model
        self.capacity_liters = capacity_liters
        self.contents = []

    def display_info(self):
        print(f"Refrigerator: {self.brand} {self.model}")
        print(f"Capacity: {self.capacity_liters} liters")
        print(f"Contents: {', '.join(self.contents)}")

    def add_item(self, item):
        self.contents.append(item)
        print(f"Added {item} to the refrigerator.")

    def remove_item(self, item):
        if item in self.contents:
            self.contents.remove(item)
            print(f"Removed {item} from the refrigerator.")
        else:
            print(f"{item} not found in the refrigerator.")
```
```
#4.

class Bird:
    def __init__(self, specie, colour,):
        self._specie = specie  
        self._colour = colour


    def info(self):
        print(f"specie: {self._specie}")
        print(f"colour: {self._colour}")
    def latanie(self):
        print(f"{self._specie} is flying.")


class BirdA(Bird):
    def __init__(self, colour, spiew):
        super().__init__(specie="BirdA", colour=colour)
        self.__spiew = spiew  
    def sing(self):
        print(f"{self._specie} sing: {self.__spiew}")


class BirdB(Bird):
    def __init__(self, colour, flight_speed):
        super().__init__(specie="BirdB", colour=colour,)
        self.__flight_speed = flight_speed

    def flight_speed(self):
        print(f"{self._specie} flies: {self.__flight_speed} km/h")
```
