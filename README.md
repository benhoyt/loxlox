
LoxLox
======

LoxLox is an interpreter for [Crafting Interpreters'](http://www.craftinginterpreters.com/) [Lox](http://www.craftinginterpreters.com/the-lox-language.html) language written in ... Lox.

Below are a few notes about running LoxLox, but you can [**read more about LoxLox here**](https://benhoyt.com/writings/loxlox/).

## How to run LoxLox

First clone the LoxLox repo as well as the Crafting Interpreters one:

```
$ git clone https://github.com/benhoyt/loxlox
$ git clone https://github.com/munificent/craftinginterpreters
```

Then patch the Crafting Interpreters repo to add the required builtins to JLox (`getc()`, `chr()`, etc) and build JLox:

```
$ cd craftinginterpreters
$ git apply ../loxlox/jlox_diff.patch
$ make jlox
$ cd ../loxlox
```

Now you're ready to run LoxLox (input can only be passed to LoxLox on stdin):

```
$ 
$ ./jlox lox.lox < example.lox
1
4
9
16
Waddles quacks
6
105
$ ./jlox lox.lox < sum.lox 
4.99995E9
$ echo 'print "Hello world!";' | ./jlox lox.lox 
Hello world!
```

## Running the tests

To run the Lox test suite against LoxLox, use this command:

```
python test.py
```

Note that several tests will fail. That's expected -- the code works, and the failures are only from differences in the runtime error messages between JLox and LoxLox.

To run the tests and diff against the git-committed failure output:

```
python test.py > failures
```

## Contact me

[Contact me](https://benhoyt.com/) if you have any feedback, suggestions, or whatever. And if you get LoxLox to run under LoxLox ... mind blown.
