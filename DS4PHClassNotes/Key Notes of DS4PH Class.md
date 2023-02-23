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

 
