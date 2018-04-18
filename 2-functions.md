# Python snippet #2 - Function expressions

Functions in Python look like functions in math.

In math, you might have "f(x) = 2x + 5". That's the function of a line.

When we write, "f(2)", we know that's equivalent to 9:

>f(x) = 2x + 5

>f(2) = 2(2) + 5

>f(2) = 4 + 5

>f(2) = 9

And we can also nest expressions:

> g(x) = 3x - 2

> f(g(2)) = 2(g(2)) + 5

We can calculate "g(2)" first:

> g(2) = 3(2) - 2

> g(2) = 6 - 2

> g(2) = 4

And then substitute that in:

> f(g(2)) = f(4)

> f(4) = 2(4) + 5

> f(4) = 8 + 5

> f(4) = 13

In Python, declaring function uses `def` and `return`:

```
def f(x):
    return 2 * x + 5
```

The `return` keyword gives us the result of the function. Using ("calling") a function is similar to math too. We use parentheses to enclose the stuff we give to the function (the "arguments").

What does this Python program print?

```
def f(x):
    return 2 * x + 5
 
 x = f(2)
 print x
```
 
What if we flip around some of that code?

```
x = f(2)

def f(x):
    return 2 * x + 5

print x
```

Uh oh, why did that happen?

Functions don't have to `return` something. They can do other things like print text, download a file, send an email, and so on.

```
def greet(name):
    print "Hello, " + name

greet("Tom")
```

Why didn't we write `print greet("Tom")`? What does this program do?

```
def greet(name):
    print "Hello, " + name

print greet("Tom")
```

We got some extra stuff. Maybe this would be clearer:

```
def greet(name):
    print "Hello, " + name

x = greet("Tom")

print "This is the result I got from greet:"
print x
```

Notice that the greeting got printed first, when we did `x = greet("Tom")`. And `x` got the value of `None`.

In Python, all functions return *something*. If you don't use `return` to return something, Python will go ahead and treat it as if you were returning `None`, which is a special value in Python.

`None` is not `0`: you cannot do `None + 2`.

`None` is not an empty list: you cannot do `None.append(123)`.

`None` is not `"None"`: you cannot do `None.capitalize()`.

`None` is just `None`.

The `return` keyword also has another special behavior:

What does this Python program print?

```
def f(x):
    print "I am about to calculate something."
    return 2 * x + 5
    print "I am done calculating."

x = f(2)
```

When a function returns something, it's done.

Functions can, of course, use other functions.

What does the following Python program print?

```
def f(x):
    print "Beginning of f"
    new_x = g(x) * 3
    print "End of f"
    return new_x

def g(x):
    print "Beginning of g"
    new_x = x * 2
    print "End of g"
    return new_x

my_num = f(2)
print my_num
```

Why didn't we have to put `def g(x):` before `def f(x):` even though `f` uses `g`?

Functions give their own names to the arguments that they're given.

```
def f(x):
    return 2 * x

y = 5
f(y)
```

We gave `y` to `f`, but `f` calls it `x`.

What does this Python program print?

```
def f(x):
    z = 2
    return x * z

y = 2
print f(y)
print z
```

The `z` that `f` created only exists inside `f`. Python doesn't let you use `z` from outside `f`. Imagine if you had to think about all the different variables created in functions that other people wrote spilling out into your code! This lets you worry a little less about the innards of a function that you're calling.

What does this Python program do?

```
the_name = "Bob"
def greet():
    "Hello, " + the_name

greet()

the_name = "Moe"
greet()
```

It's a one-way street. You can use variables that functions create from outside the function, but functions can use variables that were declared outside of the function.

Still, Python has an additional safety feature.

What does this Python program do?

```
scoreboard = 0

def add_score():
    scoreboard = scoreboard + 1

def print_score():
    print "You have"
    print scoreboard
    print "points"

print_score()

add_score()
add_score()
add_score()

print_score()
```

Hmm... this is a design decision that the creators of Python decided on. When you write `x = 2` inside a function, chances are that you just wanted a new `x`, not that you wanted to modify any `x` that exists outside the function. That would be an unintended consequence, and an easy mistake to make once your programs get bigger and bigger.

Python has a way to work around this though:

```
scoreboard = 0

def add_score():
    global scoreboard # Yes, we want to modify the "global" scoreboard
    scoreboard = scoreboard + 1

def print_score():
    print "You have"
    print scoreboard
    print "points"

print_score()

add_score()
add_score()
add_score()

print_score()
```

We can these things that are at the "top-level" (i.e. not in a function) "global" because everyone can see them. Variables inside the function that can't be seen or used outside the function are "local".

## Bonus brainteaser

Are functions also variables? Is this program possible? If so, what does it print?

```
def halve(x):
    return x / 2

divide_by_two = halve

print divide_by_two(4)
```

What about this?

```
def do_twice(x, y)
    return x(x(y))

def halve(y):
    return y / 2

print do_twice(halve, 8)
```