# Key Notes of DS4PH Class

Note: Some of the notes here are derived from the class material, while others are personal notes taken during my own learning process.

## Data type conversion

Here are two examples.

```python
a = 10
print(type(float(a)))  # use the float function
a = 10
print(type( a.__float__() ))  # use a method associated with "a" to convert the type
```

```
<class 'float'>
<class 'float'>
```

## Basic operators

```python
print(10 + 10.0) ## addition, in this case an int and float
print(10 ** 2)   ## exponent
print(10 * 2)    ## multiplication
print(10 / 2)    ## division
print(10.1 // 2) ## integer division
print(10.1 % 2)  ## modulo
```

```
20.0
100
20
5.0
5.0
0.09999999999999964
```

## Mutable and immutable

In Python, objects can be classified as mutable or immutable based on whether their value can be changed after they are created.

Mutable objects can be modified after they are created. Examples of mutable objects include lists, dictionaries, and sets. When you modify a mutable object, any variable that references that object will see the changes.

Immutable objects cannot be modified after they are created. Examples of immutable objects include integers, floats, booleans, and tuples. When you modify an immutable object, a new object is created in memory with the new value.

When working with objects in python, mutable and immutable elements act differently. Lists are mutable. So, below, the element `y` gets appended along with `x`.

```python
x = [10]
y = x
x.append(20)
## Notice y has the appended element
print(y)
## let's try again, as of now x = [10, 20] 
x[0] = x[0] + 11
## Now x = [21, 20], but did y change?
print(y)
```

```
[10, 20]
[21, 20]
```

Things like numbers and strings are immutable. Notice that changing `y` does not change `x`.

```python
x = 10
y = x
x = x + 10
print((x, y))
```

```
(20, 10)
```

## Variable length arguments

Python has a special variable for variable length arguments. Here’s an example.

```python
def concat(*args, sep="/"):
 return sep.join(args)  

print(concat("a", "b", "c"))
print(concat("a", "b", "c", sep = ":"))
```

```
a/b/c
a:b:c
```

## Unnamed functions

Lambda can be used to create short, unnamed functions. This has a lot of uses that we’ll see later.

```python
f = lambda x: x ** 2
print(f(5))
```

```
25
```

Here’s an example where we use lambda to make specific “raise to the power” functions.

```python
def makepow(n):
 return lambda x: x ** n

square = makepow(2)
print(square(3))
cube = makepow(3)
print(cube(2))
```

```
9
8
```

## Methods associated with a list object

Note that some methods change the object itself while others return things without changing the object.

```python
pets = ['frogs', 'cats', 'dogs', 'hamsters']
print(pets)
pets.sort() #note this changes the pets object
print(pets)
pets.reverse()
print(pets)
pets.pop() #removes the last item from the list
print(pets)
pets.append("horses")
print(pets)
print(pets.count("horses")) #counts the number of times the string horses is in the list
```

```
['frogs', 'cats', 'dogs', 'hamsters']
['cats', 'dogs', 'frogs', 'hamsters']
['hamsters', 'frogs', 'dogs', 'cats']
['hamsters', 'frogs', 'dogs']
['hamsters', 'frogs', 'dogs', 'horses']
1
```

The `pop()` method removes the item at the given index from the list and returns the removed item; the argument passed to the method is optional. If not passed, the default index -1 is passed as an argument (index of the last item).

If you need to remove the given item from the list, you can use the `remove()` method.

## Create a class

Let’s create a class called `mycomplex` and give it a conjugation method and some other stuff. A class consists of a series of functions.

```python
class mycomplex:
    def __init__(self, real, imag): #a built-in function used to initialize the class 
        self.r = real
        self.i = imag

    def conjugate(self): #note this modifies self
        self.i =  -self.i

    def print(self): # each function in a class needs to have the arg "self" as the first arg
        print((self.r, self.i))

y = mycomplex(10,5) #Now we can use the class named mycomplex to create objects
y.print()
y.conjugate()
y.print()
```

Let’s now create a version that doesn’t modify the object when we conjugate.

```python
class mycomplex:
    def __init__(self, real, imag):
        self.r = real
        self.i = imag

    def conjugate(self): # note this doesn't modify self and returns a new object
        return(mycomplex(self.r, -self.i))

    def print(self):
        print((self.r, self.i))

y = mycomplex(10,5)
y.print()
z = y.conjugate()
y.print()
z.print()
```

