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

Python 2.7, the last minor update to Python 2, was released in 2010. This marked the end of _feature_ updates to Python 2—there will never be a Python version 2.8. The end-of-life for Python 2 is currently set to 2020; however, it will likely be postponed for reasons presented below.

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

# `2to3` source-to-source conversion tool
This is a utility designed to convert source code from Python 2 to Python 3. It is usually installed with the Python interpreter as a script, and it preserves comments and the exact indentation of code. Example:

    $ 2to3 -w foobar.py
writes modifications to the source file, and creates a backup of the original source.

# Additional information
* [Original presentation](https://docs.google.com/presentation/d/1e8KoObdM6fJD_sp1o8UxoneB2IDA1Ar0OvtuQqwnV6o/edit?usp=sharing)
* [https://docs.python.org/3/whatsnew/3.0.html](https://docs.python.org/3/whatsnew/3.0.html)
* [https://wiki.python.org/moin/Python2orPython3](https://wiki.python.org/moin/Python2orPython3)