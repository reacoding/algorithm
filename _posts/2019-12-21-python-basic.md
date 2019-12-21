---
title: "python 3 basic"
excerpt_separator: <!--more-->
last_modified_at: 2019-12-21T06:00:54-08:00
---
> Prepared for Programming, Python basic concept:
 1. Control structure
 2. Function and genrators
 3. Classes
<!--more-->

### Control structure
`for` and `while` loops; `if`, `elif` and `else` condiotnal statements:
```python
# Examples of iteration with for loops.

my_list = [0, 1, 2, 3, 4, 5]

# Print each value in my_list. Note you can use the "in" keyword to iterate over a list.
for item in my_list:
    print('The value of item is: ' + str(item))

# Print each index and value pair.
for i, value in enumerate(my_list):
    print('The index value is: ' + str(i) + '. The value at i is: ' + str(value))

# Print each number from 0 to 9 using a while loop.
i = 0
while(i < 10):
    print(i)
    i += 1

# Print each key and dictionary value. Note that you can use the "in" keyword 
# to iterate over dictionary keys.
my_dict = {'a': 'jill', 'b': 'tom', 'c': 'tim'}
for key in my_dict:
    print(key + ', ' + my_dict[key])

# Conditional Statements
num = 5
if num < 5:
    print('The number is smaller than 5.')
elif num == 5:
    print('The number equals 5.')
else:
    print('The number is greater than 5.')
```
### Function and genrators
#### Python Functions
In the previous exercises, you worked with examples of Python functions. If you haven't written one from scratch in a while, writing a function in Python involves a function declaration `def` that takes one or more values, and a `return` that returns one or more values. Unlike some other languages, in Python you are not required to specify the data-type of the value your function is going to return.

Note: In Python every function returns a value. In case you do not specify a return value explicitly, Python will return `None` from that function.
```python
# Example function 1: return the sum of two numbers.
def sum(a, b):
    return a+b

# Example function 2: return the size of list, and modify the list to now be sorted.
def list_sort(my_list):
    my_list.sort()
    return len(my_list),  my_list
```

#### Python Generators
A generator in Python is similar to a function except instead of returning a value and exiting a process, a generator will pause the process, saving its state for next time. The biggest difference between a function and generator from a code perspective is one word: `return` is changed to `yield`.

A generator becomes very useful when dealing with very large collections of data that you don’t want to store in memory all at once. It’s also very useful for dealing with extremely large or even infinite series.

Below is an example of how to use a generator to print even numbers. Printing all even numbers at once would take an infinite amount of time, but the generator allows the process to pause, and go back to creating even numbers when needed.

To create the next successive even number simply call `next()` on the generator object, and it will yield the next iteration. After `yield` is called, everything in the state of the generator function **freezes**, and the value is returned. When the generator is called again with `next()`, it picks back up right where it stopped at `yield` from before.
```python
# Definition of the generator to produce even numbers.
def all_even():
    n = 0
    while True:
        yield n
        n += 2

my_gen = all_even()

# Generate the first 5 even numbers.
for i in range(5):
    print(next(my_gen))

# Now go and do some other processing.
do_something = 4
do_something += 3
print(do_something)

# Now go back to generating more even numbers.
for i in range(100):
    print(next(my_gen))
```

### Classes
#### Overview
A class is a structure in object-oriented programming that allows **functions and related data** to be **grouped together**.

In a Python class, an important concept is `self`, which is used to reference a class instance's own variables and functions from within the class definition. For example, if we had a class called `Person` and we wanted the class instances to have a variable called `age`, we could store this information by using `self.age`.

Also, if we wanted the class to have a function that would increment the age of the person, we could define a function inside this class called `def birthday(self)`. In order to be a class function, birthday needs to *include the input variable* `self`, as this is used for proper referencing within the class.

Another important and commonly used function definition is the class initializer, `def __init__(self)`. The body of the initializer is where instance variable definitions should be added, and the initializer initializes all the variables once an instance of the class is created. Also, any input variables that a class needs to have, such as a name for the person can be passed into initializer function.

#### Examples
Below is an example of a basic Person class. The class has two variables for name and age, along with three functions for initializing the class, incrementing the person’s age, and getting the person’s name.
```python
class Person:
    def __init__(self, name, age):
        self.person_name = name
        self.person_age = age

    def birthday(self):
        self.person_age += 1

    def getName(self):
        return self.person_name
```
Let’s look at an example for how to create an instance of the `Person` class using the class template above. We can then access that `Person`’s name:
```python
bob = Person('Bob', 32)
print(bob.getName())
# prints Bob
```
Currently, we have one function for getting the class’s variable. This is called an Accessor. The other function that the class has is actually modifying one of the class’ variables, and that is called a Mutator. We can make our `Person` older by calling `birthday()`
```python
bob.birthday()
print(bob.person_age)
# prints 33
```
The birthday function call successfully increments the age of our Person. Also note that we can directly get the age of bob without using a function call. This is because the `Person` class variables are *defined as public*, so we can directly access them without a function call. If instead we wanted the Person’s age variable to be private to the class, in Python 3 we could put double underscores in front of the variable: `__person_age`. Then we would have to use a function call in order to retrieve it.