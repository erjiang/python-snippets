# Python snippet #0 - Python usage

You can access many "command-line tools" through the Terminal app on your computer.

```
Last login: Web Feb 24 10:56:19 on ttys001
my-macbook:~ eric$
```

The `$` is the prompt at which you can type the name of the program that you want to run. For example, if I want to use the `date` program to see what the current date is, I would type `date` after the `$`:

```
my-macbook:~ eric$ date
Tue Apr 17 17:22:28 PDT 2018
```

We call Python a programming language, but practically speaking, it's also just a program on your computer that takes text (so-called "Python code"), looks at the text, and then performs certain actions based on the text.

There are a few ways to run Python from the command-line. You can run it "interactively", where you can type expressions and Python will run the code and tell you what the result is:

```
my-macbook:~ eric$ python
Python 2.7.12 (default, Dec  4 2017, 14:50:18) 
[GCC 5.4.0 20160609] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 2+2
4
```

This is a good way to test short pieces of code that you're not sure about.

The other way is to save your code in a text file and then tell Python to run the code in the file.

You can use any text editor that can read and write "plain" text files. If you use TextEdit, make sure to use only plain text files (in the TextEdit menu bar, go to Format > Make Plain Text).

Put this in a text file:

```
2+2
print "Hello, world!"
```

and save it as "helloworld.py" in your home directory (the directory that contains Documents, Downloads, etc.).

Then, back in your terminal, you can do:

```
my-macbook:~ eric$ python hello.py
```

And you should see `Hello, world!` appear. Why did it not print the result of 2+2?

The difference is that when you are using Python interactively (in the Python "REPL"), it shows you the result of each line you type. But when running a program from a file, it doesn't do that automatically.