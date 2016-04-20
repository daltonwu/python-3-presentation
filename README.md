### tl;dr
Python 2.x is legacy.  
Python 3.x is the present and future of the language.  
New projects should be written in Python 3.

# About Python releases
Python version numbers come in the form `A.B.C` where:
* `A` is the major version number
* `B` is the minor version number
* `C` is the bugfix release number

Some examples: versions 2.7.11 (2015-12-05), 3.5.1 (2015-12-07), and 3.4.4 (2015-12-21). Note that bugfixes continue to be rolled out even for previous versions of Python.

Python 2.7, the last minor update to Python 2, was released in 2010. This marked the end of _feature_ updates to Python 2—there will never be a Python version 2.8. The end-of-life for Python 2 is currently set to 2020; however, it will likely be postponed because a significant amount of code in use is written in Python 2 and cannot or will not be easily converted to Python 3.

Python 3.0 was released in 2008. It may be surprising that the first version of Python 3 came before the last version of Python 2. It may also be surprising that Python 3.0 is, in the words of Guido von Rossum, B.D.F.L., the "first ever _intentionally backwards incompatible_ Python release". At the time of writing, Python 3 is continually receiving improvements and new features.

# Primary differences between Python 2 and Python 3

## The `print` statement is now a function
    Old: print "The answer is", 2*2
    New: print("The answer is", 2*2)
    
    Old: print x,           # Trailing comma suppresses newline
    New: print(x, end=" ")  # Appends a space instead of a newline
    
    Old: print              # Prints a newline
    New: print()            # You must call the function!
    
    Old: print >>sys.stderr, "fatal error"
    New: print("fatal error", file=sys.stderr)
    
    print([object, ...][, sep=' '][, end='\n'][, file=sys.stdout])
    
    >>> print("There are <", 2**32, "> possibilities!", sep="")
    There are <4294967296> possibilities!

## Numbers
An expression like `1/2` now returns a float. Use `1//2` to get the truncating behavior.

Octal literals are no longer of the form `0720`; use `0o720` instead (implemented since version 2.6). Likewise, use `0b1010` for binary literals (also supported since version 2.6).

Essentially, the number type `long` has been renamed to `int`. Integer literals no longer support a trailing `l` or `L`.

The constant `sys.maxint` has been removed, since there is no longer a limit to the value of integers. `sys.maxsize`can be used as an integer larger than any practical list or string index, and typically has the same value as `sys.maxint` used to.

## Text vs. data instead of Unicode vs. 8-bit
In an attempt to simplify string encoding and decoding, the concepts of _text_ and binary _data_ were implemented.

Text:
* Unicode
* Type `str`
* Literals are plain `...` (string literals no longer support a leading `u` or `U`)

Binary data:
* Encoded Unicode
* Type `bytes`
* Literals: still `b'...'`

When the two different types are mixed, a `TypeError` is immediately raised. This is perhaps more sensible than the behavior in Python 2, where some quirks allow certain combination cases to be valid.

## Raw string literals
In Python 3, all raw string literals are interpreted literally (wow!).
* `r'\u20ac'` is a string of six characters in Python 3.
* `ur'\u20ac'` was the single Euro character in Python 2.

This only affects raw string literals! The Euro character is still `'\u20ac'` in Python 3.

## Non-ASCII letters
Support for the use of non-ASCII letters in variable names was added in an effort to make coding more international. The standard Python library remains ASCII-only for ease of use (with the exception of contributor names in comments).

## Miscellaneous
* `range()` now behaves like `xrange()` used to behave, except it works with values of arbitrary size. The latter no longer exists.
* `raw_input()` was renamed to `input()`. To get the old behavior of `input()`,  use `eval(input())`.
* `True`, `False`, and `None` are now reserved words.

# `2to3` source-to-source conversion tool
This is a utility designed to convert source code from Python 2 to Python 3. It is usually installed with the Python interpreter as a script, and it preserves comments and the exact indentation of code. Example:

    $ 2to3 -w foobar.py
writes modifications to the source file, and creates a backup of the original source.

# Additional information
* [Original presentation](https://docs.google.com/presentation/d/1e8KoObdM6fJD_sp1o8UxoneB2IDA1Ar0OvtuQqwnV6o/edit?usp=sharing)
* [https://docs.python.org/3/whatsnew/3.0.html](https://docs.python.org/3/whatsnew/3.0.html)
* [https://wiki.python.org/moin/Python2orPython3](https://wiki.python.org/moin/Python2orPython3)
