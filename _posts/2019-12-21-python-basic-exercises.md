---
title: "python 3 basic exercises"
excerpt_separator: <!--more-->
last_modified_at: 2019-12-21T07:09:02-08:00
---
> Prepared for Programming, Python basic concept excercises:
 1. Control structure
 2. Function and genrators
 3. Classes
<!--more-->

### Control structure
#### Exercise 1
In the following exercise you will finish writing `smallest_positive` which is a function that finds the smallest positive number in a list.
```python
def smallest_positive(in_list):
    # TODO: Define a control structure that finds the smallest positive
    # number in in_list and returns the correct smallest number.
    
    return 0

# Test cases

print(smallest_positive([4, -6, 7, 2, -4, 10]))
# Correct output: 2

print(smallest_positive([.2, 5, 3, -.1, 7, 7, 6]))
# Correct output: 0.2
```

=> solution.py 
```python
def smallest_positive(in_list):
    # TODO: Define a control structure that finds the smallest positive
    # number in in_list and returns the correct smallest number.
    smallest_pos = None
    for num in in_list:
        if num > 0:
            # Note: we use a logical "or" in this solution to form 
            # the conditional statement, although this was
            # not introduced above. 
            if smallest_pos == None or num < smallest_pos:
                smallest_pos = num
    return smallest_pos

# Test cases

print(smallest_positive([4, -6, 7, 2, -4, 10]))
# Correct output: 2

print(smallest_positive([.2, 5, 3, -.1, 7, 7, 6]))
# Correct output: 0.2
```

#### Exercise 2
Now let's assume you are planning on taking some additional courses at your local educational institution, and you have acquired some data about the available courses and when they will be offered. In the following exercise, you will write control structures to process the data and return the semesters when a given course is offered.

You will need to complete the function `when_offered(courses, course)`. This function accepts a "courses" data structure and a "course" string. The function should return a list of strings representing the semesters when the input course is offered. See the two test cases below for examples of correct results.

Since the `when_offered` function accepts a dictionary data structure, you will find the
```python
for <key> in <dictionary>:                  
    <block>
```
construct useful, as this loops through the key values in a dictionary.

=> solution.py 
```python
# This exercise uses a data structure that stores Udacity course information.
# The data structure format is:

#    { <semester>: { <class>: { <property>: <value>, ... },
#                                     ... },
#      ... }


courses = {
    'spring2020': { 'cs101': {'name': 'Building a Search Engine',
                           'teacher': 'Dave',
                           'assistant': 'Peter C.'},
                 'cs373': {'name': 'Programming a Robotic Car',
                           'teacher': 'Sebastian',
                           'assistant': 'Andy'}},
    'fall2020': { 'cs101': {'name': 'Building a Search Engine',
                           'teacher': 'Dave',
                           'assistant': 'Sarah'},
                 'cs212': {'name': 'The Design of Computer Programs',
                           'teacher': 'Peter N.',
                           'assistant': 'Andy',
                           'prereq': 'cs101'},
                 'cs253': {'name': 'Web Application Engineering - Building a Blog',
                           'teacher': 'Steve',
                           'prereq': 'cs101'},
                 'cs262': {'name': 'Programming Languages - Building a Web Browser',
                           'teacher': 'Wes',
                           'assistant': 'Peter C.',
                           'prereq': 'cs101'},
                 'cs373': {'name': 'Programming a Robotic Car',
                           'teacher': 'Sebastian'},
                 'cs387': {'name': 'Applied Cryptography',
                           'teacher': 'Dave'}},
    'spring2044': { 'cs001': {'name': 'Building a Quantum Holodeck',
                           'teacher': 'Dorina'},
                        'cs003': {'name': 'Programming a Robotic Robotics Teacher',
                           'teacher': 'Jasper'},
                     }
    }

# In this exercise, you will need to complete the function 
# when_offered(courses, course). This function accepts a "courses" 
# data structure and a "course" string. 
# The function should return a list of strings representing the semesters 
# when the input course is offered. See the two test cases below for examples 
# of correct results.


def when_offered(courses, course):
    # TODO: Fill out the function here.
    semesters = []
    for semester in courses:
        if course in courses[semester]:
            semesters.append(semester)
    # TODO: Return list of semesters here.
    return semesters



print(when_offered(courses, 'cs101'))
# Correct result: 
# ['fall2020', 'spring2020']

print(when_offered(courses, 'bio893'))
# Correct result: 
# []
```