To understand the meaning of classes we have to understand the built-in `__init__()` function. All classes have a function called `__init__()`, which is always executed when the class is being initiated. Use the `__init__()` function to assign values to object properties, or other operations that are necessary to do when the object is being created.

The `self` parameter is a reference to the current instance of the class, and is used to access variables that belongs to the class. It does not have to be named `self` , you can call it whatever you like, but it has to be the first parameter of any function in the class.

Use the words `mysillyobject` and `abc` instead of `self`:

```python
Use the words mysillyobject and abc instead of self:

class Person:
  def __init__(mysillyobject, name, age):
    mysillyobject.name = name
    mysillyobject.age = age

  def myfunc(abc):
    print("Hello my name is " + abc.name)

p1 = Person("John", 36)
p1.myfunc()
```

For more details, see [Python Classes - W3Schools](https://www.w3schools.com/python/python_classes.asp).

## Namespace

Let’s load up `numpy`. Here’s three separate ways.

1. `import numpy`
2. `import numpy as np` (recommended)
3. `from numpy import *` (not recommended)

Option 1. `imports numpy`, but then you have to type `numpy.FUNCTION` to access `FUNCTION`. The second option (my preferred) shortens this to `np.FUNCTION`. The third loads the `numpy` functions into the **global namespace**. This is probably OK for really core packages like `numpy`. But, otherwise it’s an issue since you typically load many libraries and some may have the same function names -- it may pollute our global namespace with all its stuff.

## Seaborn

[Seaborn](https://seaborn.pydata.org/index.html) is a Python data visualization library based on [matplotlib](https://matplotlib.org/).

## f-string

```python
s = 100.123456789123456789
print(f"{s} is the weight of the pig.")
```

The code is using an f-string, a feature introduced in Python 3.6, to print a string with dynamic content. The string inside the f-string is being formatted with values from the variable `s`. The f-string is using curly braces `{}` to embed expressions that will be evaluated, in this case the variable `s`. The resulting output is:

```
100.12345678912345 is the weight of the pig.
```

`s` can be any data type, including integer, float, string, etc.

The precision of the output depends on how you specify the format of `s` in the f-string. By default, it follows the normal behavior of converting the value to a string using the `str` function.

If you want to control the precision of a floating-point number, you can use the `.Nf` format specifier, where `N` is the number of digits of precision you want. For example:

```python
x = 3.141592653589793
print(f"{x:.2f}")  # Output: 3.14
```

## str.format()

`str.format()` is an improvement over `%` formatting in Python. The main advantages of using `str.format()` are:

1. Flexibility: `str.format()` provides more flexibility and allows more control over formatting compared to `%` formatting.
2. Readability: `str.format()` is more readable and less error-prone, especially when dealing with complex formatting.
3. Extensibility: `str.format()` allows for the use of named arguments, which makes it easier to add or modify the arguments in the future.
4. Compatibility: `%` formatting is being deprecated and is no longer recommended for use in new code. In contrast, `str.format()` is more modern and is widely used in Python code.

Examples:

```python
# Inserting values in a string using positional arguments
print("My name is {} and I'm {} years old".format("John", 25))
# Output:
# My name is John and I'm 25 years old

# Another use of positional arguments
greeting = "Hello, {}! It's nice to meet you, {}."
print(greeting.format("Alice", "Bob"))
# Output: 
# Hello, Alice! It's nice to meet you, Bob.

# Inserting values in a string using keyword arguments
print("My name is {name} and I'm {age} years old".format(name="John", age=25))
# Output:
# My name is John and I'm 25 years old

# Another use of keyword arguments
contact_info = "Name: {name}, Email: {email}, Phone: {phone}"
print(contact_info.format(name="Alice", email="alice@example.com", phone="555-1234"))
# Output: 
# Name: Alice, Email: alice@example.com, Phone: 555-1234.

# Formatting numbers with a specific number of decimal places
print("PI is approximately {:.2f}".format(3.14159))
# Output:
# PI is approximately 3.14

# Formatting numbers with a specific number of digits
print("{:03d}".format(7)) # here, 0 is the fill character, which is used to pad the value to the desired width
# Output:
# 007

# Displaying a percentage:
print("{:.2%}".format(0.25))
# Output:
# 25.00%

# Aligning text to the left or right by using the ">" or "<" symbol inside the curly braces of a format string
print("{:>10}".format("hello"))
# Output:
#      hello

# Displaying a datetime object
import datetime
print("The current time is {:%Y-%m-%d %H:%M:%S}".format(datetime.datetime.now()))
# Output:
# The current time is 2023-02-19 00:08:43
```

Refer to [here](https://www.runoob.com/python/att-string-format.html) for more usage of `str.format()`.

## Returning a view versus a copy in Pandas

Refer to [Returning a view versus a copy](https://pandas.pydata.org/pandas-docs/stable/user_guide/indexing.html#returning-a-view-versus-a-copy).

If you don't want to know the details, the important conclusion is that **when setting values in a pandas object, care must be taken to avoid what is called `chained indexing`**.

The following are my mistake and its correction about this issue.

```python
# This is wrong, because it use the chained indexing for setting values.
annual.loc[(annual.BUYER_STATE == "AR") & (annual.BUYER_COUNTY == "MONTGOMERY")].loc[:, ["countyfips"]] = 5097

# This is correct and will successfully set the values.
annual.loc[(annual.BUYER_STATE == "AR") & (annual.BUYER_COUNTY == "MONTGOMERY"), "countyfips"] = 5097 # In this example, we are selecting all rows where BUYER_STATE is equal to "AR" and BUYER_COUNTY is equal to "MONTGOMERY", and then setting the countyfips column of those rows to 5097.
```

## Dash, Shiny, and Streamlit

Dash, Shiny, and Streamlit are web frameworks used for building interactive and data-driven web applications.

Dash is a Python framework for building web applications with Python and HTML/CSS. It is particularly well-suited for building data visualization and analytics applications using popular Python data science libraries such as Plotly, Dash Core Components, and Dash HTML Components. (Dash is developed by Poltly.)

Shiny is a web application framework for building interactive web applications with R. It is developed by RStudio and is built on top of the popular R packages, including ggplot2, dplyr, and tidyr.

Actually, Dash is a framework for developing dashboards and creating web based data apps in R, python or Julia. Dash is more popular among the python focused, while shiny, a related platform, is more popular among R focused, but also applies much more broadly than just for R apps. So, usually we compare Python Dash with R Shiny.

Streamlit is an open-source Python framework for building data apps. It allows you to quickly create and share interactive data apps and dashboards using only Python code. It comes with a set of pre-built components for data visualization, user input, and output that allow you to create interactive apps in minutes.

All three frameworks are designed to be user-friendly and accessible to developers without deep expertise in web development, making it easy to create and deploy data-driven web applications. Dash is the most full framework; Shiny makes some compromises to make it little easier; Streamlit then makes a lot of compromises to make it easier.

##  "\_\_call\_\_" method

In Python, the `__call__` method is used to make an instance of a class callable like a function. When an instance is called, the `__call__` method is automatically invoked. This method can be defined within a class to define what happens when the instance of the class is called.

Here is an example:

```python
class MyClass:
    def __init__(self, value):
        self.value = value
    
    def __call__(self, x):
        return self.value + x
    
obj = MyClass(10)
print(obj(5))   # Output: 15
```

In the above example, `MyClass` defines a `__call__` method which adds the input value `x` to the value of the instance variable `value`. When the instance `obj` is called with an input of `5`, it returns the sum of `obj.value` and `x`, which is `15`.

## Decorators

First, we give two examples, and the `wraps` decorator used in the examples will be explained latter.

Example 1:

```python
from functools import wraps


# Here, we define a func 'logit' outside the decorator func 'logging_decorator'.
# The func 'logit' is used to pass parameters to the decorator func.
def logit(logfile='out.log'):
    def log_decorator(func): # decorator function (decorator)
        @wraps(func)
        def wrapper(*args, **kwargs): # wrapper function (wrapper)
            log_string = func.__name__ + " was called"
            print(log_string)
            # open logfile for writing
            with open(logfile, 'a') as opened_file:
                # write log_string into logfile
                opened_file.write(log_string + '\n')
            return func(*args, **kwargs)
        return wrapper
    return log_decorator

# here, the parentheses imply that 'logit' is not the decorator func, but a 
# func outside the decorator func, or a insatnce of a class in next example. 
@logit() 
def myfunc1():
    pass
 
myfunc1()
# Output: myfunc1 was called
# a file named 'out.log' will be generated with lpg_string written in

@logit(logfile='func2.log') # input a name for the log file
def myfunc2():
    pass
 
myfunc2()
# Output: myfunc2 was called
# a file named 'func2.log' will be generated with log_string written in
```

Example 2:

```python
from functools import wraps


# here we use class to do the same thing
class logit(object):
    def __init__(self, logfile='out.log'):
        self.logfile = logfile
 
    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            log_string = func.__name__ + " was called"
            print(log_string)
            # open logfile for writing
            with open(self.logfile, 'a') as opened_file:
                # write log_string into logfile
                opened_file.write(log_string + '\n')
            # send a notification
            self.notify()
            return func(*args, **kwargs)
        return wrapper
 
    def notify(self):
        # just pass, not defined here
        pass

# here logit() is a instance of the class
@logit()
def myfunc1():
    pass

myfunc1()
# Output: myfunc1 was called
# a file named 'out.log' will be generated with log_string written in
```

The `wraps` decorator is a convenience decorator provided in the `functools` module in Python. It is used to update the attributes of the wrapper function to match the original function being decorated.

When you decorate a function with another function, the original function's metadata (like its name, docstring, etc.) may get replaced by those of the decorator function. This can cause issues when debugging, testing or using some tools that rely on the original function's metadata. The `wraps` decorator helps to solve this issue by copying the original function's metadata to the wrapper function.

Here's an example:

```python
from functools import wraps

def decorator(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        """This is the wrapper function"""
        return func(*args, **kwargs)
    return wrapper

@decorator
def my_function():
    """This is the original function"""
    pass

print(my_function.__name__) # Output: my_function
print(my_function.__doc__) # Output: This is the original function
```

In the example above, the `wraps` decorator is used to copy the name and docstring of the original function `my_function` to the wrapper function `wrapper`. This ensures that the metadata of the original function is preserved.

## Type hints

We can use type hints to provide information about the expected types of function or method parameters, return values, and attributes. They are optional, but can be helpful for code clarity and for identifying errors during development.

We can see examples before the explanation. The following are two examples, one without the package `typing` and one with the package `typing`.

Example 1:

```python
def func_with_type_hint(
        channels: int,
        feature: int = 24,
        rate: float = 0.0,
        check: bool = False,
        spatial_dims: int = 3,
    ) -> None:
    print("func_with_type_hint successfully runs")

func_with_type_hint(1) 
# Output: func_with_type_hint successfully runs
```

Example 2:

```python
from typing import Sequence, Tuple, Type, Union
from sklearn.linear_model import LinearRegression

def func_with_type_hint(
        size: Union[Sequence[int], int],
        channels: int,
        heads: Sequence[int] = (3, 6, 12, 24),
        feature: int = 24,
        norm: Union[Tuple, str] = "instance",
        rate: float = 0.0,
        check: bool = False,
        spatial_dims: int = 3,
        encoding: Union[Tuple, str] = 'rand',
        method_class: Type[LinearRegression] = LinearRegression, # LinearRegression is a class, so we use Type[LinearRegression] to indicate its class
        method_instance: LinearRegression = LinearRegression(), # LinearRegression() is an instance of the class, so we directly use LinearRegression to indicate its class
    ) -> None:
    print("func_with_type_hint successfully runs")

func_with_type_hint(1,2)
# Output: func_with_type_hint successfully runs
```

In Python, the syntax used to define the type hints is based on PEP 484, which specifies a syntax for annotating variables, functions and arguments with their expected types.

The syntax of type hints and default values is `variable_name: type_hint = default_value` where `variable_name` is the name of the variable, `type_hint` is the expected data type of the variable, and `default_value` is an optional value that can be assigned to the variable if no other value is provided.

For example, `: int = 3` means that the variable is an integer type and its default value is 3. The `-> None` syntax is used to specify the return type of a function, where `None` means that the function does not return any value.

Sometimes we need the package `typing`  if more types are needed. `typing` is a module in Python that provides support for type hints, which allow you to indicate the expected types of function arguments, return values, and variables. Type hints are not enforced at runtime, but they can help catch errors during development and make code more readable and self-documenting. The `typing` module provides various types, such as `List`, `Dict`, `Tuple`, `Union`, `Any`, etc., which can be used to specify the types of variables and function arguments.



