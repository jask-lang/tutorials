# Lesson 4: Functions and modules

# Functions
Defining a function requires a _name_ and a list of _parameters_:
```python
function myFunction(param1: string, param2: number, param3: any)
    [...]
endfunction
```

Functions should be defined using _lowerCamelCase_ notation.
A parameter must have a type and can be optionally followed by a default value:
```python
function round(num: number, digits: number = 0)
    [...]
endfunction

; will result in 3
round(num = 3.1415)

; will result in 3.14
round(num = 3.1415, digits = 2) 
```

Naming parameters is not mandatory:
```python
; will result in 2.718
round(2.71828, 3)
```

# Modules
Modules are jask scripts in separated files which are providing functionalities for other scripts, like a library or framework.
For example, write a file `my_math_functions.jask`:
```python
function calculateDiscount(price: number, percent: number = 10)
    return price - (price * (percent / 100))
endfunction
```

This file can be imported via `use` where using `.jask` at the end of the file is optional:
```python
use "my_math_functions" as math

printLine("Your discount is " + math::calculateDiscount(price = 200.123, percent = 20))
```

# jcore
jcore are modules for different purposes directly provided by the jask developers.
The jcore modules are embedded into the interpreters executable, so one can use them directly:
```python
use "jcore/math" as math
use "jcore/date" as date

printLine(unfoldModule(math))
```
`unfoldModule` gives you a string containing all functions a module is providing.
Use it to explore the module, alternatively, you can check out the [implementation of jcore](https://github.com/jask-lang/jcore).


# Run
The interpreter needs the *allow-stdout* permission, because we are using *print* and *printLine* in this example.
```bash
dotnet --allow-stdout --input="main.jask"
```

# Continue...
After mastering _functions and modules_, have a look at [lists and maps](https://github.com/jask-lang/tutorials/tree/main/05_lists_and_maps)!