### Function and genrators
#### Exercise 1
In the following exercise, you will create a generator `fact_gen()` that generates factorials. For a number n, n factorial is denoted by n!, and it is the product of all positive integers less than or equal to n. For example,

5! = 5 * 4 * 3 * 2 * 1 = 120

In this exercise, you will define `prod(a, b)` which returns the product of numbers `a` and `b`. You will also define `fact_gen()` which yields the next factorial number.
```python
def prod(a,b):
    # TODO change output to the product of a and b
    output = 0
    return output

def fact_gen():
    i = 1
    n = i
    while True:
        output = prod(n, i)
        yield output
        # TODO: update i and n
        # Hint: i is a successive integer and n is the previous product


# Test block
my_gen = fact_gen()
num = 5
for i in range(num):
    print(next(my_gen))

# Correct result when num = 5:
# 1
# 2
# 6
# 24
# 120
```

=> solution.py 
```python
def prod(a,b):
    # TODO change output to the product of a and b
    # output = a*b
    # return output
    return a*b # simplified

def fact_gen():
    i = 1
    n = i
    while True:
        output = prod(n, i)
        yield output
        # TODO: update i and n
        # Hint: i is a successive integer and n is the previous product
        n = output
        i += 1

# Test block
my_gen = fact_gen()
num = 5
for i in range(num):
    print(next(my_gen))

# Correct result when num = 5:
# 1
# 2
# 6
# 24
# 120
```

#### Exercise 2
In the next exercise, you will write a function that checks sudoku squares for correctness.

Sudoku is a logic puzzle where a game is defined by a partially filled 9 x 9 square of digits where each square contains one of the digits 1, 2, 3, 4, 5, 6, 7, 8, 9. For this question we will generalize and simplify the game.

Define a procedure, `check_sudoku`, that takes as input a square list of lists representing an n x n sudoku puzzle solution and returns the boolean True if the input is a valid sudoku square and returns the boolean False otherwise.

A valid sudoku square satisfies these two properties:

  1. Each column of the square contains each of the whole numbers from 1 to n exactly once.
  2. Each row of the square contains each of the whole numbers from 1 to n exactly once.

You may assume that the input is square and contains at least one row and column.
```python
# An example solution for the check_sudoku() function

def check_sudoku(square):
    for row in square:
        # Create a list with the integers 1, 2, ..., n.
        # We will check that each number in the row is in the list
        # and remove the numbers from the list once they are verified
        # to ensure that each number only occurs once in the row.
        check_list = list(range(1, len(square[0]) + 1))
        for i in row:
            if i not in check_list:
                return False
            check_list.remove(i)
    for n in range(len(square[0])):
        # We do the same here for each column in the square.
        check_list = list(range(1, len(square[0]) + 1))
        for row in square:
            if row[n] not in check_list:
                return False
            check_list.remove(row[n])
    return True

# test case
right = [[4 ,7 ,6 ,3 ,8 ,9 ,1 ,2 ,5],
         [8 ,3 ,5 ,2 ,7 ,1 ,9 ,4 ,6],
         [2 ,1 ,9 ,5 ,6 ,4 ,8 ,7 ,3],
         [5 ,6 ,4 ,9 ,3 ,2 ,7 ,1 ,8],
         [3 ,9 ,1 ,7 ,4 ,8 ,5 ,6 ,2],
         [7 ,8 ,2 ,1 ,5 ,6 ,4 ,3 ,9],
         [1 ,5 ,8 ,6 ,2 ,7 ,3 ,9 ,4],
         [6 ,4 ,7 ,8 ,9 ,3 ,2 ,5 ,1],
         [9 ,2 ,3 ,4 ,1 ,5 ,6 ,8 ,7]]

print(check_sudoku(right))
# True

wrong = [[4 ,7 ,6 ,2 ,8 ,9 ,1 ,2 ,5],
         [8 ,3 ,5 ,2 ,7 ,1 ,9 ,4 ,6],
         [2 ,1 ,9 ,5 ,6 ,4 ,8 ,7 ,3],
         [5 ,6 ,4 ,9 ,3 ,2 ,7 ,1 ,8],
         [3 ,9 ,1 ,7 ,4 ,8 ,5 ,6 ,2],
         [7 ,8 ,2 ,1 ,5 ,6 ,4 ,3 ,9],
         [1 ,5 ,8 ,6 ,2 ,7 ,3 ,9 ,4],
         [6 ,4 ,7 ,8 ,9 ,3 ,2 ,5 ,1],
         [9 ,2 ,3 ,4 ,1 ,5 ,6 ,8 ,7]]

print(check_sudoku(wrong))
# False
```

