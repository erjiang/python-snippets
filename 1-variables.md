# Python snippet #1 - Using variables


In the below Python program, what will be printed?

```
x = 2
print x
```

What will the below Python program print?

```
x = 2
x = 4
print x
```

What will the below Python program print?

```
x = 2
y = x
print y
```

So far so good...

What will the below Python program print?

```
x = 3
y = x
y = 5
print x
```

If you are not sure, run Python in your Terminal and double-check for yourself.

Python lists let you have multiple items inside. Each item can be different, and you can have any number of items:

What does the below Python program print?

```
x = [1, 2, 3]
print x
```

You can also get individual items from within the list based on its position in the list.

What does the below Python program print?

```
x = [1, 2, 3, "hello"]
print x[3]
```

You can also add items to an existing list:

What does the below Python program print?

```
x = [1, 2, 3, "hello"]
x.append("world")
print x
```

You can also assign other variables to this list:

What does the below Python program print?

```
x = [1, 2, 3, "hello"]
y = x
print y[3]
```

What about this?

```
x = [1, 2, 3, "hello"]
y = x
y.append("world")

print x
print y
```

Did you expect `x` and `y` to be the same, or different?

And what will this print?

```
x = [1, 2, 3]
y = x
y.append(4)
x = [2, 3]

print x
print y
```

There's a difference between modifying a variable's existing value, and giving a variable a new value. And each programming language does some things slightly differently. Why does Python do things a certain way? You'd have to ask Guido.

In this piece of code, there only ever exists 1 list:

```
x = [1, 2, 3]
y = x
x.append(4)

print x
print y
```

We are changing the list using `.append`. That's why when we print `x` and `y`, we get the same thing.

But in this example:

```
x = [1, 2, 3]
y = x
x = [1, 2, 3, 4]

print x
print y
```

Here, we first created a list, `[1, 2, 3]`. But then, we made another list `[1, 2, 3, 4]` and assigned `x` to that instead. So we end up with two lists, and `x` is assigned to one of them and `y` to the other.

Lists are what we call "mutable" - you can "mutate" them or change them. Not everything is Python is mutable, but "lists", "sets", and "dictionaries" are among some of the mutable things.

```
x = 5
y = x
x = x + 1

print x
print y
```

In this above example, we're not modifying the number 5 itself. We're calculating `5 + 1` and then assigning `x` to the result.