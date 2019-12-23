---
title: "Algorithm: How to solve problems?"
categories:
  - Notes
tags:
  - Algorithm
  - Python
  - Notes
excerpt_separator: <!--more-->
last_modified_at: 2019-12-22T05:03:18-08:00
---
> How to solve problems? the practice problem in programing => algorithm problem.<br>
  The steps to solve problems:
   1. Don't Panic!!
   2. Understanding the problem.
      - What're the Inputs?
      - What're the (expected) Outputs?
      - Work through some examples by hand.
   3. Simple mechinical solution and Test.
   4. Develop incrementally and Test. 
<!--more-->

## Don't Panic!!
----------------------
Calm down, try to understand problem firstly.

## Understanding the problem.
----------------------
Read the problem carefully, and answer following questions.

### What're the Inputs?
  - **What is the set of valid input?**
  - **How are inputs represented?**
  - **PS**: List **Defensive programing** -> List items which need to **check inputs**

### What're the (expected) Outputs?
  - **What are the outputs?**
  - **Define the main procedure to link inputs and outputs.**

### Work through some examples by hand.
  - Calculation by hand, list **right** inputs and **wrong** inputs(output is `undefined`).
  - Consider **systematiclly** how a human solve the problem.

## Simple mechinical solution and Test.
----------------------
According to reasonable assumption, to simplify procedure so that we can build **program main framewrok** easily not to think algorithm details.

### **Assumpation**
Give reasonable **Assumpation** to simplify the problem.
  - ...
  - ...

### => Algorithm **Pseudocode** of simple version
  - main procedure
  - helper functions
  - test function 
  - "**Can't handle**" analysis

### => Algorithm **code** of simple version
  - main procedure
  - helper functions
  - test function 
  - "**Can't handle**" analysis


## Develop incrementally and Test.
----------------------
Remove Assumption, and Fix **Can't handle** items. Focusing on the **algorithm main details**.
### => Algorithm **Pseudocode**
  - main procedure
  - helper functions
  - test function 

### => Algorithm **code**
  - main procedure
  - helper functions
  - test function 

## Optimazation
----------------------
...(**TODO**:

## Algorithm Analysis
----------------------
### Time Complexity
#### Simple Methord: **Counting lines**
Just counting how many lines of algorithm, easy but not accurate.
For example:
```python
def say_hello(n):
    for i in range(n):
        for i in range(n):
            print("Hello!")
```
Counting lines: $$n^2+n+1$$
> **PS**: the line inside the `for` loop will get run `n` times.

#### Big O Notaiton: $$O(n)$$ -> **Counting simple single lines / opertations**

For example ($$n$$ is the length of the input to your algorithm.):
```python
create output string                                # 1
for each letter in input:                           # 1 will run in each loop
    get new_letter from letter's location in cipher # 26+1 operations because cipher own 26 letters.
    add new_letter to output                        # 1
```

Counting lines: $$2n+2$$

Counting operations: $$(3+26)n+2$$ => $$O(29n+2)$$ => $$\approx O(n)$$
- **Worst case**: $$O(29n+2)\approx O(n)$$ (each time will check all 26 letters)
- **Average case**: $$O(16n+2)\approx O(n)$$ (each time will check half 26 letters)
- **Best case**: $$O(4n+2)\approx O(n)$$ (each time will check 1 letter)

The rate of increase of an algorithm is also referred to as the **order** of the algorithm.<br>
**Order**:
- $$O(n)$$: linear -> "the order of this relationship is linear"
- $$O(n^2)$$: quadratic
- ... (**TODO**: add more ...)

<br>
Comparison of computational complexity:
{% raw %}
<figure class="figure">
  <img src="assets/images/all-comparison-computational-complexity.svg"
    alt="[&quot;Comparison of computational complexity&quot;](https://commons.wikimedia.org/wiki/File:Comparison_computational_complexity.svg) by [Cmglee](https://commons.wikimedia.org/wiki/User:Cmglee). Used under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.en)."
    class="img img-fluid">
  <figcaption class="figure-caption">
    <p><a href="https://commons.wikimedia.org/wiki/File:Comparison_computational_complexity.svg"
        target="_blank">"Comparison of computational complexity"</a> by <a
        href="https://commons.wikimedia.org/wiki/User:Cmglee" target="_blank">Cmglee</a>. Used under <a
        href="https://creativecommons.org/licenses/by-sa/4.0/deed.en" target="_blank">CC BY-SA 4.0</a>.</p>
  </figcaption>
</figure>
{% endraw %}

### Space Complexity
=> How efficient our algorithm is in terms of memory usage. 

This comes down to the datatypes of the variables we are using and their allocated space requirements. 

In Python, it's less clear how to do this due to the the underlying data structures using more memory for house keeping functions (as the language is actually written in C).

For example, in C/C++, an integer type takes up 4 bytes of memory to store the value, but in Python 3 an integer takes 14 bytes of space. Again, this extra space is used for housekeeping functions in the Python language.

Here, we assume the following sizes:

Type	  | Storage size
char  	| 1 byte
bool	  | 1 byte
int	    | 4 bytes
float	  | 4 bytes
double	| 8 bytes

It is also important to note that we will be focusing on just the data space being used and not any of the environment or instructional space.

Example:
```python
def our_linear_function(n):

    n = n # Type int
    counter = 0 # Type int
    list_ = [] # Assume that the list is empty (i.e., ignore the fact 
               # that there is actually meta data stored with Python lists)

    while counter < n:
        list. append(counter)
        counter = counter + 1

    return list_
```

So in this example we have two integers (`n` and `counter`) and an expanding list, and therefore our space complexity will be `4*n + 8` $$O(4n + 8)\approx O(n)$$ since we have an expanding integer list and two integer data types. This is an example of **linear space complexity**.