### Classes
#### Exercise 1
Now let's assume that the current month is April, and you want to use a `Person` class to help make use of information about the friends in your contacts list. In particular, you'd like to increment the age of all of your friends with birthdays in April. You would also like to know who they are, along with their current ages, so you can send them birthday cards. Finally, you would also like to figure out which month has the most friends with birthdays, so you can budget for all of the birthday cards you will need to buy.

In the following exercise, the `Person` class will be provided for you, and you will be working with a list of instances of the class, representing friends in your contacts. This list is stored in the variable people.

To complete the exercise, you will need to do two things:

  1. Complete the function `get_april_birthdays(people)`. This function should return a dictionary with each name of your friend with an April birthday as a key, and their updated age as the value.
  2. Complete the function `get_most_common_month(people)`. This function should return the name of the month with the most number of birthdays among your friends.

There is some testing code provided in `test()`, and there are more specific TODO instructions in each of the two functions mentioned.

```python
class Person:
    def __init__(self, name, age, month):
        self.name = name
        self.age = age
        self.birthday_month = month
        
    def birthday(self):
        self.age += 1

def create_person_objects(names, ages, months):
    my_data = zip(names, ages, months)
    person_objects = []
    for item in my_data:
        person_objects.append(Person(*item))
    return person_objects

def get_april_birthdays(people):
    # TODO:
    # Increment "age" for all people with birthdays in April.
    # Return a dictionary "april_birthdays" with the names of
    # all people with April birthdays as keys, and their updated ages 
    # as values. See the test below for an example expected output.
    april_birthdays = {}

    
    # TODO: Modify the return statement 
    return

def get_most_common_month(people):
    # TODO:
    # Use the "months" dictionary to record counts of birthday months
    # for persons in the "people" data.
    # Return the month with the largest number of birthdays.
    months = {'January':0, 'February':0, 'March':0, 'April':0, 'May':0, 
              'June':0, 'July':0, 'August':0, 'September':0, 'October':0,
              'November':0, 'December':0}
    
    # TODO: Modify the return statement.
    return


def test():
    # Here is the data for the test. Assume there is a single most common month.
    names = ['Howard', 'Richard', 'Jules', 'Trula', 'Michael', 'Elizabeth', 'Richard', 'Shirley', 'Mark', 'Brianna', 'Kenneth', 'Gwen', 'William', 'Rosa', 'Denver', 'Shelly', 'Sammy', 'Maryann', 'Kathleen', 'Andrew', 'Joseph', 'Kathleen', 'Lisa', 'Viola', 'George', 'Bonnie', 'Robert', 'William', 'Sabrina', 'John', 'Robert', 'Gil', 'Calvin', 'Robert', 'Dusty', 'Dario', 'Joeann', 'Terry', 'Alan', 'Rosa', 'Jeane', 'James', 'Rachel', 'Tu', 'Chelsea', 'Andrea', 'Ernest', 'Erica', 'Priscilla', 'Carol', 'Michael', 'Dale', 'Arthur', 'Helen', 'James', 'Donna', 'Patricia', 'Betty', 'Patricia', 'Mollie', 'Nicole', 'Ernest', 'Wendy', 'Graciela', 'Teresa', 'Nicole', 'Trang', 'Caleb', 'Robert', 'Paul', 'Nieves', 'Arleen', 'Milton', 'James', 'Lawrence', 'Edward', 'Susan', 'Patricia', 'Tana', 'Jessica', 'Suzanne', 'Darren', 'Arthur', 'Holly', 'Mary', 'Randal', 'John', 'Laura', 'Betty', 'Chelsea', 'Margaret', 'Angel', 'Jeffrey', 'Mary', 'Donald', 'David', 'Roger', 'Evan', 'Danny', 'William']
    ages  = [17, 58, 79, 8, 10, 57, 4, 98, 19, 47, 81, 68, 48, 13, 39, 21, 98, 51, 49, 12, 24, 78, 36, 59, 3, 87, 94, 85, 43, 69, 15, 52, 57, 36, 52, 5, 52, 5, 33, 10, 71, 28, 70, 9, 25, 28, 76, 71, 22, 35, 35, 100, 9, 95, 69, 52, 66, 91, 39, 84, 65, 29, 20, 98, 30, 83, 30, 15, 88, 89, 24, 98, 62, 94, 86, 63, 34, 23, 23, 19, 10, 80, 88, 67, 17, 91, 85, 97, 29, 7, 34, 38, 92, 29, 14, 52, 94, 62, 70, 22]
    months = ['January', 'March', 'January', 'October', 'April', 'February', 'August', 'January', 'June', 'August', 'February', 'May', 'March', 'June', 'February', 'August', 'June', 'March', 'August', 'April', 'April', 'June', 'April', 'June', 'February', 'September', 'March', 'July', 'September', 'December', 'June', 'June', 'August', 'November', 'April', 'November', 'August', 'June', 'January', 'August', 'May', 'March', 'March', 'March', 'May', 'September', 'August', 'April', 'February', 'April', 'May', 'March', 'March', 'January', 'August', 'October', 'February', 'November', 'August', 'June', 'September', 'September', 'January', 'September', 'July', 'July', 'December', 'June', 'April', 'February', 'August', 'September', 'August', 'February', 'April', 'July', 'May', 'November', 'December', 'February', 'August', 'August', 'September', 'December', 'February', 'March', 'June', 'December', 'February', 'May', 'April', 'July', 'March', 'June', 'December', 'March', 'July', 'May', 'September', 'November']
    people = create_person_objects(names, ages, months)

    # Calls to the two functions you have completed.
    print(get_april_birthdays(people))
    print(get_most_common_month(people))



test()
# Expected result:
# {'Michael': 11, 'Erica': 72, 'Carol': 36, 'Lisa': 37, 'Lawrence': 87, 'Joseph': 25, 'Margaret': 35, 'Andrew': 13, 'Dusty': 53, 'Robert': 89}
# August
```

```python
class Person:
    def __init__(self, name, age, month):
        self.name = name
        self.age = age
        self.birthday_month = month
        
    def birthday(self):
        self.age += 1

def create_person_objects(names, ages, months):
    my_data = zip(names, ages, months)
    person_objects = []
    for item in my_data:
        person_objects.append(Person(*item))
    return person_objects

def get_april_birthdays(people):
    # TODO:
    # Increment "age" for all people with birthdays in April.
    # Return a dictionary "april_birthdays" with the names of
    # all people with April birthdays as keys, and their updated ages 
    # as values. See the test below for an example expected output.
    april_birthdays = {}
    for person in people:
      if person.birthday_month == 'April':
        person.birthday()
        april_birthdays[person.name] = person.age
    
    # TODO: Modify the return statement 
    return april_birthdays

def get_most_common_month(people):
    # TODO:
    # Use the "months" dictionary to record counts of birthday months
    # for persons in the "people" data.
    # Return the month with the largest number of birthdays.
    months = {'January':0, 'February':0, 'March':0, 'April':0, 'May':0, 
              'June':0, 'July':0, 'August':0, 'September':0, 'October':0,
              'November':0, 'December':0}
    for person in people:
      for month in months:
        if person.birthday_month == month:
          months[month] += 1
    # TODO: Modify the return statement.
    max_month = 'January'
    for month in months:
      if months[max_month] < months[month]:
        max_month = month
    return max_month


def test():
    # Here is the data for the test. Assume there is a single most common month.
    names = ['Howard', 'Richard', 'Jules', 'Trula', 'Michael', 'Elizabeth', 'Richard', 'Shirley', 'Mark', 'Brianna', 'Kenneth', 'Gwen', 'William', 'Rosa', 'Denver', 'Shelly', 'Sammy', 'Maryann', 'Kathleen', 'Andrew', 'Joseph', 'Kathleen', 'Lisa', 'Viola', 'George', 'Bonnie', 'Robert', 'William', 'Sabrina', 'John', 'Robert', 'Gil', 'Calvin', 'Robert', 'Dusty', 'Dario', 'Joeann', 'Terry', 'Alan', 'Rosa', 'Jeane', 'James', 'Rachel', 'Tu', 'Chelsea', 'Andrea', 'Ernest', 'Erica', 'Priscilla', 'Carol', 'Michael', 'Dale', 'Arthur', 'Helen', 'James', 'Donna', 'Patricia', 'Betty', 'Patricia', 'Mollie', 'Nicole', 'Ernest', 'Wendy', 'Graciela', 'Teresa', 'Nicole', 'Trang', 'Caleb', 'Robert', 'Paul', 'Nieves', 'Arleen', 'Milton', 'James', 'Lawrence', 'Edward', 'Susan', 'Patricia', 'Tana', 'Jessica', 'Suzanne', 'Darren', 'Arthur', 'Holly', 'Mary', 'Randal', 'John', 'Laura', 'Betty', 'Chelsea', 'Margaret', 'Angel', 'Jeffrey', 'Mary', 'Donald', 'David', 'Roger', 'Evan', 'Danny', 'William']
    ages  = [17, 58, 79, 8, 10, 57, 4, 98, 19, 47, 81, 68, 48, 13, 39, 21, 98, 51, 49, 12, 24, 78, 36, 59, 3, 87, 94, 85, 43, 69, 15, 52, 57, 36, 52, 5, 52, 5, 33, 10, 71, 28, 70, 9, 25, 28, 76, 71, 22, 35, 35, 100, 9, 95, 69, 52, 66, 91, 39, 84, 65, 29, 20, 98, 30, 83, 30, 15, 88, 89, 24, 98, 62, 94, 86, 63, 34, 23, 23, 19, 10, 80, 88, 67, 17, 91, 85, 97, 29, 7, 34, 38, 92, 29, 14, 52, 94, 62, 70, 22]
    months = ['January', 'March', 'January', 'October', 'April', 'February', 'August', 'January', 'June', 'August', 'February', 'May', 'March', 'June', 'February', 'August', 'June', 'March', 'August', 'April', 'April', 'June', 'April', 'June', 'February', 'September', 'March', 'July', 'September', 'December', 'June', 'June', 'August', 'November', 'April', 'November', 'August', 'June', 'January', 'August', 'May', 'March', 'March', 'March', 'May', 'September', 'August', 'April', 'February', 'April', 'May', 'March', 'March', 'January', 'August', 'October', 'February', 'November', 'August', 'June', 'September', 'September', 'January', 'September', 'July', 'July', 'December', 'June', 'April', 'February', 'August', 'September', 'August', 'February', 'April', 'July', 'May', 'November', 'December', 'February', 'August', 'August', 'September', 'December', 'February', 'March', 'June', 'December', 'February', 'May', 'April', 'July', 'March', 'June', 'December', 'March', 'July', 'May', 'September', 'November']
    people = create_person_objects(names, ages, months)

    # Calls to the two functions you have completed.
    print(get_april_birthdays(people))
    print(get_most_common_month(people))



test()
# Expected result:
# {'Michael': 11, 'Erica': 72, 'Carol': 36, 'Lisa': 37, 'Lawrence': 87, 'Joseph': 25, 'Margaret': 35, 'Andrew': 13, 'Dusty': 53, 'Robert': 89}
# August
```